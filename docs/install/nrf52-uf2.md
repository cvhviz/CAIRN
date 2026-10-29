# Installing on nRF52840 boards (UF2)

For the Seeed Wio Tracker L1 Pro, the Heltec Mesh Node T096, the Heltec T096 and T114 [compact repeaters](../boards/compact-repeater.md) and the nRF52840 [preview boards](../boards/preview-boards.md). Installing, updating and recovering are the same steps: copy the board's `.uf2` onto it. Your identity, contacts, channels and settings are kept.

## Steps

1. Download your board's `.uf2` from the [latest release](https://github.com/cvhviz/CAIRN/releases/latest), which carries the L1 Pro images, the T096 companion and the T096 and T114 [compact repeater](../boards/compact-repeater.md) images; the nRF52840 preview boards are in [Cairn 107 preview](https://github.com/cvhviz/CAIRN/releases/tag/cairn-v107-preview). The [downloads page](../downloads.md) and your board page say which file.
2. Connect the board over USB with a data cable (charge-only cables are common).
3. **Double-tap Reset** (on the T096 the button is marked `RST`). A USB drive appears, named after the board's bootloader.
4. Copy the `.uf2` onto the drive. The board reboots by itself when the copy finishes, and the drive disappears. That's normal.
5. Check the splash screen: it shows **BUILD N** for the release you copied.

A good copy takes several seconds. If it "finishes" in about a second, or ends with an error such as "Device not configured", it was cut short. Double-tap Reset again and copy it again.

## macOS: Finder error -36

Finder sometimes stops with **error code -36** while copying to the UF2 drive. It is trying to write a hidden `._` metadata file that the bootloader doesn't accept. Copy from Terminal without the extended attributes instead:

```bash
cp -X MeshCore-<Board>-CairnN-<date>.uf2 /Volumes/<drive>/
```

Replace `<drive>` with the drive's name (`ls /Volumes` lists it). A message after the copy that the disk wasn't ejected properly is harmless: the board rebooted on its own.

## Bootloader notes

- Every image needs the **Adafruit nRF52 UF2 bootloader**, but not every board uses the same SoftDevice. Open `INFO_UF2.TXT` on the drive and check its `SoftDevice` line against this table:

  | Images | SoftDevice | App starts at |
  |---|---|---|
  | Wio Tracker L1 Pro (`WioL1Pro`, `DV1`, `WioL1Eink`, `WioL1RoomServer`) | **S140 7.x** (7.3.0) | `0x27000` |
  | Heltec T096 and every nRF52840 [preview board](../boards/preview-boards.md) | **S140 6.1.1** | `0x26000` |

  Each board ships with the SoftDevice its image needs. **Never change the SoftDevice major version just to install Cairn.** An S140 v7 bootloader on a board whose image expects v6 overlaps the start of the image (v7 runs up to `0x27000`), and the board won't boot.
- Copying a `.uf2` never touches the bootloader, so a bad or interrupted copy can always be fixed by copying again.
- If double-tapping Reset doesn't bring up a drive, try a different cable or port, and tap a little faster or slower. Some boards need the taps within about half a second.
- On a board that came with a very old bootloader, update it first using the board maker's instructions, keeping the same SoftDevice major version (see the table above). Cairn doesn't ship bootloaders.
- Going back to stock MeshCore, or to any other firmware, is just copying that firmware's `.uf2` the same way.

## After installing

- Pair from the MeshCore app. The Bluetooth PIN is shown on the device's screen: a new random PIN each boot unless you set your own.
- If something goes wrong, [report it](https://github.com/cvhviz/CAIRN/issues/new?template=bug_report.yml) with the board and the build number from the splash.

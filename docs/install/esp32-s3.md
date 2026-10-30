# Installing on ESP32-S3 boards (esptool or web flasher)

For the Seeed Wio Tracker L2 Pro, the Heltec V4 touch builds (Expansion Kit V2, and the untested Kit V1 preview), the Elecrow ThinkNode M9, the LilyGO T-Deck and T-LoRa Pager, the ESP32 [compact repeaters](../boards/compact-repeater.md) and the ESP32 [preview boards](../boards/preview-boards.md), including the few on the [original ESP32](#original-esp32-boards). Your board's files are on the [downloads page](../downloads.md).

Each ESP32 board has two files in a release:

| File | Use | Written at | Keeps your data? |
|---|---|---|---|
| `MeshCore-<Board>-CairnN-<date>[-<variant>]-full.bin` | first install, or recovery | `0x0`, after a full erase | **No: erases everything** |
| `MeshCore-<Board>-CairnN-<date>[-<variant>]-update.bin` | update a device already on Cairn | `0x10000` | Yes |

For example, the ThinkNode M9's are `MeshCore-ThinkNodeM9-CairnN-<date>-full.bin` and `MeshCore-ThinkNodeM9-CairnN-<date>-update.bin`.

**Flash only the `-full.bin` for a first install, never both.** The `-full.bin` already contains the app; writing the `-update.bin` after it isn't needed. Coming from stock MeshCore or other firmware, use the `-full.bin`: its partition layout may not match Cairn's.

## Before a first install: back up your identity

A first install erases the whole flash: the node's private key, contacts, channels and settings, and any factory firmware. If the board already runs MeshCore and you want to keep its identity, **export the private key and your contacts in the MeshCore app first** (Settings in the app). You can import them again after installing.

## Download mode

Most boards enter download mode on their own when esptool or the web flasher connects. If a board doesn't:

| Board | Buttons |
|---|---|
| Elecrow ThinkNode M9 | none: download mode is automatic through its USB-serial chip, and it has no Boot button. If it doesn't connect, unplug and replug the cable and try again. |
| LilyGO T-Deck / T-Deck Plus | switch it off, hold the **trackball** in (it is BOOT), switch it on, release |
| LilyGO T-LoRa Pager | hold **BOOT** (top edge), tap **RST**, release **BOOT**. With Battery saver on, a dark Pager may be asleep and miss the automatic reset: press a key to wake it first, or use the buttons |
| Wio Tracker L2 Pro | hold **Boot**, tap **Reset**, release **Boot** |
| Heltec V4 (touch or OLED), V3, Wireless Tracker | hold **PRG** (also labelled USER), tap **RST**, release **PRG** |
| Most other boards | hold **BOOT** (or IO0), tap **RST** / **EN**, release **BOOT** |

After writing, tap Reset once if the screen still shows the old firmware.

## Option 1: web flasher (Chrome or Edge)

1. Open [Espressif's web flasher](https://espressif.github.io/esptool-js/) and click **Connect**. Pick the board's serial port.
2. **First install or recovery:** click **Erase Flash** and wait for it to finish. Then set the address to `0x0`, choose the `-full.bin`, and click **Program**.
3. **Update:** set the address to `0x10000`, choose the `-update.bin`, and click **Program**. Don't erase.
4. Click **Disconnect**, then tap Reset on the board.

## Option 2: esptool (command line)

esptool v5 is shown here. `pip install esptool` (or `pipx install esptool`) installs it.

```bash
# first install or recovery
esptool --chip esp32s3 erase-flash
esptool --chip esp32s3 -b 921600 write-flash 0x0 MeshCore-<Board>-CairnN-<date>-full.bin

# update
esptool --chip esp32s3 -b 921600 write-flash 0x10000 MeshCore-<Board>-CairnN-<date>-update.bin
```

The older form still works: `esptool.py --chip esp32s3 erase_flash`, `esptool.py ... write_flash 0x10000 ...`. Add `-p <port>` if more than one serial device is connected. If writes fail at 921600, use `-b 460800`.

### If the device last updated over Wi-Fi

An L2, Heltec V4, ThinkNode M9, T-Deck or T-LoRa Pager that installed its last update over Wi-Fi may be running from its second app slot, and a USB write to `0x10000` would then be ignored at boot. Clear the boot selector first, then write the update:

```bash
esptool --chip esp32s3 erase-region 0xe000 0x2000
esptool --chip esp32s3 -b 921600 write-flash 0x10000 MeshCore-<Board>-CairnN-<date>-update.bin
```

This keeps your identity and settings. Writing the `-full.bin` after a full erase also works, but erases everything.

### Original ESP32 boards

A few preview boards (Heltec V2, the LilyGO T-Beam with SX1262 or SX1276, T-LoRa V2.1, MeshAdventurer) use the original ESP32. Use `--chip esp32` instead of `--chip esp32s3`, or leave `--chip` out and let esptool detect it. The offsets are the same: `-full.bin` at `0x0`, `-update.bin` at `0x10000`.

The [compact repeater](../boards/compact-repeater.md) images for the Heltec V2, V3, V4, V4-R8 and Wireless Tracker install the same way: `-repeater-full.bin` at `0x0` for a first install, `-repeater-update.bin` at `0x10000` to update. They don't update over Wi-Fi.

## Over Wi-Fi (L2 Pro, Heltec V4 touch kits, ThinkNode M9, T-Deck, T-LoRa Pager)

The T-Display SF32 updates over Wi-Fi too; see [its install guide](sf32.md#updating-later).

- **Online:** Settings › System › Firmware update › **Check for updates**. The device also checks this repository once a day while on Wi-Fi and shows a notice when a newer build is out. It downloads the board's `-update.bin` over HTTPS, checks its size, SHA-256 and board marker, and installs only after you confirm.
- **Wi-Fi transfer:** tap the **Wi-Fi transfer** tile on the same page (called Updater mode before Cairn 116, and update mode before Cairn 112). The board shows its address and a password. Open that address in a browser, type the password, and upload the `-update.bin`.

  Bluetooth is off while Wi-Fi transfer runs, and the board restarts into the new build when it's done.
- **From CairnOS** (Cairn 112, with the next CairnOS update): the app can ask the board over Bluetooth to start Wi-Fi transfer. The board asks **Allow app update?** first; after you tap Allow it turns Bluetooth off and the app sends the update over Wi-Fi. The board must be on Wi-Fi.

### T-Deck started from an SD-card launcher

A T-Deck that starts Cairn from a launcher on the SD card (bmorcelli Launcher, for example) can't use Cairn's online update: the launcher's partition layout has no spare slot Cairn can safely write to. From Cairn 122 the Firmware update page says "Started by a launcher: update from its SD card" and refuses cleanly. On Cairn 121 and earlier the online update crashes and restarts the device instead ([#28](https://github.com/cvhviz/CAIRN/issues/28)), or on newer launchers may write over another installed app, so don't use it there. Two ways out:

- **Keep the launcher:** copy the new `-update.bin` to the card and install it from the launcher.
- **Switch to Cairn's own layout:** erase the flash and write the `-full.bin` at `0x0` over USB (Option 1 or 2 above). This removes the launcher and its apps, and from then on Wi-Fi updates work. Export your key and contacts first.

If the T-Deck still shows the old build after a USB install, check the `-full.bin` went to `0x0` (not `0x10000`) after a full erase.

## First boot

The first boot after a full erase sits on "Loading..." for a while as it formats storage and creates the node's identity. Leave it alone; it then shows the home screen. Pair from the MeshCore app with the PIN shown on the screen.

## Troubleshooting

**Blank screen or boot loop after installing.** The wrong build for the board revision is the usual cause. Check what the chip reports:

```bash
esptool flash-id       # older esptool: esptool.py flash_id
```

`flash-id` prints the chip line (type, revision and features such as *Embedded PSRAM 8MB*) and the *Detected flash size*. `esptool chip-id` (older: `chip_id`) prints the chip line without the flash size.

The **Heltec V4 touch build needs a V4-R8** (reports *Embedded PSRAM 8MB*; 16 MB flash, octal PSRAM) **fitted in the Expansion Kit V2** (2.8" touchscreen). A standard V4 reports *2MB* PSRAM: in the Expansion Kit V1 it needs the untested `HeltecV4KitV1` build (from Cairn 121, [Kit V1 page](../boards/heltec-v4-kit-v1.md)), and with only the OLED the `HeltecV4` [preview build](../boards/preview-boards.md); on a standard V4 the Kit V2 touch image's octal PSRAM setup fails and the board boot-loops. A V4-R8 with only the OLED needs the `HeltecV4R8` preview build. The L2 Pro has 16 MB flash and 8 MB PSRAM on its Wio-S3 module.

**esptool can't connect.** Put the board in download mode by hand (see above), try another cable or USB port, and close anything else holding the serial port (the MeshCore web app, a serial monitor, another flasher tab). The ThinkNode M9 has no download-mode buttons: replug it instead, and on Windows install WCH's CH340 driver if no COM port appears.

**The old firmware still runs after an update.** Tap Reset. If it still does, the device was probably on its second app slot: see [If the device last updated over Wi-Fi](#if-the-device-last-updated-over-wi-fi).

**Still stuck?** Erase and write the `-full.bin` (this erases everything), then [report it](https://github.com/cvhviz/CAIRN/issues/new?template=bug_report.yml) with the board, the build number and a serial log.

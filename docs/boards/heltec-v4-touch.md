# Heltec WiFi LoRa 32 V4 + Expansion Kit (touch)

✅ Tested on hardware · ESP32-S3 · [install with esptool or the web flasher](../install/esp32-s3.md) · updates over Wi-Fi

The Heltec V4 with Heltec's Expansion Kit V2: ESP32-S3 (16 MB flash, 8 MB octal PSRAM), SX1262 with front end, 2.8" ST7789 touchscreen, L76K GPS, piezo and microSD. It runs the same touch interface as the [Wio Tracker L2 Pro](wio-tracker-l2-pro.md); the [L2 manual](../Cairn_Wio_L2_Pro_User_Manual.pdf) applies to it too.

**This build needs a V4-R8** (`esptool chip-id` reports *Embedded PSRAM 8MB*) **fitted in the Expansion Kit V2**. The image is built for the R8's 8 MB octal PSRAM (16 MB QIO flash, KCT8103L front end). A standard Heltec V4 reports *2MB* PSRAM (quad SPI) and has a different front end; on it this image's octal PSRAM setup fails and the board boot-loops. A standard V4 needs the `HeltecV4` [preview build](preview-boards.md); a V4-R8 with only the OLED needs the `HeltecV4R8` preview build. See [troubleshooting](../install/esp32-s3.md#troubleshooting).

## Which file

| You want to… | File | How |
|---|---|---|
| install Cairn for the first time | `MeshCore-HeltecV4Touch-CairnN-<date>-full.bin` | full erase, then write at `0x0`. **Erases everything**: export your key and contacts in the app first. |
| update | `MeshCore-HeltecV4Touch-CairnN-<date>-update.bin` | online (Settings › System › Firmware update), a browser upload in Updater mode, or USB at `0x10000` |
| recover a device that won't boot | `MeshCore-HeltecV4Touch-CairnN-<date>-full.bin` | full erase, then write at `0x0` |

Write the `-full.bin` or the `-update.bin`, never both. If the device last updated over Wi-Fi, run `esptool --chip esp32s3 erase-region 0xe000 0x2000` before a USB write of the `-update.bin` ([why](../install/esp32-s3.md#if-the-device-last-updated-over-wi-fi)).

## Buttons

| Button | Does |
|---|---|
| IO (Expansion Kit) | the WAKE button. Click: turn the screen off, or wake it; double-press: unlock; hold (1 s): lock. It can't wake the board from hibernate. |
| PRG (USER) | click: quick panel; double-press: new message (unlocks instead when the device is locked); hold: back; triple-press: mute. The first press on a dark screen only wakes it. It is the only button that wakes the board from hibernate. Click, double and hold can be reassigned in Settings. |
| PRG + RST | hold **PRG**, tap **RST**, release **PRG**: download mode for esptool. **Don't hold IO while pressing RST**: IO is GPIO46, a strap pin, and PRG + IO held together at reset is an invalid strap combination. |
| RST | restart |

## Features

The full L2 touch interface: home dashboard, chats with an on-screen keyboard and colour emoji, nodes, repeater scan and admin, radio with spectrum and band scan, GPS with the offline microSD map and pinch to zoom, quick panel, Wi-Fi with online updates, and the Wi-Fi and Bluetooth scanners and the redesigned Battery page (from Cairn 113). See the [L2 Pro page](wio-tracker-l2-pro.md#features) for the list. It has no audio hardware beyond the piezo, so the music player isn't on this board.

From Cairn 114: the Radios page with LoRa, Wi-Fi and Bluetooth tabs and a full-screen Traffic log with packet details, the Storage page with Files, and the card's `Maps`, `Music`, `Recordings`, `Sounds` and `Pictures` folders (maps in `cairn/maps` move by themselves). USB drive mode isn't on this board.

From Cairn 115: the LoRa / Wi-Fi / Bluetooth tabs are easier to tap (this panel reads taps near the top edge a little high), and after a power cut the clock shows "--:--" until GPS, the app or Wi-Fi sets it.

From Cairn 113 on this board:

- **Better reception:** the V4-R8's receive amplifier was left bypassed before; it now follows the receive-gain setting (on by default).
- **Steadier touch:** glitches no longer turn into phantom taps or split a drag, and the touch controller recovers by itself after a wake or a run of bad readings.
- **The whole screen is tappable,** edge to edge, including the bottom rows and the right edge.
- **Ocean theme** is a few steps darker, so it no longer looks washed out on this screen.

## Known issues

- No card-detect line on this board, so the SD card stays powered; the L2's SD power saving doesn't apply.
- Battery figures with the screen off are estimates; they haven't been measured yet.
- Check each build's release notes for anything new.

Problems? [Report a bug](https://github.com/cvhviz/Cairn/issues/new?template=bug_report.yml).

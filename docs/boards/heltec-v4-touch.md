# Heltec WiFi LoRa 32 V4 + Expansion Kit (touch)

✅ Tested on hardware · ESP32-S3 · [install with esptool or the web flasher](../install/esp32-s3.md) · updates over Wi-Fi

The Heltec V4 with Heltec's Expansion Kit V2: ESP32-S3 (16 MB flash, 8 MB octal PSRAM), SX1262 with front end, 2.8" ST7789 touchscreen, L76K GPS, piezo and microSD. It runs the same touch interface as the [Wio Tracker L2 Pro](wio-tracker-l2-pro.md); the [Cairn manual](../Cairn_Firmware_Manual_Dark.pdf) covers it.

**This build needs a V4-R8** (`esptool chip-id` reports *Embedded PSRAM 8MB*) **fitted in the Expansion Kit V2**. The image is built for the R8's 8 MB octal PSRAM (16 MB QIO flash, KCT8103L front end). A standard Heltec V4 reports *2MB* PSRAM (quad SPI) and has a different front end; on it this image's octal PSRAM setup fails and the board boot-loops. A standard V4 in the Expansion Kit V1 has its own untested build from Cairn 121 ([Kit V1 page](heltec-v4-kit-v1.md)); a standard V4 with only the OLED needs the `HeltecV4` [preview build](preview-boards.md); a V4-R8 with only the OLED needs the `HeltecV4R8` preview build. See [troubleshooting](../install/esp32-s3.md#troubleshooting).

## Which file

| You want to… | File | How |
|---|---|---|
| install Cairn for the first time | `MeshCore-HeltecV4Touch-CairnN-<date>-full.bin` | full erase, then write at `0x0`. **Erases everything**: export your key and contacts in the app first. |
| update | `MeshCore-HeltecV4Touch-CairnN-<date>-update.bin` | online (Settings › System › Firmware update), a browser upload in Wi-Fi transfer, or USB at `0x10000` |
| recover a device that won't boot | `MeshCore-HeltecV4Touch-CairnN-<date>-full.bin` | full erase, then write at `0x0` |

Write the `-full.bin` or the `-update.bin`, never both. If the device last updated over Wi-Fi, run `esptool --chip esp32s3 erase-region 0xe000 0x2000` before a USB write of the `-update.bin` ([why](../install/esp32-s3.md#if-the-device-last-updated-over-wi-fi)).

## Buttons

| Button | Does |
|---|---|
| IO (Expansion Kit) | the WAKE button. Click: turn the screen off, or wake it; double-press: unlock (straight from a dark screen from Cairn 119); hold (1 s): lock. It can't wake the board from hibernate. |
| PRG (USER) | click: quick panel; double-press: new message (unlocks instead when the device is locked); hold: back; triple-press: mute. The first press on a dark screen only wakes it. It is the only button that wakes the board from hibernate. Click, double and hold can be reassigned in Settings. |
| PRG + RST | hold **PRG**, tap **RST**, release **PRG**: download mode for esptool. **Don't hold IO while pressing RST**: IO is GPIO46, a strap pin, and PRG + IO held together at reset is an invalid strap combination. |
| RST | restart |

## Features

The full L2 touch interface: home dashboard, chats with an on-screen keyboard and colour emoji, nodes, repeater scan and admin, radio with spectrum and band scan, GPS with the offline microSD map and pinch to zoom, quick panel, Wi-Fi with online updates, and the Wi-Fi and Bluetooth scanners and the redesigned Battery page (from Cairn 113). See the [L2 Pro page](wio-tracker-l2-pro.md#features) for the list. It has no audio hardware beyond the piezo, so the music player isn't on this board.

From Cairn 114: the Radios page with LoRa, Wi-Fi and Bluetooth tabs and a full-screen Traffic log with packet details, the Storage page with Files, and the card's `Maps`, `Music`, `Recordings`, `Sounds` and `Pictures` folders (maps in `cairn/maps` move by themselves). USB drive mode isn't on this board.

From Cairn 122 (files `MeshCore-HeltecV4Touch-Cairn122-2026-10-25-full.bin` and `-update.bin`): **RX sync and queue sync** (with CairnOS build 18 or later): the app catches up on what the radio heard during a dropped link, as far back as its journal reaches, and a message stays queued on the radio until the app has stored it; anything the radio had to drop is counted in the app. The official MeshCore apps get the same frames as before. Going back to Cairn 121 loses the messages waiting on the radio. **Every radio preset the app offers** on the Radio page's preset picker: all 28, with their frequency and area, grouped by region with the one the device is in first; a preset with a path hash sets it too, and the device remembers which preset you picked. The summary card on top of the Radio page shows the path hash next to the TX power, and its tile moved ahead of TX power. **A locate button on the map:** a crosshair under the zoom and fit buttons centres the map on your position and follows it ("No position yet" when there is none); a second tap on the GPS tab does the same. **The position set from the app shows on the device:** with the GPS off, the map, distances and bearings, GPS data and Home's GPS card use it (GPS data labels it "(SAVED)" or "(LAST)"). **Radio settings over Wi-Fi:** a phone on the Trusted devices list ("Always allow") can apply a preset, a radio change or Repeat Mode over Wi-Fi, live; a phone allowed once is still refused. Command-line text over Wi-Fi is now limited like the other commands, so the app's Reboot, Power off, Set PIN and Wi-Fi commands work over Bluetooth only. **A radio change no longer leaves the node deaf:** a preset or radio change while the radio was listening could leave it hearing nothing until it next sent. **A failed online install says why:** "Update failed · <why>" for 4 s, and once more after the restart; Settings › Maintenance's last restart reads "Update failed". The TX power cap stays at 18; `set tx` now answers an error for anything outside -9 to 18 instead of saving it. **Not yet checked on a device:** nothing new in 122 has run on hardware yet; it builds and passes the firmware's automated tests.

From Cairn 121 (files `MeshCore-HeltecV4Touch-Cairn121-2026-10-21-full.bin` and `-update.bin`): **Settings that fit on one screen:** Storage (small tiles for USB drive, Files, Transfer, Eject, Re-scan and Format), Map (six tiles: Map set, Online map, Labels, Traffic lines, Map cache and Storage; Map cache moved here from Storage), Screensaver (when it runs moved to a new **Saver options** card under Appearance), Display, Wake & lock (Msg wake moved here), Sound, Theme (the nine themes as tiles in their own colors), Quick replies, Wi-Fi and Scope. A channel's page shows its key on the channel tile, with **Mute** beside **Leave** (still a 1.5 s hold). Hibernate is a 1.5 s hold on System › Restart, beside Restart, whose tile shows the last restart. About is shorter, with the public key on the first screen. No setting is gone; some moved. Under Settings › LoRa › Radio, FEM LNA and Boosted RX are small toggle tiles, so that page barely scrolls. Also: a crash during map downloads is fixed (closing a download's connection could close the map file on the card); contacts, settings and channels are written to a copy first, so a save cut short no longer loses them; a save that fails says "Not saved: storage full"; and a message arriving while you type no longer throws the draft away.

From Cairn 120: telemetry from your contacts and the Share telemetry setting, the renamed and color-coded Settings (LoRa, Network, GNSS) with the LoRa settings on one screen, room posts with their poster and time, streets past a big downloaded area, fuller traffic lines and more free memory, as on the [L2 Pro](wio-tracker-l2-pro.md#features). **Portrait:** the Settings cards fill the screen and a long line wraps instead of being cut; turning the screen keeps the page you're on (a repeater login, a chat or a scan carry on).

From Cairn 119:

- **Portrait mode:** the Quick panel's Advert tile is **Rotate** on this board. It turns the screen between landscape and 240×320 portrait at once, no restart, with the six tabs as a bar along the bottom. The touch (and a saved touch calibration) turns with it, and the choice is kept across restarts.
- **Faster microSD:** the card runs at 20 MHz (was 4 MHz), so maps and files read about 3.5× faster. A card that fails at 20 MHz drops back to 4 MHz until it is removed.
- **Unlock in two presses:** a double-press of IO unlocks straight from a dark screen (it took three before).
- **Maps:** download an area to the card over Wi-Fi, the online map, vector maps, and the GPS tab opening on the map, as on the [L2 Pro](wio-tracker-l2-pro.md#features). Leaving the Map while a tile was still being read no longer crashes the board.
- **CairnOS** (build 12 or later): the app's Spectrum page shows this radio's Channel view, and its chat history goes over to the app.

From Cairn 116 (tested extensively, on the bench and in the field):

- **No more touch stalls:** the touch controller could report a finger that never lifted, or a "ghost" second touch near the top-right corner, so taps did nothing until the screen was switched off and on. Cairn follows the real finger, ignores short-lived ghosts and resets the controller itself when either shows up, and also on leaving the screensaver.
- **Taps land where your finger does,** not on the row below.
- **Battery saver** (Settings › Display), the **FEM LNA** and **Boosted RX** switches (Settings › LoRa › Receive), low-battery shutdown, and the white LED flashing with each packet sent.
- **TX power at the antenna:** the Radio pages show what leaves the antenna (up to 28 dBm), and the setting stops at 18, where the amplifier is already at full output.

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

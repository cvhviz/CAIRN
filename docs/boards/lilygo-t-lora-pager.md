# LilyGO T-LoRa Pager

✅ Tested on hardware, beta · ESP32-S3 · [install with esptool or the web flasher](../install/esp32-s3.md) · updates over Wi-Fi (from Cairn 125 on)

The T-LoRa Pager is a handheld with:
- an ESP32-S3 (16 MB flash, 8 MB PSRAM)
- a Semtech SX1262 LoRa radio (LilyGO's default), or an LR1121 on some units
- a 2.33" 480×222 IPS screen (no touch)
- a 31-key QWERTY keyboard with a backlight, a side wheel that clicks in, and a BOOT key on the top edge
- a GPS, a microSD slot, a speaker and microphone, a vibration motor, a motion sensor, NFC and a real-time clock
- native USB on its USB-C port (no USB-serial chip)

Cairn runs the same interface as the [Wio Tracker L2 Pro](wio-tracker-l2-pro.md) on it, laid out for the wide screen and run from the keys, as on the [ThinkNode M9](thinknode-m9.md) and the [T-Deck](lilygo-t-deck.md). A ring shows what is selected. Typing goes straight into chats and text fields. The [Cairn manual](../Cairn_Firmware_Manual_Dark.pdf) describes the screens.

**Beta** means it is tested on hardware but new to Cairn. On a Pager (SX1262) it has run with the screen, the keyboard, the side wheel and its click, Back, the quick panel, Lift to wake and the radio; a tester reported the rest of the first test build's checklist working. The one problem found, the microSD card not mounting so Maps said low memory ([#34](https://github.com/cvhviz/CAIRN/issues/34)), is fixed in Cairn 125 but not yet re-checked on a Pager. The LR1121 file has not run on a Pager yet, and Cairn's full automated on-device test suite hasn't been run on it.

## Which file

Download from the [latest release](https://github.com/cvhviz/CAIRN/releases/latest) · [every board's files](../downloads.md)

| You want to… | File | How |
|---|---|---|
| install Cairn for the first time | `MeshCore-TLoraPager-CairnN-<date>-full.bin` | write at `0x0` ([steps](../install/esp32-s3.md)). If it runs MeshCore, export your key and contacts in the app first. |
| update | `MeshCore-TLoraPager-CairnN-<date>-update.bin` | USB at `0x10000`, or over Wi-Fi: Settings › System › Firmware update fetches it from the latest release (from Cairn 125 on) |
| recover a device that won't boot | `MeshCore-TLoraPager-CairnN-<date>-full.bin` | write at `0x0` |

**Pick the file for your radio.** The radio is on the box and the back label. SX1262 units take `TLoraPager`, LR1121 units take `TLoraPagerLR1121`. The wrong one runs but has no radio. The online update keeps to the radio you installed. Write the `-full.bin` or the `-update.bin`, never both.

**Download mode.** esptool and the web flasher can usually restart the Pager into download mode over USB by themselves. If they can't connect (with Battery saver on, a dark Pager may be asleep): hold BOOT, press and let go of RST, let go of BOOT, then connect again.

**From the experimental build.** A Pager on the Cairn 124 test build (`experimental-tlora-pager-124`) can take Cairn 125 over Wi-Fi: Settings › System › Firmware update finds it in the latest release.

## Controls

| Control | What it does |
|---|---|
| Side wheel, turn | moves through the sidebar's tabs, then the page's items in reading order. Up past a page's first item goes back to the sidebar. A slow turn moves one item at the first click, then one every two clicks; a fast spin moves on every click and speeds up in long lists (from Cairn 125). |
| Side wheel, click | OK. Held: a long press. On the sidebar it opens the tab and moves into the page. |
| Space | OK when no text field is open; a space in one. Hold Space + a key: the symbol printed on that key. |
| ← (top right, under the wheel) | Back. In a text field it deletes, and held it repeats. To leave a text field without deleting, hold the wheel in. |
| Orange key (bottom left) | the quick panel (brightness, keyboard light, Bluetooth and more): a press opens it, another closes it. |
| Cap | next letter capital; twice: caps lock; again: off. Cap + ←: delete a word. |
| Enter | finishes the text field: Send in a chat, Done, OK or Save elsewhere. |
| BOOT (top edge) | the button in Settings › Hardware › Buttons: tap locks, hold asks "Power off?", double tap starts a new message. |
| PWR | turns the Pager on after a power off. |

Unlock: click the wheel twice, or press BOOT twice. Power off on battery puts the charger in ship mode (PWR turns it back on); on USB it sleeps until BOOT or the wheel's click.

## Features

- **Lift to wake** (Settings › Hardware › Lock): the motion sensor lights the screen when you pick the Pager up. Its firmware loads when you turn it on, so a Pager without it never spends the time or the current. There is no compass: the board has no magnetometer.
- **Vibration** (Settings › Hardware › Sound › Vibrate): new messages buzz, and keys can tick.
- **NFC:** share your contact by tapping a phone to the back (Settings › LoRa › Profile › Tap to share), and read or write contact tags (Settings › LoRa › Contacts › NFC).
- **Sound and recorder:** message tones, the audio player and the recorder, through the Pager's speaker and microphone.
- **microSD:** offline maps from the card's `Maps` folder (download them on the device or make them with [tools/maptiles.py](../../tools/maptiles.py)), music, and USB drive mode.
- **Keyboard light:** lit with the screen, its level set in the quick panel.
- **Battery saver** (Settings › Hardware › Display › Batt. saver, off by default): while the screen is dark the chip sleeps between radio packets. Not yet measured on a Pager.
- **The clock** keeps time through a power off (the board's real-time clock), set again from GPS or the app.

## From Cairn 125

Files: `MeshCore-TLoraPager-Cairn125-2026-10-29-full.bin` and `-update.bin` (SX1262); `MeshCore-TLoraPagerLR1121-Cairn125-2026-10-29-full.bin` and `-update.bin` (LR1121).

- **In the release, with online updates.** The Pager joins the other boards in every release, and updates over Wi-Fi from here on.
- **microSD and Maps** ([#34](https://github.com/cvhviz/CAIRN/issues/34)): the mesh and the interface now go into the Pager's PSRAM as intended, leaving about 140 KB of internal memory instead of 15 KB, so the card mounts and Maps no longer says low memory.
- **The side wheel** is calmer at a slow turn and still fast when spun (above). Checked on a Pager.
- **No bring-up log** on the serial port: the release builds print only a short summary as they start.

## Known issues

- Not yet checked on a Pager: the LR1121 file, the microSD card and Maps since the #34 fix, Battery saver's current, and the full on-device test suite.

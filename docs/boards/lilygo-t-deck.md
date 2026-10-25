# LilyGO T-Deck / T-Deck Plus

✅ Tested on hardware, beta · ESP32-S3 · [install with esptool or the web flasher](../install/esp32-s3.md) · updates over Wi-Fi (from Cairn 108 on)

The T-Deck is a handheld with:
- an ESP32-S3 (16 MB flash, 8 MB PSRAM)
- a Semtech SX1262 LoRa radio
- a 2.8" 320×240 ST7789 touchscreen (GT911 touch)
- a QWERTY keyboard (its own ESP32-C3 controller) and a trackball with a centre click
- a microSD slot, a speaker (message chimes and tones, with a volume setting, from Cairn 109; music from Cairn 113), a microphone (voice notes from Cairn 113), and on the T-Deck Plus a GPS and a larger battery
- native USB on its USB-C port (no USB-serial chip)

Cairn runs the same interface as the [Wio Tracker L2 Pro](wio-tracker-l2-pro.md) on it, by touch or by keys. The trackball moves a ring over what is selected and its click taps it, as a finger would; touching the screen hides the ring. Typing goes straight into chats and text fields. The keyboard has no Back key: Backspace outside a text field goes back, and so does holding the trackball in when nothing is selected. The [Cairn manual](../Cairn_Firmware_Manual_Dark.pdf) describes the screens and the T-Deck's keys.

**Beta** means it is tested on hardware but new to Cairn. On a T-Deck it has run with the screen, touch, keyboard, trackball, LoRa radio, an offline map from microSD, and an identity and contacts carried over from another firmware. Cairn's full automated on-device test suite hasn't been run on it yet, and some features are untried; see [Known issues](#known-issues).

## Keyboard

- **Keyboard light:** lit while the screen is on, dark when it goes dark or locks. It also goes dark 2 s before the screen times out, and on battery 10 s after the last key or touch; any input relights it (from Cairn 112). Set its level, or Off, in Settings › Hardware › Display (under Brightness) or with the keyboard slider in the quick panel. Alt+B still turns it on or off, until the screen next wakes or goes dark.
- **Space is the customizable button:** outside a text field, Space and double Space run the actions picked in Settings › Hardware › Buttons (Quick panel and New message by default). A single Space acts after a short wait for a second one, unless double Space is set to None. On a dark screen Space only wakes it, and locked it does nothing.
- **Charging:** the blue LED is the charge light (on while charging, off when full); the T-Deck charges from USB-C with the power switch on or off. On USB the cell can't be read (the battery pin sees USB power), so the status bar, Home and the Battery page say "USB · charging" instead of a percent (from Cairn 111); the blue LED going out is the sign it's charged.
- **GPS (T-Deck Plus, or an add-on GPS):** found at 9600 or 38400 baud by itself; a u-blox receiver goes to standby while GPS is off (from Cairn 111).
- **Battery saver** (Settings › Hardware › Display › Power, off by default, beta, from Cairn 111): while the screen is dark the chip sleeps between radio packets, with Bluetooth off. Measured for Cairn 112: about 43 mA with the screen off instead of about 82 mA, so about 54 h of standby on a full charge instead of about 28 h. It slept 98–99 % of a 14-hour run and still received every packet.
- **Nodes Cards view by keys:** the trackball and arrow keys focus one card at a time; left and right move between the two in a row (from Cairn 112).
- **Enter finishes the text field** (from Cairn 113): Send in a chat, Done, OK or Save elsewhere. The trackball click still selects what is highlighted.
- **Radios by keys:** 1, 2 and 3 pick the LoRa, Wi-Fi and Bluetooth tabs (from Cairn 114). The LoRa tab lands on Advert (from Cairn 113), and the advert sheet opens with Send focused, so Advert, then a click, sends a zero-hop advert.

## From Cairn 122

Files: `MeshCore-TDeckPlus-Cairn122-2026-10-25-full.bin` and `-update.bin`.

- **Started from an SD-card launcher:** the online update no longer crashes the T-Deck ([#28](https://github.com/cvhviz/CAIRN/issues/28)). Under a launcher, Settings › System › Firmware update says "Started by a launcher: update from its SD card" and greys out Install; browser and Cairn Updater uploads are refused the same way, with no restart. About and the Firmware update page name the launcher's slot ("app1 · launcher"). **A T-Deck on Cairn 121 or earlier under a launcher still runs the old updater: don't use its online update.** Copy `MeshCore-TDeckPlus-Cairn122-2026-10-25-update.bin` to the card and install it from the launcher once. To get Wi-Fi updates instead, flash the `-full.bin` at `0x0` over USB once ([steps](../install/esp32-s3.md#t-deck-started-from-an-sd-card-launcher)); this removes the launcher.
- **RX sync and queue sync** (with CairnOS build 18 or later): the app catches up on what the radio heard during a dropped link, as far back as its journal reaches, and a message stays queued on the radio until the app has stored it; anything the radio had to drop is counted in the app. The official MeshCore apps get the same frames as before. Going back to Cairn 121 loses the messages waiting on the radio.
- **Every radio preset the app offers** on the Radio page's preset picker: all 28, with their frequency and area, grouped by region with the one the device is in first; a preset with a path hash sets it too, and the device remembers which preset you picked. The Radio page's summary card shows the path hash next to the TX power.
- **A locate button on the map:** a crosshair under the zoom and fit buttons centres the map on your position and follows it ("No position yet" when there is none); a second tap on the GPS tab does the same.
- **The position set from the app shows on the device:** with the GPS off, the map, distances and bearings, GPS data and Home's GPS card use it (GPS data labels it "(SAVED)" or "(LAST)").
- **Radio settings over Wi-Fi:** a phone on the Trusted devices list ("Always allow") can apply a preset, a radio change or Repeat Mode over Wi-Fi, live; a phone allowed once is still refused. Command-line text over Wi-Fi is now limited like the other commands, so the app's Reboot, Power off, Set PIN and Wi-Fi commands work over Bluetooth only.
- Also: a radio change no longer leaves the node deaf until it next sends, and a failed online install says why ("Update failed · <why>", shown again after the restart).
- **Not yet checked on a device:** nothing new in 122 has run on hardware yet; it builds and passes the firmware's automated tests. That includes the launcher refusal, which hasn't been tried under a launcher.

## From Cairn 121

Files: `MeshCore-TDeckPlus-Cairn121-2026-10-21-full.bin` and `-update.bin`.

- **Settings that fit on one screen:** Storage (small tiles for USB drive, Files, Transfer, Eject, Re-scan and Format), Map (six tiles: Map set, Online map, Labels, Traffic lines, Map cache and Storage; Map cache moved here from Storage), Screensaver (when it runs moved to a new **Saver options** card under Appearance), Display, Wake & lock (Msg wake moved here), Sound, Theme (the nine themes as tiles in their own colors), Quick replies, Wi-Fi and Scope. A channel's page shows its key on the channel tile, with **Mute** beside **Leave** (still a 1.5 s hold). Hibernate is a 1.5 s hold on System › Restart, beside Restart, whose tile shows the last restart. About is shorter, with the public key on the first screen. No setting is gone; some moved.
- **Keys:** the key-navigation ring now reaches every tile on these pages without scrolling, and holding Enter on Format runs its hold.
- Also: a crash during map downloads is fixed (closing a download's connection could close the map file on the card); contacts, settings and channels are written to a copy first, so a save cut short no longer loses them; a save that fails says "Not saved: storage full"; and a message arriving while you type no longer throws the draft away.

## From Cairn 120

- **Telemetry:** a contact's node page shows its battery and opens its telemetry; Settings › GNSS › Telemetry chooses who may read yours (off by default).
- **Settings** renamed LoRa, Network and GNSS, color-coded, with the LoRa radio settings on one screen.
- **Rooms:** each post shows who wrote it and when.
- **Maps:** streets where a big downloaded area stops short of them (online map on), the satellite count in the status bar, and fuller traffic lines.
- About 55-65 KB more free memory beside Bluetooth and Wi-Fi, and Battery saver sleeps with Wi-Fi on away from your networks.

## From Cairn 119

- **Maps:** the GPS tab opens on the full-screen Map, and the trackball and keys start on its compass (GPS data). Download an area to the card over Wi-Fi (long-press the Map › **Download area…**), or use the online map with no card, as on the [L2 Pro](wio-tracker-l2-pro.md#features). Downloads no longer stop with "Card write failed": a write the card refuses for a moment is tried again.
- **Rooms:** posting to a room you just logged in to works (no more "Recipient gone").
- **Add a heard node:** with "manually add contacts" on, "…" on a node heard since the last restart offers **Add contact**.
- **CairnOS** (build 12 or later): the app's Spectrum page shows this radio's Channel view, and its chat history goes over to the app.
- In Files, Backspace still goes up a folder.

## Music and voice notes

From Cairn 113, tried on a T-Deck Plus. On the T-Deck an **Audio** card takes the GPS card's place on Home (the GPS tab's GPS data still shows the satellites) and opens a Player and a Recorder.

- **Player:** put MP3 or WAV files in a `Music` folder on the microSD card. Now playing has a live spectrum with volume buttons over it, a seek bar and previous / -10 s / play-pause / +10 s / next; repeat and shuffle are in its options. Subfolders in `Music` show two levels deep (from Cairn 114). Music keeps playing with the screen dark unless you set "Pause at screen off". From Cairn 115: a five-band **EQ**, Now playing as a full-screen visualizer, Player options as cards, and alert tones no longer interrupt music (Options › Alerts turns them back on). Hold a file to delete it. MP3 (CBR or VBR) and WAV (8, 16 or 24-bit), 8 to 48 kHz; stereo plays as mono.
- **Add music over Wi-Fi** (from Cairn 116): Settings › Storage › **Wi-Fi transfer**, then open the address it shows in a browser on your network and drop MP3 or WAV files in; they go into `Music`, or a folder you name inside it.
- **Mic key** (from Cairn 114): opens the Recorder; on the Recorder it starts and stops a recording.
- **Older keyboards** (from Cairn 115): a keyboard whose firmware ignores the raw key mode the Mic key needs types normally again ([#17](https://github.com/cvhviz/CAIRN/issues/17)).
- **Recorder:** voice notes to a `Recordings` folder as WAV at 16 or 8 kHz, with mic gain, a time limit, voice start and marks. Files are named by date and time once the clock is set. A recording keeps going with the screen dark and is kept safe if the power or the card goes. The microphone is only on while you record or the Record view is open, and the status bar shows MIC or REC whenever it is.
- The card shares its bus with the radio and the screen, so very large files (CD-quality WAV) are refused with "Too fast for this card: use MP3".
- The folders match the T-Display SF32's, so a card moves between them.

The T-Deck also has the Wi-Fi and Bluetooth scanners and the redesigned Battery page from Cairn 113, and from Cairn 114 the Radios tabs with Traffic, the Storage page with Files, and **USB drive** mode (the microSD card as a disk on your computer, about 0.5 MB/s); see the [L2 Pro page](wio-tracker-l2-pro.md#features). On USB the Battery page says the cell can't be read instead of claiming Full.

## Screens

![Home on the T-Deck](../screens/tdeck/home.png)

Home on a T-Deck running Cairn 108, with the trackball's focus ring on the Battery card. The other pages look as on the [L2 Pro](wio-tracker-l2-pro.md) and the [ThinkNode M9](thinknode-m9.md#screens).

## Which file

| You want to… | File | How |
|---|---|---|
| install Cairn for the first time | `MeshCore-TDeckPlus-CairnN-<date>-full.bin` | write at `0x0` ([steps](../install/esp32-s3.md)). If it runs MeshCore, export your key and contacts in the app first. |
| update | `MeshCore-TDeckPlus-CairnN-<date>-update.bin` | USB at `0x10000`, or over Wi-Fi: Settings › System › Firmware update fetches it from the latest release (from Cairn 108 on), or a browser upload in Wi-Fi transfer |
| recover a device that won't boot | `MeshCore-TDeckPlus-CairnN-<date>-full.bin` | write at `0x0` |

The same files run on the T-Deck and the T-Deck Plus. Write the `-full.bin` or the `-update.bin`, never both.

**Download mode.** esptool and the web flasher can usually restart the T-Deck into download mode over USB by themselves. If they can't connect, switch the T-Deck off, hold the trackball in (it is the BOOT button), switch it on, then release it and connect again.

**Coming from another firmware.** Cairn keeps its identity, contacts and settings in the T-Deck's internal flash. Firmwares that keep them on the microSD card (Wadamesh does, in a `meshcomod` folder) don't carry over by themselves: Cairn starts with a new identity. Your files stay on the card. Cairn reads offline maps from the card's `Maps` folder (`cairn/maps` before Cairn 114; it moves by itself); you can download them on the device (from Cairn 119), or make them on a computer with [tools/maptiles.py](../../tools/maptiles.py).

## Known issues

- **GPS (T-Deck Plus):** checked on a unit with a u-blox GPS (from Cairn 118); a unit with the Quectel L76K hasn't been tried yet.
- **Battery percentage** hasn't been calibrated on the T-Deck yet. Screen-off standby has been measured (see Battery saver above); battery life in use hasn't.
- **Hibernate:** waking with the trackball click hasn't been confirmed.
- **Audio:** battery draw while playing or recording, hour-long recordings during radio traffic, and a card pulled mid-recording haven't been tried yet.
- **The full automated on-device test suite** hasn't been run on it yet. Please [report](https://github.com/cvhviz/Cairn/issues/new?template=bug_report.yml) anything that looks wrong.

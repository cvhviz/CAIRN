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

## Music and voice notes

From Cairn 113, tried on a T-Deck Plus. On the T-Deck an **Audio** card takes the GPS card's place on Home (the GPS tab still shows the satellites) and opens a Player and a Recorder.

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

**Coming from another firmware.** Cairn keeps its identity, contacts and settings in the T-Deck's internal flash. Firmwares that keep them on the microSD card (Wadamesh does, in a `meshcomod` folder) don't carry over by themselves: Cairn starts with a new identity. Your files stay on the card. Cairn reads offline maps from the card's `Maps` folder (`cairn/maps` before Cairn 114; it moves by itself); [tools/maptiles.py](../../tools/maptiles.py) makes them.

## Known issues

- **GPS (T-Deck Plus) hasn't been checked on hardware yet.**
- **Battery percentage** hasn't been calibrated on the T-Deck yet. Screen-off standby has been measured (see Battery saver above); battery life in use hasn't.
- **Hibernate:** waking with the trackball click hasn't been confirmed.
- **Audio:** battery draw while playing or recording, hour-long recordings during radio traffic, and a card pulled mid-recording haven't been tried yet.
- **The full automated on-device test suite** hasn't been run on it yet. Please [report](https://github.com/cvhviz/Cairn/issues/new?template=bug_report.yml) anything that looks wrong.

# LilyGO T-Display SF32 (with the keypad board)

✅ Tested on hardware · SiFli SF32LB52 · [install with one double-click](../install/sf32.md) · updates over Wi-Fi

LilyGO's T-Display SF32 has:
- a SiFli SF32LB52 (Cortex-M33)
- a 480×480 AMOLED touchscreen
- an SX1262 LoRa radio and an L76K GPS
- an ESP32-C6 for Wi-Fi
- a BHI260AP motion sensor
- a microphone and speaker
- an IR transmitter and microSD

The keypad board adds a 20-key phone-style keypad with backlight, a haptic motor and a BME280 climate sensor.

Cairn runs a native interface on it, built for the large square screen. It works with the official MeshCore apps over Bluetooth.

Its current files are in [Cairn 114](https://github.com/cvhviz/Cairn/releases/tag/cairn-v114): `MeshCore-TDisplaySF32-Cairn114-2026-10-12-install.zip` and `MeshCore-TDisplaySF32-Cairn114-2026-10-12-update.bin`. A board on Cairn 107, 108, 112 or 113 updates over Wi-Fi (with the keyboard board attached). A board on the very first SF32 build (6 Oct) needs the [USB installer](../install/sf32.md#if-your-board-has-the-first-sf32-build) once.

## Which file

| You want to… | File | How |
|---|---|---|
| install Cairn, or update over USB | `MeshCore-TDisplaySF32-CairnN-<date>-install.zip` | unzip, then double-click the installer for your computer ([steps](../install/sf32.md)). This keeps your identity, contacts and settings. |
| update over Wi-Fi | `MeshCore-TDisplaySF32-CairnN-<date>-update.bin` | the board fetches it itself: Settings › System › Firmware update (Cairn 107 and later), with the keyboard board attached: it carries the Wi-Fi chip |
| recover a board that won't start | the same `-install.zip` | hold A for 12 s, then run the installer again. Download mode is in ROM, so it always works. |

## Features

- **Home dashboard of cards:**
  - a header with a big clock and either a **mini spectrum** (one full-height graph of your channel that zooms to what the band is doing and colours each level by how often the channel sat there, from Cairn 113; tap it to open Spectrum) or **Date & info**. Switch in Settings › Home, or long-press the header;
  - battery, chats, nodes, radio (frequency, SF / BW and noise floor) and network (the GPS card left Home in Cairn 114: the sidebar shows the GPS);
  - board cards: Sensors (steps as its main value, with temperature, humidity and pressure; one card from Cairn 114), IR remote, Audio (Player and Recorder) and Tools.
  - Scroll down for more cards.
- **Sidebar tabs:** Home, Chats, Nodes, Radios, GPS and Settings, with coloured icons. The GPS icon is green while the GPS is on and red while it is off, paused for Wi-Fi, or the keyboard is unpowered (from Cairn 113).
- **Settings as cards:** Settings and every sub-page use dashboard-style cards (icon badge, title, big value, detail line), including System and Firmware update.
- **Themes:** the nine colour themes from the L2 Pro, plus red and Night modes. Text is a size larger throughout, and chats show colour emoji.
- **Chats:** channels and direct messages, typed on the keypad (multi-tap) or on the touchscreen. Messages sent from a phone app appear in the board's chats, and messages sent on the board appear in CairnOS (with the next CairnOS update).
- **Nodes:** list and cards views, ping, repeater scan and remote admin.
- **Node pages:** selecting a companion, repeater, room server or sensor opens a page of cards for it: signal, route, battery, last ping and, once logged in, its status, neighbours, readings and clock. The bar at the bottom follows the session: Message or Log in, Ping, then More, Admin or Refresh. The full admin console is one step further.
- **Radios** (tabs from Cairn 114): **1 LoRa**, **2 Wi-Fi** and **3 BLE**, by touch or keys 1, 2 and 3. LoRa has a live spectrum strip, a full-screen spectrum and band scan, and **Traffic**: the last hour's packets with a stats strip, each opening its details as tiles.
- **GPS:** position, satellites and a compass. Tap the compass for a full-screen view with all the GPS details.
- **Sensors:** temperature, humidity and pressure (keypad board), and a step counter.
- **IR remote:** large buttons, with brand and device chosen in its settings.
- **Audio (Player and Recorder):** one card for two apps that play music from the microSD card and record from the microphone, with a live audio spectrum. Recordings are saved to the card.
- **Charging:** the battery charges on USB. Cairn sets up the battery charger at boot and checks it every few seconds. The Battery page shows the charge state and, if the battery has a temperature sensor, whether it is too cold or too hot to charge.
- **Low battery:** on battery, below 3.55 V for a minute, a 30-second countdown starts, then the board powers off to protect the cell. Any key or USB cancels it. To wake it, plug in USB or hold D for 2 seconds.
- **Wi-Fi:** the keyboard's ESP32-C6 joins your network (Settings › Network). While Wi-Fi is on, the GPS is paused: the two share one connection.
- **Wi-Fi and Bluetooth scanners** (from Cairn 113; the Radios page's Wi-Fi and BLE tabs from Cairn 114): each has a Start button, a live plot and a list, and the scan status shows in the status bar. Keys: 4 Active, 5 Passive, 6 Plot / List, 7 Start. The Bluetooth radar opens full screen, and **Find** helps you walk towards a device, using the GPS course or the motion sensor for a heading. Wi-Fi scan needs the keyboard board.
- **Internet time:** on Wi-Fi the clock is set from the internet. In Settings › Time & location, Internet time is Off, Ask (the default) or **Always**. Ask corrects small differences silently and asks before a change of more than an hour ("Set clock from internet?": Not now, Set, Always). Always sets it without asking. A GPS fix still comes first.
- **Clock after a power loss:** the board saves the time to its flash every 15 minutes and before a restart or power-off. After a power loss it comes back with the last known time, shown as "Last known", until the GPS, the internet or the app sets it.
- **Wi-Fi updates:** Settings › System › Firmware update checks this repository's latest release, downloads the board's `-update.bin`, and checks its size, SHA-256 and board marker before it offers to install. The new build goes into a spare slot and runs on trial; it is kept only after it has run for a minute, otherwise the board goes back to the build it had. It needs USB with the battery switched on, or 30 % battery.
- **Bluetooth:** a companion link to the MeshCore apps, paired with the PIN shown on the screen.
- **Power:** the board sleeps deeply while the screen is off, and can hibernate. With **Wake on motion** on, picking it up wakes the screen.

## Power switch and the keyboard's battery

The side power switch picks which battery feeds the board:

| Switch | Core on its own | Docked on the keyboard |
|---|---|---|
| **ON** | the core's own battery | the core's own battery |
| **OFF** | no battery: the board runs only from USB | the keyboard's battery |

- **Install and update with the switch ON**, with the core off the keyboard. With the switch OFF and no keyboard, a USB install fails: the board restarts every 20 to 40 seconds once the flash tool takes over.
- **Docked and on battery, the switch turns the unit off** (from Cairn 112). Slide it OFF and a "Switched off" card counts down 5 seconds; any key cancels. Then the board saves everything and turns off. Slide it back ON and it starts within about 5 seconds (up to about 20 seconds on a board that was updated over Wi-Fi), or press A.
- **With USB plugged in, the switch does nothing** to a docked board: it keeps running from USB.
- You can also turn it off by holding A for 3 seconds and choosing Hibernate. A wakes it.
- The Battery page and the battery icon show whichever battery the switch connects. Cairn can't tell which one that is.
- On the core alone (not docked), moving the switch while running on battery restarts the board or cuts it: the power breaks as the switch moves.
- On USB with a flat battery, Cairn shows the USB symbol instead of a percentage and won't start a Wi-Fi update.

## Buttons and keys

| Control | Does |
|---|---|
| **C** (side) | click: turn the screen off or wake it; double-press: unlock; hold: lock |
| **A** (side) | click: Settings; double-press: new message; hold 1–3 s: back; triple-press: mute; hold 3 s: power menu (Hibernate, Restart). It also wakes the board from hibernate. Held 12 s, it restarts the chip even when the firmware is stuck. |
| **B** (side) | click: alert profile; hold: flashlight |
| **D** (side) | not used by the interface. Hold 2 s: wakes the board after a low-battery power-off. Hold about 20 s: the battery charger cuts the power for a moment and the board restarts, for a board that stops responding. |
| ▲ / ▼ | move up and down. On values and sliders, **up always means more**. |
| OK | select; hold: context menu |
| Back | back. On Home with the sidebar selected, it turns the screen off. |
| Home | Home tab; hold: quick panel |
| Mail | newest unread message; hold: new message |
| Stop | stop an alert or dismiss a pop-up; hold: mute |
| 0–9 | Home card shortcuts; letter jump in lists; typing in chats |

The side buttons can be changed in Settings › Controls. Without the keypad board: B steps forward, B double-press steps back, and A selects.

## Known issues

- **No USB-serial companion.** The board's only USB port is the CH343 console, so connect the MeshCore apps over Bluetooth.
- **Wi-Fi after re-docking.** After the core is taken off the keyboard and docked again, Wi-Fi may not come back by itself. Restart the board (hold A for 3 seconds, Restart) and it reconnects. Wi-Fi updates from GitHub work: 107 to 108 was tested end to end.
- **The Windows installer hasn't been run on a Windows PC yet.** Please [report](https://github.com/cvhviz/Cairn/issues/new?template=bug_report.yml) how it goes.
- **No offline map yet.** It's coming in a later release.
- **The IR transmitter hasn't been checked against a TV yet.** Its codes follow the public IR databases.
- **Battery life with the screen off hasn't been measured yet.**
- **Waking on a received LoRa message hasn't been confirmed on hardware yet.**
- **Wi-Fi and Bluetooth scanners** (Cairn 113): both ran on the board. Touch scrolling of the lists, a scan with the app connected, and the screen-off and idle stops haven't been tried yet.
- **Node pages are new in this build.** Please report anything that looks wrong.

Problems? [Report a bug](https://github.com/cvhviz/Cairn/issues/new?template=bug_report.yml). Please include the build number from the splash screen.

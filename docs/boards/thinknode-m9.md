# Elecrow ThinkNode M9

✅ Tested on hardware, beta · ESP32-S3 · [install with esptool or the web flasher](../install/esp32-s3.md) · updates over Wi-Fi (Settings › System › Firmware update)

The ThinkNode M9 is a handheld with:
- an ESP32-S3 (16 MB flash, 8 MB PSRAM)
- a Semtech LR1110 LoRa radio
- a 2.4" 320×240 ST7789 screen, without touch
- a QWERTY keyboard with a d-pad and a row of function keys
- a CC1167Q GPS, a real-time clock and a microSD slot
- a piezo buzzer, a power slider and a RESET button
- a WCH USB-serial chip on its USB-C port

Cairn runs the same interface as the [Wio Tracker L2 Pro](wio-tracker-l2-pro.md) on it, driven by the keys: a ring shows what is selected, the d-pad moves it and OK taps it, exactly as a finger would. Typing goes straight into chats. The [Cairn manual](../Cairn_Firmware_Manual_Dark.pdf) describes the screens and the M9's keys.

**Beta** means it is tested on hardware but new to Cairn. It passes Cairn's full on-device test suite (13 of 13): boot, the Home cards, Settings, the quick panel, the lock screen, Radio, Spectrum and Band scan, the GPS map, a walk over every page and sheet by keys, and quick key runs. Some features haven't been tried on the M9 yet; they are listed under [Known issues](#known-issues).

## Screens

Captured on an M9 running Cairn 108 (the focus ring shows which item the keys are on).

| | |
|---|---|
| ![Battery](../screens/m9/battery.png)<br>Battery | ![Spectrum](../screens/m9/spectrum.png)<br>Spectrum |
| ![Quick panel](../screens/m9/quick-panel.png)<br>Quick panel | ![Settings](../screens/m9/settings.png)<br>Settings |

## Which file

| You want to… | File | How |
|---|---|---|
| install Cairn for the first time | `MeshCore-ThinkNodeM9-CairnN-<date>-full.bin` | full erase, then write at `0x0` ([steps](../install/esp32-s3.md)). **Erases everything**: if it runs MeshCore, export your key and contacts in the app first. |
| update | `MeshCore-ThinkNodeM9-CairnN-<date>-update.bin` | USB at `0x10000`, or over Wi-Fi: Settings › System › Firmware update (from Cairn 107) fetches it from the latest release, or a browser upload in Wi-Fi transfer (from Cairn 112). |
| recover a device that won't boot | `MeshCore-ThinkNodeM9-CairnN-<date>-full.bin` | full erase, then write at `0x0` |

Write the `-full.bin` or the `-update.bin`, never both. Coming from Elecrow's firmware, Meshtastic or stock MeshCore, use the `-full.bin`.

**Download mode is automatic.** The M9's USB-serial chip lets esptool and the web flasher restart it into download mode, so there is no Boot button to hold. If they can't connect, unplug and replug the USB cable, try another cable, and close anything else using the port (the MeshCore web app, a serial monitor). On Windows, if no COM port appears, install WCH's CH340 driver.

## Keys

| Key | Press | Hold |
|---|---|---|
| d-pad arrows | move the selection; in a list, step through the rows; on a value, left / right change it | — |
| OK (d-pad centre) | tap what is selected; in a text field, send; on a slider or stepper, adjust mode (then up / down change it too, **up means more**); locked, twice unlocks | long press of what is selected (a Files row's menu, message details, hold-to-confirm buttons; 700 ms from Cairn 119); locked: unlock |
| BACK | leave adjust or pan mode, close a menu, go back (unsaved edits ask first), then Home | — |
| HOME | close what is open and go Home | — |
| MSG | Chats | — |
| @ | new message | — |
| ADV | the Send advert menu | GPS on / off |
| MAP | the GPS map; on the map, pan mode (arrows pan, OK taps the centre; the map's controls hide until it ends, from Cairn 119) | — |
| CTRL | the quick panel (again: close it) | — |
| MIC | turn the screen off | — |
| DEL | backspace in a text field; on a Files row, asks to delete the file or folder (from Cairn 119) | delete the word before the cursor |
| letters | type in a text field; in a conversation, start a reply; in the new-message picker, search; `+` / `-` zoom the map | — |

- Any key wakes a dark screen, and only wakes it.
- Up past the top of Nodes scans for repeaters (the touch boards' pull down to scan).
- The keyboard sends one press per key and nothing while it is held, so holding an arrow moves once. Quick repeated presses go further instead: in a list, after six quick presses each one moves two rows, then four.
- A page with nothing to select (Battery, About) shows no ring: up and down scroll it, left goes to the sidebar, BACK leaves.
- RESET restarts the M9. The power slider disconnects the battery.

## Features

The L2 interface, as on the [L2 Pro page](wio-tracker-l2-pro.md#features): the sidebar, the Home dashboard, chats with colour emoji, nodes, repeater scan and remote admin, the quick panel, GPS with Off / On / Eco, settings as tiles (from Cairn 112) that apply at once, except radio, connection and security changes (from Cairn 111), themes, the screensaver, notices in the status bar, sent-message sync with CairnOS, the lock screen, Wi-Fi with the MeshCore app over Wi-Fi, and the Wi-Fi and Bluetooth scanners with the full-screen Bluetooth radar and Find (from Cairn 113; the d-pad moves between the radar's dots). Wi-Fi, Bluetooth and GPS ask before they switch on or off (from Cairn 113). On the M9 also:

- **Spectrum and Band scan on the LR1110.**
- **Battery page** (redesigned in Cairn 113): the percent, the voltage and a status line ("On battery · 9h 40m left"), six cells (time left or to full, rate, time in this state, today's low and high, the last full charge, and the screen-on share, or the mode while Battery saver is on), and a graph over 1 hour, 6 hours, 24 hours or 7 days in % or volts, with markers for plug-in, unplug, full, warnings, restarts and Battery saver changes. OK on the graph puts a cursor at now; left and right move it. The week's history comes back after a restart, once the clock is set.
- **Keyboard light** (Settings › Hardware › Display, under Brightness, and the quick panel's keyboard slider): the level the keys light at, or Off. The keyboard controller lights the keys at a key press for 10 s; they stay dark while the screen is dark or locked, and go dark 2 s before the screen times out (from Cairn 112).
- **Battery saver** (Settings › Hardware › Display › Power, off by default, beta): while the screen is dark it turns Bluetooth off and lets the chip sleep between radio packets. A key still wakes the screen. Turning Bluetooth back on restarts the device.
- **Automatic power-off** below 3.3 V on battery, to protect the cell.
- **MIC** turns the screen off.
- **Nodes Cards view:** the keys focus one card at a time; left and right move between the two in a row (from Cairn 112).
- **Clock after a power cut** (from Cairn 115): the clock shows "--:--" until GPS, the app or Wi-Fi sets it, instead of the time the power slider was switched off ([#18](https://github.com/cvhviz/CAIRN/issues/18)).
- **Radios** (from Cairn 114): LoRa, Wi-Fi and Bluetooth tabs, and a full-screen Traffic log with packet details. The Storage page has Files (from Cairn 114); USB drive mode isn't on the M9, whose USB-C is a serial bridge.
- **LoRa tab:** the keys land on Advert, and the advert sheet opens with Send focused, so Advert, OK sends a zero-hop advert (from Cairn 113).
- **Ocean theme** is a few steps darker, so it no longer looks washed out on this screen (from Cairn 113).
- **microSD:** the card mounts (a 16 GB card was tested); Settings › Hardware › Storage sees it.
- **Maps** (from Cairn 119): the GPS tab opens on the full-screen Map, and the keys start on its compass (GPS data). Download an area to the card over Wi-Fi (the Map's menu › **Download area…**), or use the online map with no card, as on the [L2 Pro](wio-tracker-l2-pro.md#features). Downloads no longer stop with "Card write failed": a write the card refuses for a moment is tried again, and a 1,731-tile (44 MB) download finished on an M9 with no card error.
- **From Cairn 119** also: posting to a room you just logged in to works (no more "Recipient gone"); the CairnOS app (build 12 or later) shows this radio's Spectrum Channel view and receives its chat history.
- **From Cairn 120:** telemetry from your contacts and the Share telemetry setting (Settings › GNSS › Telemetry), Settings renamed LoRa, Network and GNSS with color-coded lines and the LoRa settings on one screen, room posts with their poster and time, streets past a big downloaded area, fuller traffic lines, about 55-65 KB more free memory, and Battery saver sleeping with Wi-Fi on away from your networks.

## Known issues

- **Battery saver hasn't run on the device yet.** Its savings are estimates from datasheets; treat it as an experiment.
- **Online updates work:** an M9 updated itself over Wi-Fi from GitHub (107 to 108). A new build starts on trial and goes back to the old one by itself if it fails to start.
- **Unplugging USB:** whether the status bar switches from the plug to the battery when you unplug hasn't been confirmed yet.
- **Hibernate:** a key may not wake the board. The power slider (off, then on) or RESET always does.
- **Battery percentage:** the curve for the M9's 4.35 V cell is provisional until a full discharge is measured. While Wi-Fi is on the battery can't be read, so the Battery page says "Reading paused · Wi-Fi".
- **Not reachable by keys yet:** the Home header's long press (Settings › System › Clock gets there) and the Spectrum plots' tap-for-readout.
- **Settings › Hardware › Buttons** configures a button the M9 doesn't have, and Tap to wake does nothing here.
- The motion sensor and compass chip aren't used; the GPS page's compass follows your course.
- A V1.1 board (keyboard controller at I2C 0x6D) should work, but only V1.0 has been tried.

Problems? [Report a bug](https://github.com/cvhviz/Cairn/issues/new?template=bug_report.yml). Please include the build number from the splash screen.

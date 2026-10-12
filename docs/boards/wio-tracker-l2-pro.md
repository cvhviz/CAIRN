# Seeed Wio Tracker L2 Pro

✅ Tested on hardware · ESP32-S3 · [install with esptool or the web flasher](../install/esp32-s3.md) · updates over Wi-Fi

[![Cairn on the Wio Tracker L2 Pro](../promo/01_cairn_hero.jpg)](../promo/01_cairn_hero.jpg)

Wio-S3 module (ESP32-S3, 16 MB flash, 8 MB PSRAM), SX1262 LoRa (TCXO 3.0 V), 3.2" 320×240 NV3031B LCD with GT911 touch, L76K GPS, ES8311 speaker and microSD.

- [Brochure (PDF)](../Cairn_Wio_L2_Pro_Brochure.pdf) · [User manual (PDF)](../Cairn_Wio_L2_Pro_User_Manual.pdf) · [Screens](#screens)
- Offline-map tool: [tools/maptiles.py](../../tools/maptiles.py) ([guide](../../tools/MAPTILES.md))

## Which file

| You want to… | File | How |
|---|---|---|
| install Cairn for the first time | `MeshCore-WioL2Pro-CairnN-<date>-full.bin` | full erase, then write at `0x0`. **Erases everything**: export your key and contacts in the app first. |
| update | `MeshCore-WioL2Pro-CairnN-<date>-update.bin` | online (Settings › System › Firmware update), a browser upload in Updater mode, or USB at `0x10000` |
| recover a device that won't boot | `MeshCore-WioL2Pro-CairnN-<date>-full.bin` | full erase, then write at `0x0` |

Write the `-full.bin` or the `-update.bin`, never both. If the device last updated over Wi-Fi, run `esptool --chip esp32s3 erase-region 0xe000 0x2000` before a USB write of the `-update.bin` ([why](../install/esp32-s3.md#if-the-device-last-updated-over-wi-fi)).

## Buttons

| Button | Does |
|---|---|
| WAKE (side) | click: turn the screen off, or wake it; double-press: unlock; hold: lock |
| User (also the Boot button, GPIO0) | click: quick panel; double-press: new message (unlocks instead when the device is locked); hold: back; triple-press: mute. The first press on a dark screen only wakes it. It is the button that wakes the board from hibernate. Click, double and hold can be reassigned in Settings. |
| User + Reset | hold **User (Boot)**, tap **Reset**, release: download mode for esptool |
| Reset | restart |

## Features

- **Side icon rail**: Home, Chats, Nodes, Radio, GPS and Settings, with unread and new-advert badges. The GPS icon is green while the GPS is on and red while it is off (from Cairn 113). A status bar shows the page title (in its tab's colour), a 12-hour clock, Bluetooth, GPS and battery. Notices take the status bar over for a moment (from Cairn 112); tap one with a chevron to open what it is about.
- **Home dashboard**: a large clock with sunrise/sunset, temperature and channel-busy readouts, plus live cards for battery, chats, nodes, Audio (from Cairn 113, in the GPS card's place; the GPS tab still shows the satellites), radio and network. A tap on the big clock opens the quick panel.
- **Chats**: channels, direct messages and rooms in one list, message bubbles, a full on-screen keyboard with emoji, quick replies and a byte counter.
- **Colour emoji**: 229 Noto emoji drawn inline in messages, previews and node names.
- **Nodes**: recent adverts and saved contacts as a list or cards, with hops, last heard, distance, the short ID and position. Companions show a walkie-talkie and repeaters a mast, as in CairnOS. Node detail shows heard, distance, bearing, path, position and the last ping, with ping, chat and map; tap the short key for a **QR code** the MeshCore apps scan to add the contact (from Cairn 111).
- **Repeater tools**: a repeater scan (who hears you, whom you hear) and remote admin for repeaters and room servers.
- **Radio**: frequency and settings, Now/Floor/Peak/Margin meters, a live signal graph and the last packets heard, each in its own card, with a large Advert button.
- **Spectrum and band scan**: your channel over 10 s to 1 h, and a sweep of the whole band with a waterfall.
- **Wi-Fi and Bluetooth scanners** (Home › Network, from Cairn 113): **Wi-Fi scan** shows the 2.4 GHz networks around you as arcs by channel and signal, with a bar per channel for how crowded it is; **BT scan** shows the Bluetooth devices in range as bars over a radar, MeshCore nodes named. Each has a list with details. The Bluetooth radar opens full screen, and **Find** helps you walk towards a device (Closer, Farther, Steady, with an optional tone). Scans start only when you tap Start and stop when you leave the page.
- **Quick panel**: Wi-Fi, Bluetooth, GPS and sound toggles, lock, flashlight, advert, brightness and volume, and Radio, Theme and Settings buttons (from Cairn 112). Wi-Fi, Bluetooth and GPS ask before they switch on or off (from Cairn 113).
- **GPS**: position in ft/mph with a course compass, an on/off switch, Off / On / Eco modes (Eco shows when the next fix is due), and an **offline map** from microSD tiles with pinch to zoom. Tap the status or any card for **GPS data**: satellites, HDOP, grid square, GPS time and the NMEA stream (from Cairn 111).
- **Settings**: six tiles (Radio, Connect, Hardware, Location, Appearance, System), each with three lines of what it holds. Every page under them is tiles too (from Cairn 112): two across, each with an icon, its name and its value; a tap flips a switch on its tile, and other values open a small sheet. Appearance, Display, Sound, Buttons, Wake & lock and Clock apply as you change them; Radio, Bluetooth, the PIN, Wi-Fi, Join channel and Profile are drafts with Cancel and Save (from Cairn 111). Destructive actions need a hold (the tile says how long) plus a confirmation. **Settings › Radio** shows TX power and every LoRa setting (preset, frequency, bandwidth, spreading factor, coding rate), each editable, with a typed frequency for a custom radio, and the **path hash** size (1–3 bytes per hop, from Cairn 111).
- **Themes** (Settings › Appearance › Theme, from Cairn 111): Dark, Neon, Light, Sunlight, Night, Ocean, Cartoon, Red Radar and Green Radar, previewed live.
- **Screensaver** (Settings › Appearance › Screensaver, from Cairn 112): Beacon, Ambient, Night clock or Auto, in place of a screen that never times out (Screen timeout Never, or Stay on USB). It runs on USB power by default, starts after 1–30 minutes without a touch, and on battery hands over to a real screen-off after a time you choose.
- **Battery** (redesigned in Cairn 113): the percent, the voltage and a status line ("On battery · 9h 40m left"), six cells (time left or to full, rate, time in this state, today's low and high, the last full charge, the screen-on share), and a graph over 1 h to 7 days in % or volts with markers for plug-in, unplug, full, warnings and restarts. Tap the graph for a readout. The week's history comes back after a restart, once the clock is set.
- **Music player** (from Cairn 113): put MP3 or WAV files in a `Music` folder on the microSD card and play them from the Audio card, with a live spectrum, seek, volume, repeat and shuffle. Music keeps playing with the screen dark; a message alert pauses it and it carries on after the tone.
- **Sound**: volume and a choice of alert tone per event.
- **Wake & lock**: tap to wake, auto-lock, and a pocket-safe lock screen.
- **Clock**: 12h / 24h / analog, US time zones or a custom offset, and internet time over Wi-Fi; *Always take internet time* skips the question when the clock is off by over an hour (from Cairn 111).
- **Wi-Fi**: on-device setup, clock sync, the MeshCore app over Wi-Fi, **online updates** from this repository's releases (checked once a day; nothing installs without your confirmation), and **Updater mode** for an update sent from a browser (from Cairn 112; CairnOS can start one with its next update, after you tap Allow on the board).
- **Sent-message sync** (from Cairn 112): messages a phone app sends appear in the board's chats, with the delivered tick when the ACK arrives; messages sent on the board appear in CairnOS, or wait until it next syncs.

## Screens

The Cairn interface on the L2 Pro's 3.2" touch screen. The Heltec V4 touch, ThinkNode M9 and T-Deck run the same interface.

|                                                                          |                                                                    |                                                                    |
| ------------------------------------------------------------------------ | ------------------------------------------------------------------ | ------------------------------------------------------------------ |
| ![Home](../screens/01-home.png)<br>Home                                  | ![Chats](../screens/02-chats.png)<br>Chats                         | ![Conversation](../screens/03-conversation.png)<br>Conversation    |
| ![Keyboard](../screens/04-keyboard.png)<br>Keyboard                      | ![Nodes](../screens/05-nodes.png)<br>Nodes                         | ![Node detail](../screens/06-node-detail.png)<br>Node detail       |
| ![Radio](../screens/07-radio.png)<br>Radio                               | ![GPS](../screens/08-gps.png)<br>GPS                               | ![Settings](../screens/09-settings.png)<br>Settings                |
| ![Lock screen](../screens/10-lock-screen.png)<br>Lock screen             | ![Quick panel](../screens/11-quick-panel.png)<br>Quick panel       | ![Spectrum](../screens/12-spectrum.png)<br>Spectrum                |
| ![Band scan](../screens/13-band-scan.png)<br>Band scan                   | ![Map](../screens/14-map.png)<br>Map                               | ![Repeater scan](../screens/15-repeater-scan.png)<br>Repeater scan |
| ![Repeater admin](../screens/16-repeater-admin.png)<br>Repeater admin    | ![Nodes as cards](../screens/17-nodes-cards.png)<br>Nodes as cards | ![Channels](../screens/18-channels.png)<br>Channels                |
| ![Firmware update](../screens/19-firmware-update.png)<br>Firmware update |                                                                    |                                                                    |

Screens use fictional sample data.

## Known issues

- Battery figures with the screen off are estimates; they haven't been measured yet.
- **No voice recorder.** The recorder is off on the L2 Pro: the microphone gives only silence on our unit, and Seeed lists it as reserved. It stays off until we know more.
- The offline map needs a **FAT32** card (8–32 GB SDHC recommended). exFAT cards aren't read.
- Check each build's release notes for anything new.

Problems? [Report a bug](https://github.com/cvhviz/Cairn/issues/new?template=bug_report.yml).

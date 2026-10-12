# Seeed Wio Tracker L1 Pro

✅ Tested on hardware · nRF52840 · [install with UF2](../install/nrf52-uf2.md)

nRF52840, SX1262 LoRa, L76K GPS, piezo buzzer, a five-way joystick and a Back button. Cairn has four images for it: three companion builds for different screens, and a room server.

## Which file

| Your L1 has… | File |
|---|---|
| the stock SH1106 OLED (most units) | `MeshCore-WioL1Pro-CairnN-<date>.uf2` |
| a 2.42" SSD1309 OLED on the Grove port ("DV1") | `MeshCore-DV1-CairnN-<date>.uf2` |
| a 2.13" e-ink panel | `MeshCore-WioL1Eink-CairnN-<date>.uf2` |
| a room server role (no phone app; SH1106 OLED) | `MeshCore-WioL1RoomServer-CairnN-<date>.uf2` |

Install, update and recovery all use the same file: double-tap **Reset** and copy the `.uf2` onto the drive that appears ([details](../install/nrf52-uf2.md)). Updating keeps your identity, contacts, channels and settings. Switching between the screen variants keeps them too.

## Buttons

| Button | Does |
|---|---|
| Joystick up / down / left / right | move between pages and items |
| Joystick press | select |
| Back (menu) | back out of a page or menu |
| Reset | restart; **double-tap** for the UF2 drive |

## Features

- Works with the official MeshCore apps over Bluetooth (PIN on the screen).
- Cairn splash with the build number and build stamp.
- Page tabs along the bottom or down the side (Settings > Page tabs). With the side rail, up and down step between pages and left and right switch the page's own view.
- Settings in six categories: Radio, Connect, Location, Display, Sound and System (from Cairn 113). System › About shows the build, MeshCore version, node name and key prefix.
- Messages sent from the phone app appear on the L1 as yours, and a delivered direct message shows a ✓ (from Cairn 113). With CairnOS, messages sent on the L1 also appear in the app. This needs a CairnOS version with sent-message sync (TestFlight).
- GPS: position, a compass and a GPS data view with satellites, HDOP, the grid square and the fix age (from Cairn 113). A click of the joystick steps through them. Eco mode, also from the app.
- **Path hash** (1 to 3 bytes per hop) and **Units** (imperial or metric) in Settings (from Cairn 113). 12-hour clock.
- A thin line under the title flashes when the radio sends or receives (OLED builds, from Cairn 113).
- Room server image with the CLI over USB serial.

## Known issues

- The three-colour e-ink panel isn't supported: every refresh is a ~15 s full flash. Use a black-and-white 2.13" panel.
- Check the release notes of each build for anything new.

Problems? [Report a bug](https://github.com/cvhviz/Cairn/issues/new?template=bug_report.yml) with the image name and the build number from the splash.

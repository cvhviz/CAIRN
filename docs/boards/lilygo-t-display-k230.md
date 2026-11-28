# LilyGO T-Display K230 Kit

✅ Beta: tested on hardware, new to Cairn · Kendryte K230 (RISC-V, Linux) · LR2021 radio · installed from the board's console · from Cairn 140

Cairn's own interface and MeshCore run as one Linux program on the K230 kit's 1232×568 AMOLED (rounded corners, touch), with LilyGO's keyboard base. The kit's radio is the LR2021: this build is not for other K230 boards. LilyGO's launcher stays installed, one key away.

| Part | In Cairn 140 |
|---|---|
| Screen and touch | landscape layouts made for the wide screen: an eight-tile Home with a clock, date and eight readings in its header, Battery, Nodes, Spectrum (with a Live view), Radios, the Player and Recorder |
| Radio | LR2021 LoRa: send and receive, the Spectrum page, extra spreading factors (`set extra.sf`) |
| Keyboard base | typing; F1–F6 pick the side tabs; the Mic key opens the Recorder; the LilyGO key goes Home (hold it for LilyGO's launcher); the key light (dark 10 s after the last key); three LEDs: Caps Lock, unread messages, LoRa activity |
| Batteries | the base's two cells: percent, charging, and a Battery page with current, power, temperature, capacity, health, cycles and the USB input |
| Sound | alerts and the music player through the base's speaker; the Recorder on the board's mic |
| GNSS | the base's nRF9151 (reception was weak in the one outdoor test so far) |
| Bluetooth | a scanner (Radios › Bluetooth) through the base's nRF52840 |
| Wi-Fi | joining, the app over Wi-Fi, online maps (OpenFreeMap) |

**Not yet tried or not in this build:** the Bluetooth phone link (a bridge firmware for the nRF52840 is attached to the release, untested: see its notes), online updates, the camera, the data USB port.

## Which file

Download from the [K230 beta release](https://github.com/cvhviz/CAIRN/releases/tag/experimental-tdisplay-k230-140): it isn't in the main release and no online update offers it.

| File | Use |
|---|---|
| `MeshCore-TDisplayK230-Cairn140-<date>-cairn-bin` | the program: `/root/cairn-bin` |
| `MeshCore-TDisplayK230-Cairn140-<date>-cairn-switch` | brings Cairn back from LilyGO's launcher: `/root/cairn-switch` |
| `MeshCore-TDisplayK230-Cairn140-<date>-S99zz_cairn` | the boot script: `/etc/init.d/S99zz_cairn` |
| `MeshCore-TDisplayK230-Cairn140-<date>-nrf52840-bridge.uf2` / `.zip` | optional, untested: Cairn's Bluetooth bridge for the base's nRF52840 |

The release notes have the install steps (the kit's USB console, 115200 baud, user root).

## Switching between Cairn and LilyGO's launcher

- **Cairn → launcher:** hold the LilyGO key about a second and choose Open, or Settings › Maintenance › LilyGO launcher.
- **Launcher → Cairn:** press the power key three times quickly.
- The board boots into whichever you used last.

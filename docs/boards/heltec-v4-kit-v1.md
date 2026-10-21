# Heltec WiFi LoRa 32 V4 + Expansion Kit V1 (touch)

🧪 Preview: **not yet tested on hardware** · ESP32-S3 · [install with esptool or the web flasher](../install/esp32-s3.md) · updates over Wi-Fi

The plain Heltec V4 (ESP32-S3, 16 MB flash, 2 MB quad PSRAM; SX1262 with a GC1109 front end on a V4.2 or a KCT8103L on a V4.3) in Heltec's Expansion Kit V1 case, with a 2.8" 240×320 ST7789 touchscreen and a piezo. From Cairn 121 it runs the same touch interface as the [Expansion Kit V2 build](heltec-v4-touch.md), without the map.

**Nobody here has a V1 kit, so this build has not run on a device yet.** Its pins come from Heltec's datasheet, Meshtastic's and upstream MeshCore's files, none measured on a unit. If you have one, please try it and [report](https://github.com/cvhviz/Cairn/issues/new?template=bug_report.yml) what works and what doesn't, even "it works".

**This build is for a standard V4** (`esptool chip-id` reports *Embedded PSRAM 2MB*) **in the Expansion Kit V1**. A V4-R8 (*8MB*) in the Expansion Kit V2 needs the [Heltec V4 touch build](heltec-v4-touch.md). The two images carry different firmware markers and refuse each other over Wi-Fi.

## Which file

| You want to… | File | How |
|---|---|---|
| install Cairn for the first time | `MeshCore-HeltecV4KitV1-CairnN-<date>-full.bin` | full erase, then write at `0x0`. **Erases everything**: export your key and contacts in the app first. |
| update | `MeshCore-HeltecV4KitV1-CairnN-<date>-update.bin` | online (Settings › System › Firmware update), a browser upload in Wi-Fi transfer, or USB at `0x10000` |
| recover a device that won't boot | `MeshCore-HeltecV4KitV1-CairnN-<date>-full.bin` | full erase, then write at `0x0` |

The first build is in [Cairn 121](https://github.com/cvhviz/Cairn/releases/tag/cairn-v121): `MeshCore-HeltecV4KitV1-Cairn121-2026-10-21-full.bin` and `MeshCore-HeltecV4KitV1-Cairn121-2026-10-21-update.bin`. Write the `-full.bin` or the `-update.bin`, never both. Download mode: hold **PRG**, tap **RST**, release **PRG**.

## Buttons

| Button | Does |
|---|---|
| PRG (USER) | click: quick panel; double-press: new message (unlocks instead when the device is locked); hold: lock now. It wakes the board from hibernate. |
| RST | restart |

PRG is the only button this build uses. Heltec's datasheet shows a second case button on GPIO 35, the same pin as the white TX LED; until someone checks how the two are wired, it is left out.

## Against the Expansion Kit V2 build

- **No map, card storage or map downloads.** No microSD is known on this kit, and its 2 MB of PSRAM could not hold the map cache anyway. Settings › Map and Storage show them as not available; the Online map, Map cache and Screenshot are left out.
- **PRG only** (see above).
- **TX power** shows the radio's setting, not the power at the antenna.
- **FEM LNA:** on a V4.3 (KCT8103L) the tile works; on a V4.2 (GC1109, no LNA switch) it reads "Not on this radio". Boosted RX stays on both.
- The Spectrum page, chats, nodes, repeater admin, Wi-Fi with online updates, the Wi-Fi and Bluetooth scanners, the Battery page, Battery saver and portrait mode (the Quick panel's Rotate) are as on the [Kit V2 build](heltec-v4-touch.md#features).

## Not yet checked

Everything, since no one here has the kit. In particular:

- that it boots and the screen lights (the splash should say "Heltec Kit V1"), with the right rotation and colors
- touch: whether taps land where drawn, in landscape and portrait
- list scrolling with no garbled rows
- the piezo's alert tones and startup sound
- the battery reading (it should top out near 4.20 V on USB), the battery curve and the low-battery shutdown
- radio TX and RX on a V4.2 and a V4.3, the FEM LNA tile, and the TX LED
- the GPS: a fix, and GPS Off really off
- PRG's click, double-press and hold; hibernate and waking from it
- Battery saver, and Wi-Fi with an update check while Bluetooth is up

Problems? [Report a bug](https://github.com/cvhviz/Cairn/issues/new?template=bug_report.yml). Please include the build number from the splash screen and, if you can, a serial log of the first boot.

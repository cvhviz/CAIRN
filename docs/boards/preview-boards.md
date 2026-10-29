# Preview boards

🧪 **Preview: these images build from the Cairn tree but haven't been tried on hardware yet.** They take the stock MeshCore companion setup for each board (pins, radio, power) and add Cairn's one-button interface from the [Heltec T096](heltec-t096.md), in colour with the T096's themes on the ST7735 boards (Heltec Wireless Tracker V1/V2, Heltec T1) and in monochrome on OLED boards, plus the Cairn splash and the fork's shared mesh, storage and radio fixes.

If you try one, please [report back](#reporting), even if it just works. A board moves to ✅ once someone has used it on real hardware.

## File names

| Chip | Files | Install |
|---|---|---|
| nRF52840 | `MeshCore-<Board>-CairnN-<date>-ble.uf2` (Bluetooth companion) and `-usb.uf2` (USB serial companion) | [UF2](../install/nrf52-uf2.md): double-tap Reset, copy |
| ESP32 / ESP32-S3 | `MeshCore-<Board>-CairnN-<date>-ble-full.bin` / `-ble-update.bin`, and the same for `-usb` | [esptool or web flasher](../install/esp32-s3.md): first install `-full.bin` at `0x0` after an erase; update `-update.bin` at `0x10000` |

Some boards have only a Bluetooth or only a USB image. Preview boards don't update over Wi-Fi (only the L2 Pro, Heltec V4 touch kits, ThinkNode M9, T-Deck and T-Display SF32 do); update them over USB the way they were installed.

**Before a first ESP32 install, export your private key and contacts in the MeshCore app**: the `-full.bin` erases everything.

## Boards and files

Files in the current preview release, [Cairn 107 preview](https://github.com/cvhviz/CAIRN/releases/tag/cairn-v107-preview):

| Board | File | Use |
|---|---|---|
| **nRF52840 (`.uf2`: double-tap Reset, copy)** | | |
| 🧪 B&Q Nano G2 Ultra | `MeshCore-NanoG2Ultra-Cairn107-2026-10-05-ble.uf2` | companion over Bluetooth |
|  | `MeshCore-NanoG2Ultra-Cairn107-2026-10-05-usb.uf2` | companion over USB serial |
| 🧪 GAT562 30S Mesh Kit | `MeshCore-GAT562MeshKit-Cairn107-2026-10-05-ble.uf2` | companion over Bluetooth |
|  | `MeshCore-GAT562MeshKit-Cairn107-2026-10-05-usb.uf2` | companion over USB serial |
| 🧪 GAT562 Mesh Tracker Pro | `MeshCore-GAT562TrackerPro-Cairn107-2026-10-05-ble.uf2` | companion over Bluetooth |
|  | `MeshCore-GAT562TrackerPro-Cairn107-2026-10-05-usb.uf2` | companion over USB serial |
| 🧪 GAT562 Mesh Watch13 | `MeshCore-GAT562Watch13-Cairn107-2026-10-05-ble.uf2` | companion over Bluetooth |
| 🧪 Heltec T1 (colour TFT) | `MeshCore-HeltecT1-Cairn107-2026-10-05-ble.uf2` | companion over Bluetooth |
|  | `MeshCore-HeltecT1-Cairn107-2026-10-05-usb.uf2` | companion over USB serial |
| 🧪 Keepteen LT1 | `MeshCore-KeepteenLT1-Cairn107-2026-10-05-ble.uf2` | companion over Bluetooth |
|  | `MeshCore-KeepteenLT1-Cairn107-2026-10-05-usb.uf2` | companion over USB serial |
| 🧪 LilyGO T-Impulse Plus | `MeshCore-TImpulsePlus-Cairn107-2026-10-05-ble.uf2` | companion over Bluetooth |
| 🧪 Meshtiny | `MeshCore-Meshtiny-Cairn107-2026-10-05-ble.uf2` | companion over Bluetooth |
|  | `MeshCore-Meshtiny-Cairn107-2026-10-05-usb.uf2` | companion over USB serial |
| 🧪 ProMicro | `MeshCore-ProMicro-Cairn107-2026-10-05-ble.uf2` | companion over Bluetooth |
|  | `MeshCore-ProMicro-Cairn107-2026-10-05-usb.uf2` | companion over USB serial |
| 🧪 RAK3401 | `MeshCore-RAK3401-Cairn107-2026-10-05-ble.uf2` | companion over Bluetooth |
|  | `MeshCore-RAK3401-Cairn107-2026-10-05-usb.uf2` | companion over USB serial |
| 🧪 RAK4631 | `MeshCore-RAK4631-Cairn107-2026-10-05-ble.uf2` | companion over Bluetooth |
|  | `MeshCore-RAK4631-Cairn107-2026-10-05-usb.uf2` | companion over USB serial |
| **ESP32-S3 (`-full.bin` / `-update.bin`)** | | |
| 🧪 Ebyte EoRa-S3 | `MeshCore-EoRaS3-Cairn107-2026-10-05-ble-full.bin` | companion over Bluetooth; first install or recovery: `0x0` after a full erase |
|  | `MeshCore-EoRaS3-Cairn107-2026-10-05-ble-update.bin` | companion over Bluetooth; update: `0x10000` |
|  | `MeshCore-EoRaS3-Cairn107-2026-10-05-usb-full.bin` | companion over USB serial; first install or recovery: `0x0` after a full erase |
|  | `MeshCore-EoRaS3-Cairn107-2026-10-05-usb-update.bin` | companion over USB serial; update: `0x10000` |
| 🧪 Elecrow ThinkNode M2 | `MeshCore-ThinkNodeM2-Cairn107-2026-10-05-ble-full.bin` | companion over Bluetooth; first install or recovery: `0x0` after a full erase |
|  | `MeshCore-ThinkNodeM2-Cairn107-2026-10-05-ble-update.bin` | companion over Bluetooth; update: `0x10000` |
|  | `MeshCore-ThinkNodeM2-Cairn107-2026-10-05-usb-full.bin` | companion over USB serial; first install or recovery: `0x0` after a full erase |
|  | `MeshCore-ThinkNodeM2-Cairn107-2026-10-05-usb-update.bin` | companion over USB serial; update: `0x10000` |
| 🧪 Heltec V3 (OLED) | `MeshCore-HeltecV3-Cairn107-2026-10-05-ble-full.bin` | companion over Bluetooth; first install or recovery: `0x0` after a full erase |
|  | `MeshCore-HeltecV3-Cairn107-2026-10-05-ble-update.bin` | companion over Bluetooth; update: `0x10000` |
|  | `MeshCore-HeltecV3-Cairn107-2026-10-05-usb-full.bin` | companion over USB serial; first install or recovery: `0x0` after a full erase |
|  | `MeshCore-HeltecV3-Cairn107-2026-10-05-usb-update.bin` | companion over USB serial; update: `0x10000` |
| 🧪 Heltec V4, standard 2 MB PSRAM (OLED) | `MeshCore-HeltecV4-Cairn107-2026-10-05-ble-full.bin` | companion over Bluetooth; first install or recovery: `0x0` after a full erase |
|  | `MeshCore-HeltecV4-Cairn107-2026-10-05-ble-update.bin` | companion over Bluetooth; update: `0x10000` |
|  | `MeshCore-HeltecV4-Cairn107-2026-10-05-usb-full.bin` | companion over USB serial; first install or recovery: `0x0` after a full erase |
|  | `MeshCore-HeltecV4-Cairn107-2026-10-05-usb-update.bin` | companion over USB serial; update: `0x10000` |
| 🧪 Heltec V4-R8, 8 MB PSRAM (OLED, no Expansion Kit) | `MeshCore-HeltecV4R8-Cairn107-2026-10-05-ble-full.bin` | companion over Bluetooth; first install or recovery: `0x0` after a full erase |
|  | `MeshCore-HeltecV4R8-Cairn107-2026-10-05-ble-update.bin` | companion over Bluetooth; update: `0x10000` |
|  | `MeshCore-HeltecV4R8-Cairn107-2026-10-05-usb-full.bin` | companion over USB serial; first install or recovery: `0x0` after a full erase |
|  | `MeshCore-HeltecV4R8-Cairn107-2026-10-05-usb-update.bin` | companion over USB serial; update: `0x10000` |
| 🧪 Heltec Wireless Tracker V1 (colour TFT) | `MeshCore-HeltecTracker-Cairn107-2026-10-05-ble-full.bin` | companion over Bluetooth; first install or recovery: `0x0` after a full erase |
|  | `MeshCore-HeltecTracker-Cairn107-2026-10-05-ble-update.bin` | companion over Bluetooth; update: `0x10000` |
|  | `MeshCore-HeltecTracker-Cairn107-2026-10-05-usb-full.bin` | companion over USB serial; first install or recovery: `0x0` after a full erase |
|  | `MeshCore-HeltecTracker-Cairn107-2026-10-05-usb-update.bin` | companion over USB serial; update: `0x10000` |
| 🧪 Heltec Wireless Tracker V2 (colour TFT) | `MeshCore-HeltecTrackerV2-Cairn107-2026-10-05-ble-full.bin` | companion over Bluetooth; first install or recovery: `0x0` after a full erase |
|  | `MeshCore-HeltecTrackerV2-Cairn107-2026-10-05-ble-update.bin` | companion over Bluetooth; update: `0x10000` |
|  | `MeshCore-HeltecTrackerV2-Cairn107-2026-10-05-usb-full.bin` | companion over USB serial; first install or recovery: `0x0` after a full erase |
|  | `MeshCore-HeltecTrackerV2-Cairn107-2026-10-05-usb-update.bin` | companion over USB serial; update: `0x10000` |
| 🧪 LilyGO T-Beam 1W | `MeshCore-TBeam1W-Cairn107-2026-10-05-ble-full.bin` | companion over Bluetooth; first install or recovery: `0x0` after a full erase |
|  | `MeshCore-TBeam1W-Cairn107-2026-10-05-ble-update.bin` | companion over Bluetooth; update: `0x10000` |
|  | `MeshCore-TBeam1W-Cairn107-2026-10-05-usb-full.bin` | companion over USB serial; first install or recovery: `0x0` after a full erase |
|  | `MeshCore-TBeam1W-Cairn107-2026-10-05-usb-update.bin` | companion over USB serial; update: `0x10000` |
| 🧪 LilyGO T-Beam Supreme (SX1262) | `MeshCore-TBeamSupreme-Cairn107-2026-10-05-ble-full.bin` | companion over Bluetooth; first install or recovery: `0x0` after a full erase |
|  | `MeshCore-TBeamSupreme-Cairn107-2026-10-05-ble-update.bin` | companion over Bluetooth; update: `0x10000` |
| 🧪 LilyGO T3S3 (SX1262) | `MeshCore-T3S3SX1262-Cairn107-2026-10-05-ble-full.bin` | companion over Bluetooth; first install or recovery: `0x0` after a full erase |
|  | `MeshCore-T3S3SX1262-Cairn107-2026-10-05-ble-update.bin` | companion over Bluetooth; update: `0x10000` |
|  | `MeshCore-T3S3SX1262-Cairn107-2026-10-05-usb-full.bin` | companion over USB serial; first install or recovery: `0x0` after a full erase |
|  | `MeshCore-T3S3SX1262-Cairn107-2026-10-05-usb-update.bin` | companion over USB serial; update: `0x10000` |
| 🧪 LilyGO T3S3 (SX1276) | `MeshCore-T3S3SX1276-Cairn107-2026-10-05-ble-full.bin` | companion over Bluetooth; first install or recovery: `0x0` after a full erase |
|  | `MeshCore-T3S3SX1276-Cairn107-2026-10-05-ble-update.bin` | companion over Bluetooth; update: `0x10000` |
|  | `MeshCore-T3S3SX1276-Cairn107-2026-10-05-usb-full.bin` | companion over USB serial; first install or recovery: `0x0` after a full erase |
|  | `MeshCore-T3S3SX1276-Cairn107-2026-10-05-usb-update.bin` | companion over USB serial; update: `0x10000` |
| 🧪 Meshnology W12 | `MeshCore-MeshnologyW12-Cairn107-2026-10-05-ble-full.bin` | companion over Bluetooth; first install or recovery: `0x0` after a full erase |
|  | `MeshCore-MeshnologyW12-Cairn107-2026-10-05-ble-update.bin` | companion over Bluetooth; update: `0x10000` |
|  | `MeshCore-MeshnologyW12-Cairn107-2026-10-05-usb-full.bin` | companion over USB serial; first install or recovery: `0x0` after a full erase |
|  | `MeshCore-MeshnologyW12-Cairn107-2026-10-05-usb-update.bin` | companion over USB serial; update: `0x10000` |
| 🧪 Seeed XIAO ESP32-S3 | `MeshCore-XiaoS3-Cairn107-2026-10-05-ble-full.bin` | companion over Bluetooth; first install or recovery: `0x0` after a full erase |
|  | `MeshCore-XiaoS3-Cairn107-2026-10-05-ble-update.bin` | companion over Bluetooth; update: `0x10000` |
|  | `MeshCore-XiaoS3-Cairn107-2026-10-05-usb-full.bin` | companion over USB serial; first install or recovery: `0x0` after a full erase |
|  | `MeshCore-XiaoS3-Cairn107-2026-10-05-usb-update.bin` | companion over USB serial; update: `0x10000` |
| 🧪 Seeed XIAO ESP32-S3 + Wio-SX1262 kit | `MeshCore-XiaoS3Wio-Cairn107-2026-10-05-ble-full.bin` | companion over Bluetooth; first install or recovery: `0x0` after a full erase |
|  | `MeshCore-XiaoS3Wio-Cairn107-2026-10-05-ble-update.bin` | companion over Bluetooth; update: `0x10000` |
|  | `MeshCore-XiaoS3Wio-Cairn107-2026-10-05-usb-full.bin` | companion over USB serial; first install or recovery: `0x0` after a full erase |
|  | `MeshCore-XiaoS3Wio-Cairn107-2026-10-05-usb-update.bin` | companion over USB serial; update: `0x10000` |
| 🧪 Station G2 (USB build only) | `MeshCore-StationG2-Cairn107-2026-10-05-usb-full.bin` | companion over USB serial; first install or recovery: `0x0` after a full erase |
|  | `MeshCore-StationG2-Cairn107-2026-10-05-usb-update.bin` | companion over USB serial; update: `0x10000` |
| 🧪 Station G3 (USB build only) | `MeshCore-StationG3-Cairn107-2026-10-05-usb-full.bin` | companion over USB serial; first install or recovery: `0x0` after a full erase |
|  | `MeshCore-StationG3-Cairn107-2026-10-05-usb-update.bin` | companion over USB serial; update: `0x10000` |
| **Original ESP32 (`-full.bin` / `-update.bin`)** | | |
| 🧪 Heltec V2 (OLED) | `MeshCore-HeltecV2-Cairn107-2026-10-05-ble-full.bin` | companion over Bluetooth; first install or recovery: `0x0` after a full erase |
|  | `MeshCore-HeltecV2-Cairn107-2026-10-05-ble-update.bin` | companion over Bluetooth; update: `0x10000` |
|  | `MeshCore-HeltecV2-Cairn107-2026-10-05-usb-full.bin` | companion over USB serial; first install or recovery: `0x0` after a full erase |
|  | `MeshCore-HeltecV2-Cairn107-2026-10-05-usb-update.bin` | companion over USB serial; update: `0x10000` |
| 🧪 LilyGO T-Beam (SX1262) | `MeshCore-TBeamSX1262-Cairn107-2026-10-05-ble-full.bin` | companion over Bluetooth; first install or recovery: `0x0` after a full erase |
|  | `MeshCore-TBeamSX1262-Cairn107-2026-10-05-ble-update.bin` | companion over Bluetooth; update: `0x10000` |
| 🧪 LilyGO T-Beam (SX1276) | `MeshCore-TBeamSX1276-Cairn107-2026-10-05-ble-full.bin` | companion over Bluetooth; first install or recovery: `0x0` after a full erase |
|  | `MeshCore-TBeamSX1276-Cairn107-2026-10-05-ble-update.bin` | companion over Bluetooth; update: `0x10000` |
| 🧪 LilyGO T-LoRa V2.1-1.6 | `MeshCore-TLoraV2116-Cairn107-2026-10-05-ble-full.bin` | companion over Bluetooth; first install or recovery: `0x0` after a full erase |
|  | `MeshCore-TLoraV2116-Cairn107-2026-10-05-ble-update.bin` | companion over Bluetooth; update: `0x10000` |
|  | `MeshCore-TLoraV2116-Cairn107-2026-10-05-usb-full.bin` | companion over USB serial; first install or recovery: `0x0` after a full erase |
|  | `MeshCore-TLoraV2116-Cairn107-2026-10-05-usb-update.bin` | companion over USB serial; update: `0x10000` |
| 🧪 MeshAdventurer (SX1262) | `MeshCore-MeshAdventurerSX1262-Cairn107-2026-10-05-ble-full.bin` | companion over Bluetooth; first install or recovery: `0x0` after a full erase |
|  | `MeshCore-MeshAdventurerSX1262-Cairn107-2026-10-05-ble-update.bin` | companion over Bluetooth; update: `0x10000` |
|  | `MeshCore-MeshAdventurerSX1262-Cairn107-2026-10-05-usb-full.bin` | companion over USB serial; first install or recovery: `0x0` after a full erase |
|  | `MeshCore-MeshAdventurerSX1262-Cairn107-2026-10-05-usb-update.bin` | companion over USB serial; update: `0x10000` |
| 🧪 MeshAdventurer (SX1268) | `MeshCore-MeshAdventurerSX1268-Cairn107-2026-10-05-ble-full.bin` | companion over Bluetooth; first install or recovery: `0x0` after a full erase |
|  | `MeshCore-MeshAdventurerSX1268-Cairn107-2026-10-05-ble-update.bin` | companion over Bluetooth; update: `0x10000` |
|  | `MeshCore-MeshAdventurerSX1268-Cairn107-2026-10-05-usb-full.bin` | companion over USB serial; first install or recovery: `0x0` after a full erase |
|  | `MeshCore-MeshAdventurerSX1268-Cairn107-2026-10-05-usb-update.bin` | companion over USB serial; update: `0x10000` |

🧪 = preview, not yet tried on hardware.

<!--
Preview envs in this build (variant dir: envs), for filling the table above:
nRF52840: rak4631, rak3401, promicro, nano_g2_ultra, heltec_t1, gat562_mesh_tracker_pro, gat562_30s_mesh_kit,
  gat562_mesh_watch13 (ble only), meshtiny, keepteen_lt1, lilygo_t_impulse_plus (ble only)
ESP32-S3: heltec_v4 (OLED), heltec_v4_r8 (OLED), heltec_v3, heltec_tracker, heltec_tracker_v2,
  lilygo_tbeam_supreme_SX1262 (ble only), lilygo_tbeam_1w, lilygo_t3s3 (sx1262), lilygo_t3s3_sx1276,
  station_g2 (usb only), station_g3_esp32 (usb only), xiao_s3, xiao_s3_wio, thinknode_m2, meshnology_w12, ebyte_eora_s3
ESP32 (original): heltec_v2, lilygo_tbeam_SX1262 (ble only), lilygo_tbeam_SX1276 (ble only),
  lilygo_tlora_v2_1, meshadventurer (sx1262 + sx1268)
-->

## Buttons

Every preview board uses the one-button interface: a **click** for the next page or row, a **hold** to open or do (from Cairn 124 the T096's simpler layout: messages, Nodes, Spectrum, GPS, then the Menu with everything you can do; see [its buttons](heltec-t096.md#buttons)). On boards with more buttons, the extra ones keep their stock MeshCore roles. Download and bootloader buttons are the board's own: see the [install guides](../install/esp32-s3.md#download-mode).

## Known issues

- Untested: screens, buttons, GPS and battery readings may be wrong on some boards.
- Station G2 / G3: USB build only. Their Bluetooth build doesn't fit the app partition.
- If a board won't boot, go back to stock MeshCore with the [official flasher](https://flasher.meshcore.co.uk) and report it.

## Reporting

[Open a bug report](https://github.com/cvhviz/CAIRN/issues/new?template=bug_report.yml) with:

- the exact file name you flashed,
- the build number from the splash,
- what worked and what didn't (screen, button, radio, GPS, Bluetooth pairing, battery),
- a serial log from boot if you can (115200 baud).

"Works fine on my board" is a useful report too: it's how a board gets promoted to ✅.

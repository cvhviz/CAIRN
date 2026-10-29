# Downloads

Every file for every board, grouped by maker. Pick your board, note its file names, and download them from the release the table names.

- **Current boards:** the **[latest release](https://github.com/cvhviz/CAIRN/releases/latest)**. This link always opens the newest Cairn release, so it never goes out of date.
- 🧪 **Preview boards:** [Cairn 107 preview](https://github.com/cvhviz/CAIRN/releases/tag/cairn-v107-preview), an older build than the current release.
- **Experimental boards:** their own pre-releases, listed on [Experimental builds](experimental.md).

Files are named `MeshCore-<Board>-Cairn<N>-<date>[-<variant>].<ext>`, so in the tables below `CairnN-<date>` stands for the release's build and date: in Cairn 123, `MeshCore-WioL2Pro-CairnN-<date>-update.bin` is `MeshCore-WioL2Pro-Cairn123-2026-10-25-update.bin`. GitHub lists a release's files alphabetically; your browser's find (Ctrl+F or ⌘F) on the board's name finds them quickly. `SHA256SUMS.txt` in each release covers every file in it.

What the file types are for:

| File | Chip | Use | Keeps your data? |
|---|---|---|---|
| `.uf2` | nRF52840 | install, update and recovery alike: double-tap Reset and copy it ([UF2 guide](install/nrf52-uf2.md)) | yes |
| `-full.bin` | ESP32 | first install or recovery, at `0x0` after a full erase ([ESP32 guide](install/esp32-s3.md)) | **no: erases everything** |
| `-update.bin` | ESP32, SF32 | update: over Wi-Fi on the boards that have it, or over USB at `0x10000` (ESP32) | yes |
| `-install.zip` | SF32 | install or update over USB with the included installer ([SF32 guide](install/sf32.md)) | yes |

Status: ✅ tested on hardware · ✅ beta: tested, new to Cairn · 🧪 preview: not yet tried on hardware.

## LilyGO

| Board | Status | File | Use |
|---|---|---|---|
| [T-Deck / T-Deck Plus](boards/lilygo-t-deck.md) | ✅ beta | `MeshCore-TDeckPlus-CairnN-<date>-full.bin` | first install or recovery, at `0x0` (erases everything, and removes an SD-card launcher) |
| | | `MeshCore-TDeckPlus-CairnN-<date>-update.bin` | update over Wi-Fi, over USB at `0x10000`, or from a launcher's SD card |
| [T-Display SF32 + keypad board](boards/lilygo-t-display-sf32.md) | ✅ | `MeshCore-TDisplaySF32-CairnN-<date>-install.zip` | install or update over USB: unzip, double-click the installer |
| | | `MeshCore-TDisplaySF32-CairnN-<date>-update.bin` (and `.sha256`) | the Wi-Fi update; the board fetches it itself |

🧪 Preview, in [Cairn 107 preview](https://github.com/cvhviz/CAIRN/releases/tag/cairn-v107-preview): T-Beam (SX1262, SX1276), T-Beam Supreme, T-Beam 1W, T3S3 (SX1262, SX1276), T-LoRa V2.1-1.6 and T-Impulse Plus. Their files are listed on [Preview boards](boards/preview-boards.md#boards-and-files).

## Seeed

| Board | Status | File | Use |
|---|---|---|---|
| [Wio Tracker L2 Pro](boards/wio-tracker-l2-pro.md) | ✅ | `MeshCore-WioL2Pro-CairnN-<date>-full.bin` | first install or recovery, at `0x0` (erases everything) |
| | | `MeshCore-WioL2Pro-CairnN-<date>-update.bin` | update over Wi-Fi, or over USB at `0x10000` |
| [Wio Tracker L1 Pro](boards/wio-tracker-l1-pro.md) | ✅ | `MeshCore-WioL1Pro-CairnN-<date>.uf2` | companion, stock SH1106 OLED (most units) |
| | | `MeshCore-DV1-CairnN-<date>.uf2` | companion, 2.42" SSD1309 OLED on the Grove port ("DV1") |
| | | `MeshCore-WioL1Eink-CairnN-<date>.uf2` | companion, 2.13" e-ink |
| | | `MeshCore-WioL1RoomServer-CairnN-<date>.uf2` | room server (no phone app; SH1106 OLED) |

- **LilyGO T-LoRa Pager:** experimental test builds only, one per radio: `MeshCore-TLoraPager-…-full.bin` (SX1262) or `MeshCore-TLoraPagerLR1121-…-full.bin`; see [Experimental builds](experimental.md).
- **SenseCAP MeshPager X2:** experimental test builds only, as `MeshCore-MeshPagerX2-…-full.bin`; see [Experimental builds](experimental.md).
- 🧪 Preview, in [Cairn 107 preview](https://github.com/cvhviz/CAIRN/releases/tag/cairn-v107-preview): XIAO ESP32-S3, and the XIAO ESP32-S3 + Wio-SX1262 kit.

## Heltec

| Board | Status | File | Use |
|---|---|---|---|
| [V4-R8 + Expansion Kit V2 (touch)](boards/heltec-v4-touch.md) | ✅ | `MeshCore-HeltecV4Touch-CairnN-<date>-full.bin` | first install or recovery, at `0x0` (erases everything) |
| | | `MeshCore-HeltecV4Touch-CairnN-<date>-update.bin` | update over Wi-Fi, or over USB at `0x10000` |
| [V4 + Expansion Kit V1 (touch)](boards/heltec-v4-kit-v1.md) | 🧪 | `MeshCore-HeltecV4KitV1-CairnN-<date>-full.bin` | first install or recovery, at `0x0` (erases everything) |
| | | `MeshCore-HeltecV4KitV1-CairnN-<date>-update.bin` | update over Wi-Fi, or over USB at `0x10000` |
| [Mesh Node T096](boards/heltec-t096.md) | ✅ | `MeshCore-HeltecT096-CairnN-<date>-ble.uf2` | companion over Bluetooth (the main build) |
| | | `MeshCore-HeltecT096-CairnN-<date>-usb.uf2` | companion over USB serial (no Bluetooth, no GPS page) |
| [Mesh Node T096 repeater](boards/compact-repeater.md) | ✅ beta | `MeshCore-HeltecT096-CairnN-<date>-repeater.uf2` | compact repeater |
| [T114 repeater](boards/compact-repeater.md) | 🧪 | `MeshCore-HeltecT114-CairnN-<date>-repeater.uf2` | compact repeater |
| [WiFi LoRa 32 V2 repeater](boards/compact-repeater.md) | 🧪 | `MeshCore-HeltecV2-CairnN-<date>-repeater-full.bin` / `-repeater-update.bin` | compact repeater: first install at `0x0` / update at `0x10000` |
| [WiFi LoRa 32 V3 repeater](boards/compact-repeater.md) | 🧪 | `MeshCore-HeltecV3-CairnN-<date>-repeater-full.bin` / `-repeater-update.bin` | compact repeater |
| [WiFi LoRa 32 V4 repeater](boards/compact-repeater.md) | 🧪 | `MeshCore-HeltecV4-CairnN-<date>-repeater-full.bin` / `-repeater-update.bin` | compact repeater |
| [V4-R8 repeater](boards/compact-repeater.md) | 🧪 | `MeshCore-HeltecV4R8-CairnN-<date>-repeater-full.bin` / `-repeater-update.bin` | compact repeater |
| [Wireless Tracker V1 repeater](boards/compact-repeater.md) | 🧪 | `MeshCore-HeltecTracker-CairnN-<date>-repeater-full.bin` / `-repeater-update.bin` | compact repeater |
| [Wireless Tracker V2 repeater](boards/compact-repeater.md) | 🧪 | `MeshCore-HeltecTrackerV2-CairnN-<date>-repeater-full.bin` / `-repeater-update.bin` | compact repeater |

- **Which V4?** `esptool chip-id` reports *Embedded PSRAM 8MB* on a V4-R8 and *2MB* on a standard V4. The Kit V2 touch build needs the V4-R8; on a standard V4 it boot-loops ([details](boards/heltec-v4-touch.md)).
- 🧪 Preview companions, in [Cairn 107 preview](https://github.com/cvhviz/CAIRN/releases/tag/cairn-v107-preview): V2, V3, V4 and V4-R8 with their OLED, Wireless Tracker V1 and V2, and T1. Their files have `-ble` or `-usb` in the name, where the repeaters above have `-repeater`.

## Elecrow ThinkNode

| Board | Status | File | Use |
|---|---|---|---|
| [ThinkNode M9](boards/thinknode-m9.md) | ✅ beta | `MeshCore-ThinkNodeM9-CairnN-<date>-full.bin` | first install or recovery, at `0x0` (erases everything); also the way in from Elecrow's firmware, Meshtastic or stock MeshCore |
| | | `MeshCore-ThinkNodeM9-CairnN-<date>-update.bin` | update over Wi-Fi, or over USB at `0x10000` |

🧪 Preview, in [Cairn 107 preview](https://github.com/cvhviz/CAIRN/releases/tag/cairn-v107-preview): ThinkNode M2.

## Other boards (🧪 preview)

All in [Cairn 107 preview](https://github.com/cvhviz/CAIRN/releases/tag/cairn-v107-preview), with each file listed on [Preview boards](boards/preview-boards.md#boards-and-files):

- **nRF52840 (`.uf2`):** RAK4631, RAK3401, ProMicro, B&Q Nano G2 Ultra, GAT562 30S Mesh Kit, GAT562 Mesh Tracker Pro, GAT562 Mesh Watch13, Meshtiny, Keepteen LT1.
- **ESP32-S3 (`.bin`):** Station G2 and G3 (USB build only), Meshnology W12, Ebyte EoRa-S3.
- **Original ESP32 (`.bin`):** MeshAdventurer (SX1262, SX1268).

## Older and test builds

- Earlier Cairn releases: [all releases](https://github.com/cvhviz/CAIRN/releases). Each one's notes list its files.
- Experimental builds: [Experimental builds](experimental.md) · [all experimental releases](https://github.com/cvhviz/CAIRN/releases?q=experimental&expanded=true).
- Wio Tracker L1 Pro builds 40 to 98, from before Cairn: [archived builds](https://github.com/cvhviz/CAIRN/releases?q=cvhbuild&expanded=true).

Back to the [README](../README.md).

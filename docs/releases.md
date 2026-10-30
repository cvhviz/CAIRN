# Release format

How Cairn releases are tagged and named. Devices that update over Wi-Fi depend on it, so it is written down here for anyone publishing a build (and for the curious). To download a build, see the [downloads page](downloads.md).

## Tags

| Tag | What it is | Release type |
|---|---|---|
| `cairn-vN` | a Cairn release; N is the build number on the splash | normal release; the newest is **Latest** |
| `cairn-v107-preview` | the 🧪 [preview boards](boards/preview-boards.md), built from Cairn 107 | pre-release |
| `experimental-<board>-<N>[-<test>]` | a one-off [experimental build](experimental.md) | pre-release, never Latest |
| `cvhbuild-v*` (and `cvhbuild-47`) | Wio Tracker L1 Pro builds 40 to 98, from before Cairn | pre-release, archived |

## File names

```
MeshCore-<Board>-Cairn<N>-<YYYY-MM-DD>[-<variant>].<ext>
```

- `<Board>` names one board and one build, for example `WioL2Pro`, `HeltecV4Touch`, `TDisplaySF32`.
- `<variant>` is `ble` or `usb` (which link the companion uses), `repeater`, or empty; ESP32 files then end in `-full.bin` or `-update.bin`.
- `SHA256SUMS.txt` lists every file in the release.

## For the online updater

The L2 Pro, Heltec V4 touch (Kit V2 and Kit V1), ThinkNode M9, T-Deck, T-LoRa Pager and T-Display SF32 builds read `https://api.github.com/repos/cvhviz/Cairn/releases/latest`. For a build to be offered:

- Tag it `cairn-vN`, where N is the build number shown on the splash (it must be higher than the device's own). Publish it as a normal release, not a draft or pre-release.
- [Experimental builds](experimental.md) are the opposite: always a pre-release, never marked latest, so no device is offered one.
- Attach each board's `-update.bin` under its exact name, with nothing between the date and `-update.bin`. The SF32 also accepts a `.sha256` file next to its update.
- GitHub records each file's SHA-256, which the device checks, along with the size and the board's OTA marker inside the image.
- No other asset may start with one of these board prefixes and end in `-update.bin`. Preview boards use their own board names.
- The release notes are shown on the device before installing, so keep the top of them short and plain.

| Board | Update file |
|---|---|
| Seeed Wio Tracker L2 Pro | `MeshCore-WioL2Pro-CairnN-YYYY-MM-DD-update.bin` |
| Heltec V4-R8 + Expansion Kit V2 (touch) | `MeshCore-HeltecV4Touch-CairnN-YYYY-MM-DD-update.bin` |
| Heltec V4 + Expansion Kit V1 (touch), untested preview | `MeshCore-HeltecV4KitV1-CairnN-YYYY-MM-DD-update.bin` |
| Elecrow ThinkNode M9 | `MeshCore-ThinkNodeM9-CairnN-YYYY-MM-DD-update.bin` |
| LilyGO T-Deck / T-Deck Plus | `MeshCore-TDeckPlus-CairnN-YYYY-MM-DD-update.bin` |
| LilyGO T-LoRa Pager (SX1262) | `MeshCore-TLoraPager-CairnN-YYYY-MM-DD-update.bin` |
| LilyGO T-LoRa Pager (LR1121) | `MeshCore-TLoraPagerLR1121-CairnN-YYYY-MM-DD-update.bin` |
| LilyGO T-Display SF32 | `MeshCore-TDisplaySF32-CairnN-YYYY-MM-DD-update.bin` |

Back to the [README](../README.md).

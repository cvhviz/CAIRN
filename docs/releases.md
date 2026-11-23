# Release format

How Cairn releases are tagged and named. Devices that update over Wi-Fi depend on it, so it is written down here for anyone publishing a build (and for the curious). To download a build, see the [downloads page](downloads.md).

## Tags

| Tag | What it is | Release type |
|---|---|---|
| `cairn-vN` | a Cairn release; N is the build number on the splash | normal release; the newest is **Latest** |
| `cairn-vN` (beta) | the same build offered early to radios with **Beta updates** on | pre-release, never Latest, until promoted |
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

## Beta releases

A beta is an ordinary build published early as a pre-release. Radios with **Settings › Firmware update › Beta updates** on (and the app's Firmware Update page, which follows the radio's setting) read `https://api.github.com/repos/cvhviz/Cairn/releases?per_page=8` (the app reads 10) and take the highest `cairn-vN` that has their board's file, pre-release or not. Radios with it off still read only `releases/latest`, which never returns a pre-release, so a beta never reaches them.

- Build and name it exactly as a stable release: tag `cairn-vN`, files `MeshCore-<Board>-CairnN-<date>-update.bin`, `CVH_BUILD_NAME "Cairn N"`. Not `Cairn Nbeta`: a beta's number is its release number, so promoting it needs no rebuild.
- Publish it as a pre-release, never Latest, with `SHA256SUMS.txt` (the app needs it):

  ```
  gh release create cairn-vN -R cvhviz/Cairn --target main --title "Cairn N beta" --prerelease --latest=false \
    --notes-file "Releases and Promo/Firmware releases/cairn-vN/release-notes.md" MeshCore-* SHA256SUMS.txt
  ```

- Check that stable radios still see the previous release: `gh api repos/cvhviz/Cairn/releases/latest --jq .tag_name`.
- Promote it to stable when it's ready (same tag, same files):

  ```
  gh release edit cairn-vN -R cvhviz/Cairn --prerelease=false --latest --title "Cairn N"
  ```

- A fix during the beta is the next number (`cairn-vN+1`), again as a pre-release. Never replace a beta's files under the same tag: radios compare build numbers, not file contents.
- Keep the newest stable release within the last 8 releases (counting betas and experimental builds), or a beta radio's list may not reach it.
- Turning Beta updates off on a radio running a beta offers nothing older: it keeps the beta until a stable release with a higher number is published (or the beta is promoted).

| Board | Update file |
|---|---|
| Seeed Wio Tracker L2 Pro | `MeshCore-WioL2Pro-CairnN-YYYY-MM-DD-update.bin` |
| Heltec V4-R8 + Expansion Kit V2 (touch) | `MeshCore-HeltecV4Touch-CairnN-YYYY-MM-DD-update.bin` |
| Heltec V4 + Expansion Kit V1 (touch), in the normal release again from Cairn 130 (experimental for 127 to 129) | `MeshCore-HeltecV4KitV1-CairnN-YYYY-MM-DD-update.bin` |
| Elecrow ThinkNode M9 | `MeshCore-ThinkNodeM9-CairnN-YYYY-MM-DD-update.bin` |
| Elecrow ThinkNode M9, USB companion | `MeshCore-ThinkNodeM9USB-CairnN-YYYY-MM-DD-update.bin` |
| LilyGO T-Deck / T-Deck Plus | `MeshCore-TDeckPlus-CairnN-YYYY-MM-DD-update.bin` |
| LilyGO T-LoRa Pager (SX1262) | `MeshCore-TLoraPager-CairnN-YYYY-MM-DD-update.bin` |
| LilyGO T-LoRa Pager (LR1121) | `MeshCore-TLoraPagerLR1121-CairnN-YYYY-MM-DD-update.bin` |
| LilyGO T-Display SF32 | `MeshCore-TDisplaySF32-CairnN-YYYY-MM-DD-update.bin` |

The one-button ESP32 companions in the release from Cairn 131, the Heltec Wireless Tracker V2 (`MeshCore-HeltecTrackerV2-CairnN-YYYY-MM-DD-ble-update.bin`) and the V4-R8 with its OLED (`MeshCore-HeltecV4R8-CairnN-YYYY-MM-DD-ble-update.bin`), have Wi-Fi for the app but don't update over it: the `-ble` between the date and `-update.bin` keeps them apart from the names above. The ThinkNode M9 USB companion is a board of its own from Cairn 139, packaged as `MeshCore-ThinkNodeM9USB-…` files: its build looks for `MeshCore-ThinkNodeM9USB-CairnN-YYYY-MM-DD-update.bin`, so its online update keeps it on USB, and the CairnOS app installs that file when its Firmware Update page's Build is set to USB cable (the radio can't tell the app which build it runs). Its earlier files, `MeshCore-ThinkNodeM9-CairnN-YYYY-MM-DD-usb-full.bin` / `-usb-update.bin` (the experimental build from Cairn 131, then the releases from 136 to 138), carry the Bluetooth M9's update name: their online update installs the normal (Bluetooth) M9 build. Never publish that `-usb-` pair beside the new one.

Back to the [README](../README.md).

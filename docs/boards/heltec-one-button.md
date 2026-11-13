# Heltec Wireless Tracker V2 and WiFi LoRa 32 V4-R8 (OLED) companions

✅ Beta: tested on hardware, new to Cairn · ESP32-S3 · [install with esptool or the web flasher](../install/esp32-s3.md) · the app over Bluetooth or Wi-Fi; updates over USB

From Cairn 131 these two boards have a Cairn companion in the normal release, next to their [compact repeater](compact-repeater.md). Both run the one-button interface from the [Heltec T096](heltec-t096.md): Home dashboard, Messages, Nodes, Spectrum, GPS and the Menu with its Settings.

| Board | Screen | Notes |
|---|---|---|
| Heltec Wireless Tracker V2 | 0.96" 160×80 color TFT | built-in GPS; the T096's five themes (Menu › Settings › Theme). No PSRAM, so it keeps 200 contacts |
| Heltec WiFi LoRa 32 V4-R8, OLED only (no Expansion Kit) | 0.96" 128×64 OLED, white on black | GPS with the Heltec GPS module fitted; 350 contacts, the mesh kept in the R8's PSRAM |

The V4-R8 with the Expansion Kit V2 touchscreen has its own build: [Heltec V4 touch](heltec-v4-touch.md). A plain V4 (2 MB PSRAM) with only the OLED is still a 🧪 [preview board](preview-boards.md).

## Which file

Download from the [latest release](https://github.com/cvhviz/CAIRN/releases/latest) · [every board's files](../downloads.md)

| Board | File | Use |
|---|---|---|
| Wireless Tracker V2 | `MeshCore-HeltecTrackerV2-CairnN-<date>-ble-full.bin` | first install or recovery, at `0x0` after an erase (erases everything) |
| | `MeshCore-HeltecTrackerV2-CairnN-<date>-ble-update.bin` | update over USB at `0x10000` (keeps your data) |
| V4-R8 (OLED) | `MeshCore-HeltecV4R8-CairnN-<date>-ble-full.bin` | first install or recovery, at `0x0` after an erase (erases everything) |
| | `MeshCore-HeltecV4R8-CairnN-<date>-ble-update.bin` | update over USB at `0x10000` (keeps your data) |

Files with `-repeater` in the name are the compact repeater, not the companion. These builds don't update themselves over Wi-Fi: write the next `-ble-update.bin` over USB.

## Buttons

One button, as on the T096: a **click** moves on, a **hold** opens or does. See the [T096 page](heltec-t096.md#buttons).

## Wi-Fi

The app connects over Bluetooth or over Wi-Fi (TCP port 5000), whichever it finds; both can be up at once.

- **Menu › Wi-Fi:** with no network set yet, a hold opens Wi-Fi setup. After that, a hold turns Wi-Fi off or on (it asks first: the radio restarts).
- **Menu › Settings › Wi-Fi setup:** the radio puts up its own network ("Cairn-xxxx", with the password on its screen). Join it from a phone, and the setup page lists the networks the radio can see; pick one and save, and the radio restarts onto it.
- **Home's bottom line** shows the radio's address once it has joined.
- From the app's command line: `set wifi.ssid` and `set wifi.pwd`.

## From Cairn 132

Files: `MeshCore-HeltecTrackerV2-Cairn132-2026-11-12-ble-full.bin` and `-ble-update.bin`; `MeshCore-HeltecV4R8-Cairn132-2026-11-12-ble-full.bin` and `-ble-update.bin`.

- **V4-R8: no more boot loop.** After a soft reset the interface could read leftover memory and crash on every start.
- **No more power-off on USB with a low battery** (both boards). The board now knows when it is plugged in, and powers off only when the cell is low and not rising for 5 minutes.
- Both fixes were already in the Cairn 131 files, which were replaced on 12 Nov 2026 (run on the bench).

## From Cairn 131

Files: `MeshCore-HeltecTrackerV2-Cairn131-2026-11-11-ble-full.bin` and `-ble-update.bin`; `MeshCore-HeltecV4R8-Cairn131-2026-11-11-ble-full.bin` and `-ble-update.bin`.

- First release build for both (the Cairn 107 preview had untested images). Run on both boards on the bench: the screen, the button, the app over Bluetooth, Wi-Fi setup, joining a network and the app over Wi-Fi, and on the V4-R8 the Heltec GPS module.
- The 12h / 24h clock (Menu › Settings › Clock) and the rest of the T096's Cairn 131 interface.
- **Wireless Tracker V2 memory:** with no PSRAM, the mesh, Bluetooth and Wi-Fi share the internal RAM, so it keeps 200 contacts, 64 messages waiting for the phone and a 4 KB packet log (33-35 KB free with both radios up).

# Heltec WiFi LoRa 32 V4 + Expansion Kit V1 (touch)

✅ Tested · ESP32-S3 · [install with esptool or the web flasher](../install/esp32-s3.md) · updates over Wi-Fi

The plain Heltec V4 (ESP32-S3, 16 MB flash, 2 MB quad PSRAM; SX1262 with a GC1109 front end on a V4.2 or a KCT8103L on a V4.3) in Heltec's Expansion Kit V1 case, with a 2.8" 240×320 ST7789 touchscreen and a piezo. From Cairn 121 it runs the same touch interface as the [Expansion Kit V2 build](heltec-v4-touch.md), without the map.

**Nobody here has a V1 kit, so this build has not run on a device yet.** Its pins come from Heltec's datasheet, Meshtastic's and upstream MeshCore's files, none measured on a unit. If you have one, please try it and [report](https://github.com/cvhviz/CAIRN/issues/new?template=bug_report.yml) what works and what doesn't, even "it works".

**This build is for a standard V4** (`esptool chip-id` reports *Embedded PSRAM 2MB*) **in the Expansion Kit V1**. A V4-R8 (*8MB*) in the Expansion Kit V2 needs the [Heltec V4 touch build](heltec-v4-touch.md). The two images carry different firmware markers and refuse each other over Wi-Fi.

## Which file

Download from the [latest release](https://github.com/cvhviz/CAIRN/releases/latest) · [every board's files](../downloads.md)

| You want to… | File | How |
|---|---|---|
| install Cairn for the first time | `MeshCore-HeltecV4KitV1-CairnN-<date>-full.bin` | full erase, then write at `0x0`. **Erases everything**: export your key and contacts in the app first. |
| update | `MeshCore-HeltecV4KitV1-CairnN-<date>-update.bin` | online (Settings › System › Firmware update), a browser upload in Wi-Fi transfer, or USB at `0x10000` |
| recover a device that won't boot | `MeshCore-HeltecV4KitV1-CairnN-<date>-full.bin` | full erase, then write at `0x0` |

Every release from Cairn 121 on carries both files. Write the `-full.bin` or the `-update.bin`, never both. Download mode: hold **PRG**, tap **RST**, release **PRG**.

## Buttons

| Button | Does |
|---|---|
| PRG (USER) | click: quick panel; double-press: new message (unlocks instead when the device is locked); hold: lock now. It wakes the board from hibernate. |
| RST | restart |

PRG is the only button this build uses. Heltec's datasheet shows a second case button on GPIO 35, the same pin as the white TX LED; until someone checks how the two are wired, it is left out.

## Against the Expansion Kit V2 build

- **No map, card storage or map downloads.** No microSD is known on this kit, and its 2 MB of PSRAM could not hold the map cache anyway. Settings › Map and Storage show them as not available; the Online map, Map cache and Screenshot are left out.
- **PRG only** (see above).
- **TX power** stops at 18 (was 22), and from Cairn 122 the screens show the power at the antenna, from the GC1109 or KCT8103L curve picked at boot.
- **FEM LNA:** on a V4.3 (KCT8103L) the tile works; on a V4.2 (GC1109, no LNA switch) it reads "Not on this radio". Boosted RX stays on both.
- The Spectrum page, chats, nodes, repeater admin, Wi-Fi with online updates, the Wi-Fi and Bluetooth scanners, the Battery page, Battery saver and portrait mode (the Quick panel's Rotate) are as on the [Kit V2 build](heltec-v4-touch.md#features).

## From Cairn 133

Files: `MeshCore-HeltecV4KitV1-Cairn133-2026-11-13-full.bin` and `-update.bin`.

- **Sharper text:** the upright strokes of letters like m, n, l, 1 and H now land on whole pixels instead of smearing across two. **Chat text is one size larger** (14 px, or 12 px with Display › Text size Small).
- **Wallpaper** (Settings › Appearance › Wallpaper): a photo from the card's `/Photos`, one of four built-in pictures (Cairn, Alpine, Aurora, Mesh), one of eight gradients or one of eight colors, behind Home (under the status bar and the side rail too), the lock screen and the Ambient screensaver. The cards over it turn to frosted glass. Only a photo needs the card. A picture opened from Files has a **Set as wallpaper** button.
- **Wi-Fi scan:** each network has its own color, and networks that overlap never share one. Each is drawn in the real 802.11 channel shape, so a strong network's spill into its neighbors shows. **Tap a network** to pick it out: the others dim, and the readout shows its name, signal, channel, security, width and BSSID; tap the readout for its Details. Each list row has a stripe in its plot color.
- **Walkie**, a new alert tone: a push-to-talk chirp, in every tone picker.

## From Cairn 132

Files: `MeshCore-HeltecV4KitV1-Cairn132-2026-11-12-full.bin` and `-update.bin`.

- **Wi-Fi scan:** each network is drawn flat across the channels it covers and drops straight to the floor at the channel edge, and a 40 MHz network's name is followed by "40 MHz".
- **Spectrum › Channel draws like the Band scan:** a filled trace colored by level (teal, amber, red) with the average as a white line, and a heat map in the Band waterfall's colors.
- **Emoji taps land** on the keyboard's emoji panel even when the finger drifts a little while pressing.
- **No hint text** in an empty message field.
- **Less lag when adverts and messages arrive:** saves to flash (chat history, the offline queue, contacts, stored adverts) wait for the screen to go dark, for at most 3 minutes.

Not yet checked on a device.

## From Cairn 131

Files: `MeshCore-HeltecV4KitV1-Cairn131-2026-11-11-full.bin` and `-update.bin`. **Every time zone shows** in Settings › Clock › Time zone: the list stopped after the first four of Europe & Africa ([#50](https://github.com/cvhviz/CAIRN/issues/50), [#38](https://github.com/cvhviz/CAIRN/issues/38)).

## From Cairn 130

The Kit V1 build is in the normal release again (`MeshCore-HeltecV4KitV1-Cairn130-2026-11-10-full.bin` and `-update.bin`), so a kit's online update (Settings › System › Firmware update) finds it. It has everything in Cairn 130: with a full contact list a save writes only the contacts that changed, and no longer holds the screen after an advert.

## From Cairn 127

For Cairn 127 to 129 the Kit V1 build was an [experimental pre-release](https://github.com/cvhviz/CAIRN/releases/tag/experimental-heltec-kitv1-127) (`MeshCore-HeltecV4KitV1-Cairn127-2026-11-03-full.bin`), out of the normal release until a kit confirms the blank-screen fix: the kit's power switch (GPIO 36) held as Meshtastic and MeshCore hold it. A kit's online update does not offer it; flash it by hand. It has everything else in Cairn 127.

## From Cairn 125

Files: `MeshCore-HeltecV4KitV1-Cairn125-2026-10-29-full.bin` and `-update.bin`.

- **The 2 MB PSRAM is used from start-up:** the mesh and the interface (about 140 KB) were put in internal memory, because this kit's kind of PSRAM came up only after they were made. They now go into PSRAM, as on the Kit V2, leaving that much more internal memory for Wi-Fi, maps and the card. The same fix was checked on a T-LoRa Pager; not yet on a Kit V1.

## From Cairn 123

- No more **"Watchdog (stall)" restarts from a full node list**: with the list at or near its 350-node limit, saving it to flash could take long enough that the watchdog restarted the device. The save now checks in with the watchdog as it goes. Not yet checked on a device.

## From Cairn 122

- **RX sync and queue sync** (with CairnOS build 18 or later): the app catches up on what the radio heard during a dropped link, as far back as its journal reaches, and a message stays queued on the radio until the app has stored it; anything the radio had to drop is counted in the app. The official MeshCore apps get the same frames as before. Going back to Cairn 121 loses the messages waiting on the radio.
- **Radio settings over Wi-Fi** from a phone on the Trusted devices list ("Always allow"); command-line text over Wi-Fi is now limited like the other commands, so the app's Reboot, Power off, Set PIN and Wi-Fi commands work over Bluetooth only.
- **Every radio preset the app offers** on the Radio page's preset picker: all 28, with their frequency and area, grouped by region with the one the device is in first; a preset with a path hash sets it too, and the device remembers which preset you picked. The summary card on top of the Radio page shows the path hash next to the TX power, and its tile moved ahead of TX power.
- **The position set from the app** shows in GPS data and on Home's GPS card while the GPS is off.
- **TX power at the antenna** on the screens; the setting stops at 18 (a saved value above it is lowered at boot, with the same output).
- A radio change no longer leaves the node deaf until it next sends, and a failed online install says why.
- **Not yet checked on a device:** nothing new in 122 has run on hardware yet; it builds and passes the firmware's automated tests. This whole build is still an untested preview.

Problems? [Report a bug](https://github.com/cvhviz/CAIRN/issues/new?template=bug_report.yml). Please include the build number from the splash screen and, if you can, a serial log of the first boot.

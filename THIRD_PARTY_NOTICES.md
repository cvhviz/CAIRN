# Third-party notices

The Cairn firmware (the builds for the Wio Tracker L2 Pro, Heltec V4 touch, ThinkNode M9, T-Deck and T-Display SF32 in particular) includes the following third-party works. Their full licence texts are in [`licenses/`](licenses/).

| Work | Used for | Licence | Text |
|---|---|---|---|
| [MeshCore](https://github.com/meshcore-dev/MeshCore), © Scott Powell / rippleradios.com | Mesh, radio and companion firmware | MIT | [MeshCore-license.txt](licenses/MeshCore-license.txt) |
| [Montserrat](https://github.com/JulietaUla/Montserrat), © The Montserrat Project Authors | Interface typeface, embedded as anti-aliased bitmap fonts | SIL Open Font License 1.1 | [Montserrat-OFL.txt](licenses/Montserrat-OFL.txt) |
| [Noto Emoji](https://github.com/googlefonts/noto-emoji), © Google LLC | Colour emoji, embedded as downscaled bitmaps | SIL Open Font License 1.1 (the repository's README also lists Apache 2.0 for image resources) | [NotoEmoji-LICENSE.txt](licenses/NotoEmoji-LICENSE.txt) |
| [region-flags](https://github.com/googlefonts/noto-emoji/tree/main/third_party/region-flags), via Noto Emoji | The 🇺🇸 flag | Public domain or exempt from copyright | [region-flags-LICENSE.txt](licenses/region-flags-LICENSE.txt) |
| [LovyanGFX](https://github.com/lovyan03/LovyanGFX), © lovyan03 and contributors | Display and touch driver | FreeBSD | [LovyanGFX-license.txt](licenses/LovyanGFX-license.txt) |
| [QRCode](https://github.com/ricmoo/QRCode), © 2017 Richard Moore | The contact QR code (from Cairn 111) | MIT | [QRCode-LICENSE.txt](licenses/QRCode-LICENSE.txt) |

The LilyGO T-Display SF32 build and its installer also include:

| Work | Used for | Licence | Text |
|---|---|---|---|
| [SiFli SDK](https://github.com/OpenSiFli/SiFli-SDK), © SiFli Technologies | SF32 drivers, Bluetooth stack, bootloader (with Cairn's update-slot changes) | Apache 2.0 | [SiFli-SDK-LICENSE.txt](licenses/SiFli-SDK-LICENSE.txt) |
| [RT-Thread](https://github.com/RT-Thread/rt-thread), © RT-Thread Development Team | Real-time operating system | Apache 2.0 | [RT-Thread-LICENSE.txt](licenses/RT-Thread-LICENSE.txt) |
| [LVGL](https://github.com/lvgl/lvgl), © LVGL Kft | Graphics library for the SF32 interface | MIT | [LVGL-LICENSE.txt](licenses/LVGL-LICENSE.txt) |
| [Font Awesome Free 5](https://github.com/FortAwesome/Font-Awesome), © Fonticons, Inc., via LVGL | Some interface symbols | Icons CC BY 4.0, font SIL OFL 1.1 | [FontAwesome-LICENSE.txt](licenses/FontAwesome-LICENSE.txt) |
| [DejaVu Sans](https://github.com/dejavu-fonts/dejavu-fonts), © Bitstream, DejaVu changes public domain | Extra glyphs in the SF32 fonts | Bitstream Vera licence | [DejaVu-LICENSE.txt](licenses/DejaVu-LICENSE.txt) |
| [sftool](https://github.com/OpenSiFli/sftool), © OpenSiFli | The flashing tool bundled, unchanged, in the SF32 `-install.zip` | Apache 2.0 | [sftool-LICENSE.txt](licenses/sftool-LICENSE.txt) |
| [pyserial](https://github.com/pyserial/pyserial) 3.5, © Chris Liechti | Serial-port access for the installer's helper, bundled unchanged in the SF32 `-install.zip` | BSD 3-Clause | [pyserial-LICENSE.txt](licenses/pyserial-LICENSE.txt) |

The SenseCAP MeshPager X2 build (experimental) also includes:

| Work | Used for | Licence | Text |
|---|---|---|---|
| [BMM350 SensorAPI](https://github.com/boschsensortec/BMM350_SensorAPI) v1.10.0, © 2024 Bosch Sensortec GmbH | The compass (BMM350 magnetometer driver), unmodified | BSD 3-Clause | [BMM350-SensorAPI-LICENSE.txt](licenses/BMM350-SensorAPI-LICENSE.txt) |

The [Cairn firmware manual](docs/Cairn_Firmware_Manual_Dark) (its web version and PDF) also includes:

| Work | Used for | Licence | Text |
|---|---|---|---|
| [Inter and Inter Tight](https://github.com/rsms/inter), © The Inter Project Authors | Body and heading typefaces, bundled in `docs/Cairn_Firmware_Manual_Dark/fonts/` and embedded in the PDF | SIL Open Font License 1.1 | [Inter-OFL.txt](licenses/Inter-OFL.txt) |
| [JetBrains Mono](https://github.com/JetBrains/JetBrainsMono), © The JetBrains Mono Project Authors | Labels and key names, bundled and embedded the same way | SIL Open Font License 1.1 | [JetBrainsMono-OFL.txt](licenses/JetBrainsMono-OFL.txt) |

Other libraries (RadioLib, the Arduino ESP32 core, ESP-IDF and the audio driver) are linked unmodified under their own permissive licences; see each project's repository.

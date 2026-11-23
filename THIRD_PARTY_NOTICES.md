# Third-party notices

This page lists the third-party works in the current Cairn firmware images (Cairn releases after 138), in the Cairn installers and in the Cairn manual. The full license texts are in [`licenses/`](licenses/). Works are linked unmodified unless the row says otherwise.

Cairn releases up to and including 138 also contained some works that later releases no longer use; see [Earlier releases](#earlier-releases) at the end.

## Most builds

| Work | Used for | License | Text |
|---|---|---|---|
| [MeshCore](https://github.com/meshcore-dev/MeshCore), © Scott Powell / rippleradios.com | Mesh, radio and companion firmware | MIT | [MeshCore-license.txt](licenses/MeshCore-license.txt) |
| [Montserrat](https://github.com/JulietaUla/Montserrat), © 2011 The Montserrat Project Authors | Interface typeface. It is embedded as anti-aliased bitmap fonts in the touch and SF32 interfaces. In releases after Cairn 138 it is also embedded as Cairn's 1-bit CairnSans / CairnClock bitmap fonts, which are a Modified Version under the OFL, on the Heltec T114 and Wio Tracker L1 E-ink, and on the experimental e-paper builds for the Heltec MeshPocket, ThinkNode M1 and M8, and LilyGO T-Echo and T-Echo Lite (from Cairn 139) | SIL Open Font License 1.1 | [Montserrat-OFL.txt](licenses/Montserrat-OFL.txt) |
| [RadioLib](https://github.com/jgromes/RadioLib) 7.8.1, © Jan Gromeš | LoRa radio drivers | MIT | [RadioLib-license.txt](licenses/RadioLib-license.txt) |
| [Crypto](https://github.com/rweather/arduinolibs), © Southern Storm Software, Pty Ltd. | AES, SHA and other primitives | MIT | [Crypto-LICENSE.txt](licenses/Crypto-LICENSE.txt) |
| [ed25519](https://github.com/orlp/ed25519), © 2015 Orson Peters | Signatures and key exchange | zlib | [ed25519-LICENSE.txt](licenses/ed25519-LICENSE.txt) |
| [CayenneLPP](https://github.com/ElectronicCats/CayenneLPP) 1.6.1, by Electronic Cats | Telemetry encoding | MIT | [CayenneLPP-LICENSE.md](licenses/CayenneLPP-LICENSE.md) |
| [RTClib](https://github.com/adafruit/RTClib) 2.1.4, © Adafruit Industries | Clock helpers | MIT | [RTClib-license.txt](licenses/RTClib-license.txt) |
| [Melopero RV3028](https://github.com/melopero/Melopero_RV-3028_Arduino_Library) 1.2.0, © Melopero | External real-time clock driver | MIT | [Melopero-RV3028-LICENSE.txt](licenses/Melopero-RV3028-LICENSE.txt) |
| [Adafruit BusIO](https://github.com/adafruit/Adafruit_BusIO) 1.17.4, © Adafruit Industries | I²C/SPI helpers used by the sensor and display drivers | MIT | [Adafruit-BusIO-LICENSE.txt](licenses/Adafruit-BusIO-LICENSE.txt) |
| [base64](https://github.com/Densaugeo/base64_arduino) 1.4.0, © Densaugeo | Base64 encoding | MIT | [base64-LICENSE.txt](licenses/base64-LICENSE.txt) |

## Builds with the touch (L2-style) interface

These are the Wio Tracker L2 Pro, Heltec V4 touch and V4 kit v1 touch, ThinkNode M9, T-Deck Plus and T-LoRa Pager builds. The T-Display SF32 also uses the Noto Emoji, region-flags and minimp3 rows.

| Work | Used for | License | Text |
|---|---|---|---|
| [LovyanGFX](https://github.com/lovyan03/LovyanGFX) 1.2.30, © lovyan03 and contributors | Display and touch driver | FreeBSD (with MIT parts) | [LovyanGFX-license.txt](licenses/LovyanGFX-license.txt) |
| [Noto Emoji](https://github.com/googlefonts/noto-emoji), © Google LLC | Color emoji, embedded as downscaled bitmaps | SIL Open Font License 1.1 (the repository's README also lists Apache 2.0 for image resources) | [NotoEmoji-LICENSE.txt](licenses/NotoEmoji-LICENSE.txt) |
| [region-flags](https://github.com/googlefonts/noto-emoji/tree/main/third_party/region-flags), via Noto Emoji | The 🇺🇸 flag | Public domain or exempt from copyright | [region-flags-LICENSE.txt](licenses/region-flags-LICENSE.txt) |
| [QRCode](https://github.com/ricmoo/QRCode), © 2017 Richard Moore | The contact QR code (from Cairn 111) | MIT | [QRCode-LICENSE.txt](licenses/QRCode-LICENSE.txt) |
| [minimp3](https://github.com/lieff/minimp3) (commit ea99364), by lieff | MP3 decoding in the media player. Cairn's copy has one small patch that moves the decoder's scratch memory off the stack. Also used on the T-Display SF32 in releases after Cairn 138 | CC0 1.0 (public domain dedication) | [minimp3-LICENSE.txt](licenses/minimp3-LICENSE.txt) |
| [SCOWL](http://wordlist.aspell.net/) 2020.12.07 word lists, © Kevin Atkinson and others | The keyboard's word list (levels 10 and 20) | SCOWL license (BSD-style and public-domain parts) | [SCOWL-Copyright.txt](licenses/SCOWL-Copyright.txt) |
| [esp_codec_dev](https://components.espressif.com/components/espressif/esp_codec_dev), © Espressif Systems | Reference for the ES7210 / ES7243E / ES8311 register values in Cairn's own microphone and codec code (T-Deck Plus, L2 Pro, T-LoRa Pager). Register values were followed; no code was copied | Apache 2.0 | [Apache-2.0.txt](licenses/Apache-2.0.txt) |

## ESP32 builds

| Work | Used for | License | Text |
|---|---|---|---|
| [ESP-IDF](https://github.com/espressif/esp-idf) v4.4.7, © Espressif Systems | The SDK under the Arduino core: system, drivers, Bluetooth (Bluedroid) and the Wi-Fi/Bluetooth/PHY binary libraries, plus the second-stage bootloader and partition table in the `-full.bin` files | Apache 2.0 | [Apache-2.0.txt](licenses/Apache-2.0.txt) |
| Components bundled in ESP-IDF: FreeRTOS (MIT), lwIP (BSD 3-Clause), Mbed TLS (Apache 2.0), wpa_supplicant (BSD 3-Clause), SPIFFS, FatFs, littlefs, cJSON and TinyUSB (MIT or BSD-style) | The RTOS, network stack, TLS and file systems | As listed; see [ESP-IDF's per-component licenses](https://github.com/espressif/esp-idf/tree/v4.4.7/components) | [Apache-2.0.txt](licenses/Apache-2.0.txt) and the component repositories |
| Arduino core for the ESP32: its Apache 2.0 parts (the `esp32-hal-*` layer, BLE, SD, SPIFFS, LittleFS) and libb64 (public domain) | Hardware layer, Bluetooth, SD card | Apache 2.0; libb64 public domain | [Apache-2.0.txt](licenses/Apache-2.0.txt) |
| [TFT_eSPI](https://github.com/Bodmer/TFT_eSPI) 2.5.43, © Bodmer, with Adafruit-derived parts | Display driver on the Heltec Wireless Tracker / Tracker V2 (and the T096 below) | FreeBSD, BSD and MIT | [TFT_eSPI-license.txt](licenses/TFT_eSPI-license.txt) |

The LGPL parts of the Arduino core are listed under [LGPL components](#lgpl-components).

### ESP32 repeater builds (Heltec V2, V3, V4, V4 R8, Wireless Tracker, Tracker V2)

These builds serve a web update page, which brings in the following works:

| Work | Used for | License | Text |
|---|---|---|---|
| [AsyncElegantOTA](https://github.com/ayushsharma82/AsyncElegantOTA) 2.2.8, © 2019 Ayush Sharma | The web update page and its handler | MIT | [AsyncElegantOTA-LICENSE.txt](licenses/AsyncElegantOTA-LICENSE.txt) |
| [Vue.js](https://github.com/vuejs/vue) 2.6.11 (© Evan You), [core-js](https://github.com/zloirock/core-js) 3.6.4 (© Denis Pushkarev), [regenerator-runtime](https://github.com/facebook/regenerator) (© Facebook, Inc.), [Spectre.css](https://github.com/picturepan2/spectre) 0.5.8 (© Yan Zhu) and webpack / vue-loader runtime helpers | Bundled inside the update page's web interface | MIT | [AsyncElegantOTA-web-ui-LICENSES.txt](licenses/AsyncElegantOTA-web-ui-LICENSES.txt) |
| [SparkMD5](https://github.com/satazor/js-spark-md5), © André Cruz | MD5 of the uploaded file, in the same web interface | WTFPL 2 | [AsyncElegantOTA-web-ui-LICENSES.txt](licenses/AsyncElegantOTA-web-ui-LICENSES.txt) |

ESPAsyncWebServer and AsyncTCP, which serve the page, are LGPL-3.0; see [LGPL components](#lgpl-components).

## nRF52 builds (Wio Tracker L1 Pro, L1 E-ink, L1 room server, DV1, Heltec T096 and T114, and the experimental Heltec MeshPocket, ThinkNode M1, ThinkNode M8, LilyGO T-Echo and T-Echo Lite)

| Work | Used for | License | Text |
|---|---|---|---|
| Components bundled in the Adafruit nRF52 core: FreeRTOS (MIT), Nordic nrfx drivers and MDK (BSD 3-Clause), Bluefruit52Lib, Adafruit_TinyUSB, Adafruit_nRFCrypto, Adafruit_LittleFS and InternalFileSystem (MIT; littlefs BSD 3-Clause), Nordic SoftDevice API headers (Nordic 5-Clause) | RTOS, Bluetooth, USB, crypto and flash file system | As listed; see the [core's repository](https://github.com/meshcore-dev/Adafruit_nRF52_Arduino) | the core's repository |
| ARM CryptoCell CC310 runtime (`nrf_cc310`, binary), © ARM Limited / Nordic Semiconductor | Hardware crypto, via Adafruit_nRFCrypto | ARM Object Code and Header Files License | the [core's repository](https://github.com/meshcore-dev/Adafruit_nRF52_Arduino) |
| [CustomLFS](https://github.com/oltaco/CustomLFS), © oltaco | File system on custom flash regions | MIT | the [library's repository](https://github.com/oltaco/CustomLFS) |
| [NonBlockingRTTTL](https://github.com/end2endzone/NonBlockingRTTTL) 1.4.0, © 2018 Antoine Beauchamp (end2endzone) | Buzzer melodies on the Wio Tracker L1 builds and the experimental ThinkNode M1 and M8 | MIT | [NonBlockingRTTTL-LICENSE.txt](licenses/NonBlockingRTTTL-LICENSE.txt) |
| [Adafruit GFX Library](https://github.com/adafruit/Adafruit-GFX-Library), © Adafruit Industries | Drawing on the OLED and e-paper displays, here and on the Heltec V2, V3, V4 and V4 R8 ESP32 builds, and on the experimental e-paper builds for the Heltec MeshPocket, ThinkNode M1 and M8, and LilyGO T-Echo and T-Echo Lite (from Cairn 139). The GFXfont format is also used for Cairn's Montserrat bitmap fonts | BSD 2-Clause | [Adafruit-GFX-license.txt](licenses/Adafruit-GFX-license.txt) |
| Tom Thumb font, via Adafruit GFX, © Brian J. Swetland, Vassilii Khachaturov, Dan Marks and contributors | Small font on the DV1 display | BSD 3-Clause | [source-header-LICENSES.txt](licenses/source-header-LICENSES.txt) |
| [Adafruit SSD1306](https://github.com/adafruit/Adafruit_SSD1306) 2.5.17 and [Adafruit SH110X](https://github.com/adafruit/Adafruit_SH110x) 2.1.15, © Adafruit Industries | OLED drivers: SSD1306 on the DV1 and on the Heltec V2, V3, V4 and V4 R8 ESP32 builds; SH110X on the Wio Tracker L1 Pro and room server | BSD 3-Clause | [Adafruit-SSD1306-license.txt](licenses/Adafruit-SSD1306-license.txt), [Adafruit-SH110X-license.txt](licenses/Adafruit-SH110X-license.txt) |
| [ThingPulse OLEDDisplay](https://github.com/ThingPulse/esp8266-oled-ssd1306) and its ST7789 variant, © ThingPulse / Daniel Eichhorn, Fabrice Weinberg, Helmut Tschemernjak, Heltec AutoMation, carried in MeshCore | Display layer and ArialMT bitmap fonts on the Heltec T114 | MIT | [ThingPulse-OLEDDisplay-LICENSE.txt](licenses/ThingPulse-OLEDDisplay-LICENSE.txt) |
| [TFT_eSPI](https://github.com/Bodmer/TFT_eSPI) 2.5.43, © Bodmer | Display driver on the Heltec T096 | FreeBSD, BSD and MIT | [TFT_eSPI-license.txt](licenses/TFT_eSPI-license.txt) |
| [CRC32](https://github.com/bakercp/CRC32) 2.0.1, © Christopher Baker | Skipping unchanged e-paper frames (Wio Tracker L1 E-ink, and the experimental e-paper builds for the Heltec MeshPocket, ThinkNode M1 and M8, and LilyGO T-Echo and T-Echo Lite) | MIT | [CRC32-LICENSE.md](licenses/CRC32-LICENSE.md) |

The Arduino core itself (LGPL-2.1) is listed under [LGPL components](#lgpl-components).

## Sensor drivers

These are in every image except the Heltec Wireless Tracker and Heltec V2 repeaters. Each driver is linked only where the build enables that sensor.

| Work | License | Text |
|---|---|---|
| Adafruit [AHTX0](https://github.com/adafruit/Adafruit_AHTX0), [BME280](https://github.com/adafruit/Adafruit_BME280_Library), [SHTC3](https://github.com/adafruit/Adafruit_SHTC3), [MLX90614](https://github.com/adafruit/Adafruit-MLX90614-Library), [INA219](https://github.com/adafruit/Adafruit_INA219) and [INA260](https://github.com/adafruit/Adafruit_INA260) drivers, © Adafruit Industries | BSD 3-Clause | [AHTX0](licenses/Adafruit-AHTX0-license.txt), [BME280](licenses/Adafruit-BME280-LICENSE.txt), [SHTC3](licenses/Adafruit-SHTC3-license.txt), [MLX90614](licenses/Adafruit-MLX90614-license.txt), [INA219](licenses/Adafruit-INA219-license.txt), [INA260](licenses/Adafruit-INA260-license.txt) |
| Adafruit [BMP280](https://github.com/adafruit/Adafruit_BMP280_Library), [BMP085](https://github.com/adafruit/Adafruit-BMP085-Library) and [BME680](https://github.com/adafruit/Adafruit_BME680) drivers, © Adafruit Industries, with Bosch Sensortec's BME68x API | BSD (Bosch part BSD 3-Clause) | [source-header-LICENSES.txt](licenses/source-header-LICENSES.txt) |
| [Adafruit_VL53L0X](https://github.com/adafruit/Adafruit_VL53L0X), © Adafruit Industries, with the STMicroelectronics VL53L0X API | MIT; ST part BSD 3-Clause | [source-header-LICENSES.txt](licenses/source-header-LICENSES.txt) |
| [Adafruit INA3221](https://github.com/adafruit/Adafruit_INA3221) © Adafruit Industries, and [INA226](https://github.com/RobTillaart/INA226) © Rob Tillaart | MIT | [INA3221](licenses/Adafruit-INA3221-license.txt), [INA226](licenses/INA226-LICENSE.txt) |
| [Adafruit Unified Sensor](https://github.com/adafruit/Adafruit_Sensor), © Adafruit Industries | Apache 2.0 | [Adafruit-Unified-Sensor-LICENSE.txt](licenses/Adafruit-Unified-Sensor-LICENSE.txt) |
| [Sensirion Core](https://github.com/Sensirion/arduino-core) and [Sensirion I2C SHT4x](https://github.com/Sensirion/arduino-i2c-sht4x), © Sensirion AG | BSD 3-Clause | [Core](licenses/Sensirion-Core-LICENSE.txt), [SHT4x](licenses/Sensirion-I2C-SHT4x-LICENSE.txt) |

The LPS22HB barometer and the GPS (NMEA) parsing use Cairn's own code.

## The LilyGO T-Display SF32 build and its installer

These also include the following works. The SF32 image contains none of the LGPL components listed below.

| Work | Used for | License | Text |
|---|---|---|---|
| [SiFli SDK](https://github.com/OpenSiFli/SiFli-SDK), © SiFli Technologies | SF32 drivers, Bluetooth stack, bootloader (with Cairn's update-slot changes) | Apache 2.0 (some files under SiFli's own BSD-style license) | [SiFli-SDK-LICENSE.txt](licenses/SiFli-SDK-LICENSE.txt) |
| [RT-Thread](https://github.com/RT-Thread/rt-thread), © RT-Thread Development Team | Real-time operating system | Apache 2.0 | [RT-Thread-LICENSE.txt](licenses/RT-Thread-LICENSE.txt) |
| [FlashDB](https://github.com/armink/FlashDB), © Armink, via the SiFli SDK | Settings storage | Apache 2.0 | [Apache-2.0.txt](licenses/Apache-2.0.txt) |
| [FatFs](http://elm-chan.org/fsw/ff/) R0.12b, © ChaN, via RT-Thread | SD card file system | FatFs license (BSD-style, one clause) | [the FatFs site](http://elm-chan.org/fsw/ff/doc/appnote.html#license) |
| [LVGL](https://github.com/lvgl/lvgl), © LVGL Kft, with its bundled [QR Code generator](https://github.com/nayuki/QR-Code-generator) (© Project Nayuki) | Graphics library for the SF32 interface | MIT | [LVGL-LICENSE.txt](licenses/LVGL-LICENSE.txt) |
| [Font Awesome Free 5](https://github.com/FortAwesome/Font-Awesome), © Fonticons, Inc., via LVGL | Some interface symbols | Icons CC BY 4.0, font SIL OFL 1.1 | [FontAwesome-LICENSE.txt](licenses/FontAwesome-LICENSE.txt) |
| [DejaVu Sans](https://github.com/dejavu-fonts/dejavu-fonts), © Bitstream, DejaVu changes public domain | Extra glyphs in the SF32 fonts | Bitstream Vera license | [DejaVu-LICENSE.txt](licenses/DejaVu-LICENSE.txt) |
| [BHY2 SensorAPI](https://github.com/boschsensortec/BHY2_SensorAPI), © Bosch Sensortec GmbH, via LilyGO's SF32 SDK | Motion sensor driver | BSD 3-Clause | [BHY2-SensorAPI-LICENSE.txt](licenses/BHY2-SensorAPI-LICENSE.txt) |
| [sftool](https://github.com/OpenSiFli/sftool), © OpenSiFli | The flashing tool bundled, unchanged, in the SF32 `-install.zip` | Apache 2.0 | [sftool-LICENSE.txt](licenses/sftool-LICENSE.txt) |
| [pyserial](https://github.com/pyserial/pyserial) 3.5, © Chris Liechti | Serial-port access for the installer's helper, bundled unchanged in the SF32 `-install.zip` | BSD 3-Clause | [pyserial-LICENSE.txt](licenses/pyserial-LICENSE.txt) |

## The SenseCAP MeshPager X2 build (experimental)

This build also includes:

| Work | Used for | License | Text |
|---|---|---|---|
| [BMM350 SensorAPI](https://github.com/boschsensortec/BMM350_SensorAPI) v1.10.0, © 2024 Bosch Sensortec GmbH | The compass (BMM350 magnetometer driver), unmodified | BSD 3-Clause | [BMM350-SensorAPI-LICENSE.txt](licenses/BMM350-SensorAPI-LICENSE.txt) |

## The LilyGO T-LoRa Pager build

This build also includes:

| Work | Used for | License | Text |
|---|---|---|---|
| [BHY2 SensorAPI](https://github.com/boschsensortec/BHY2_SensorAPI) v1.6.0, © 2023 Bosch Sensortec GmbH | Lift to wake (the BHI260AP motion sensor's driver), unmodified | BSD 3-Clause | [BHY2-SensorAPI-LICENSE.txt](licenses/BHY2-SensorAPI-LICENSE.txt) |
| BHI260AP firmware image (`firmware/bhi260ap/BHI260AP.fw`, from the same repository), © Bosch Sensortec GmbH | Uploaded to the motion sensor's RAM at run time, unmodified | BSD 3-Clause (the repository's license) | [BHY2-SensorAPI-LICENSE.txt](licenses/BHY2-SensorAPI-LICENSE.txt) |

## The LilyGO T5 E-Paper S3 Pro build (experimental)

This build also includes:

| Work | Used for | License | Text |
|---|---|---|---|
| [FastEPD](https://github.com/bitbank2/FastEPD) 2.2.0, © BitBank Software, Inc. | The e-paper panel driver, with Cairn's patches | Apache 2.0 | [FastEPD-LICENSE.txt](licenses/FastEPD-LICENSE.txt) |

## The LilyGO T-Display K230 build (experimental)

This build also includes:

| Work | Used for | License | Text |
|---|---|---|---|
| [musl libc](https://musl.libc.org/), © Rich Felker and contributors | The C library, linked into the program | MIT | [musl-COPYRIGHT.txt](licenses/musl-COPYRIGHT.txt) |
| [lr2021-sdr](https://github.com/SAMS0N1TE/lr2021-sdr), © 2026 SAMS0N1TE | How to read raw radio samples from the LR2021, for the Spectrum page's Live view | MIT | [lr2021-sdr-LICENSE.txt](licenses/lr2021-sdr-LICENSE.txt) |

## The Cairn manual

The [Cairn firmware manual](docs/Cairn_Firmware_Manual_Dark) (its web version and PDF) also includes:

| Work | Used for | License | Text |
|---|---|---|---|
| [Inter and Inter Tight](https://github.com/rsms/inter), © The Inter Project Authors | Body and heading typefaces, bundled in `docs/Cairn_Firmware_Manual_Dark/fonts/` and embedded in the PDF | SIL Open Font License 1.1 | [Inter-OFL.txt](licenses/Inter-OFL.txt) |
| [JetBrains Mono](https://github.com/JetBrains/JetBrainsMono), © The JetBrains Mono Project Authors | Labels and key names, bundled and embedded the same way | SIL Open Font License 1.1 | [JetBrainsMono-OFL.txt](licenses/JetBrainsMono-OFL.txt) |

## LGPL components

The following libraries are under the GNU Lesser General Public License and are statically linked into the builds named. They are not under a permissive license. Cairn's own code is not covered by the LGPL. See [LGPL relinking materials](#lgpl-relinking-materials) for how the LGPL's relinking requirement is met.

| Work | Used for, and in which builds | License | Text |
|---|---|---|---|
| [Arduino core for the ESP32](https://github.com/espressif/arduino-esp32) 2.0.17, © the Arduino Team, Espressif Systems and contributors | The Arduino framework, in every ESP32 build. Its Arduino-derived core files and the WiFi, WebServer, HTTPClient, WiFiClientSecure, FS, SPI, Wire, DNSServer and ArduinoOTA libraries are LGPL | LGPL-2.1 or later | [LGPL-2.1.txt](licenses/LGPL-2.1.txt) |
| [Adafruit nRF52 Arduino core](https://github.com/adafruit/Adafruit_nRF52_Arduino), in [MeshCore's fork](https://github.com/meshcore-dev/Adafruit_nRF52_Arduino) at commit d541301 (a Bluetooth-stack lock-up fix), © Arduino LLC, Sandeep Mistry, Adafruit Industries | The Arduino framework with its SPI and Wire libraries, in every nRF52 build (Wio Tracker L1 Pro, L1 E-ink, L1 room server, DV1, Heltec T096 / T114, and the experimental Heltec MeshPocket, ThinkNode M1, ThinkNode M8, LilyGO T-Echo and T-Echo Lite) | LGPL-2.1 or later | [Adafruit-nRF52-Arduino-LICENSE.txt](licenses/Adafruit-nRF52-Arduino-LICENSE.txt) (full text: [LGPL-2.1.txt](licenses/LGPL-2.1.txt)) |
| [ESPAsyncWebServer](https://github.com/ESP32Async/ESPAsyncWebServer) 3.10.3, © Hristo Gochkov, Mathieu Carbou, Emil Muratov, Will Miles | The web update page, in the ESP32 repeater builds only | LGPL-3.0 | [ESPAsyncWebServer-LICENSE.txt](licenses/ESPAsyncWebServer-LICENSE.txt) (with [GPL-3.0.txt](licenses/GPL-3.0.txt), which LGPL-3.0 builds on) |
| [AsyncTCP](https://github.com/ESP32Async/AsyncTCP) 3.5.0, © Hristo Gochkov, Mathieu Carbou, Emil Muratov, Will Miles | Network layer of the web update page, in the ESP32 repeater builds only | LGPL-3.0 | [AsyncTCP-LICENSE.txt](licenses/AsyncTCP-LICENSE.txt) (with [GPL-3.0.txt](licenses/GPL-3.0.txt)) |

[Adafruit NeoPixel](https://github.com/adafruit/Adafruit_NeoPixel) 1.15.5 (LGPL-3.0, [Adafruit-NeoPixel-COPYING.txt](licenses/Adafruit-NeoPixel-COPYING.txt)) is fetched as a dependency of the sensor libraries. It is not linked into any release image.

The compiler runtime libraries are statically linked into every image: GCC's libgcc and libstdc++, under the GPL with the GCC Runtime Library Exception, and newlib, under BSD-style licenses. The exception means they place no conditions on the firmware.

## LGPL relinking materials

The LGPL lets you modify the LGPL libraries above and use your modified versions with Cairn. For each Cairn release, the materials to do this are available on request for every image that contains an LGPL component (every ESP32 and nRF52 image). The T-Display SF32 and K230 images contain no LGPL code. For each image the materials are:

- Cairn's compiled object files and archives for that image, with the exact linker command, linker scripts and build flags, so the image can be relinked against a modified copy of the LGPL libraries.
- The exact version of each LGPL library's source used in that image, or a pointer to it:
  - arduino-esp32 2.0.17, as packaged by PlatformIO (`framework-arduinoespressif32` 3.20017.241212).
  - MeshCore's Adafruit nRF52 core fork at commit d541301.
  - ESPAsyncWebServer 3.10.3 and AsyncTCP 3.5.0.
- For the LGPL-3.0 libraries (the repeater images): the installation information. A relinked image installs the same way as a release image, over USB with the ESP32 serial bootloader or through the repeater's web update page. Cairn does not lock the bootloader or the flash.

**How to request them:** open an issue at [github.com/cvhviz/CAIRN/issues](https://github.com/cvhviz/CAIRN/issues) titled "LGPL relinking materials", naming the release (for example `cairn-v139`) and the image file. The materials are provided free of charge, apart from any cost of physically sending them if you ask for a copy on a physical medium.

**This offer is valid for at least three years** after the last date on which Cairn distributed the image concerned, and is open to anyone who has a copy of that image. This written offer is how the requirements of LGPL-2.1 section 6(c) and LGPL-3.0 section 4(d) are met.

The materials are kept from Cairn 139 on. For Cairn 138 and earlier images, see [Earlier releases](#earlier-releases).

## Earlier releases

Cairn releases up to and including **Cairn 138** contained the following works, which later releases have replaced with Cairn's own code or with Montserrat-based fonts. Their licenses still apply to those earlier images, which remain available for download, so the texts stay here. Each image is named below by its Cairn 138 file name. Earlier releases of the same boards that used the same component carry the same obligation.

| Work | License | Cairn 138 images that contain it | Text |
|---|---|---|---|
| [arduino-audio-driver](https://github.com/pschatzmann/arduino-audio-driver) 0.2.1, © Phil Schatzmann. Its bundled codec drivers (WM8960, WM8994, CS43L22 and others) carry their vendors' notices in the library source | GPL-3.0 | `MeshCore-WioL2Pro-…`, `MeshCore-TLoraPager-…`, `MeshCore-TLoraPagerLR1121-…` | [arduino-audio-driver-License.txt](licenses/arduino-audio-driver-License.txt) |
| [GxEPD2](https://github.com/ZinggJM/GxEPD2) 1.6.2, © Jean-Marc Zingg | GPL-3.0 | `MeshCore-WioL1Eink-…` | [GxEPD2-LICENSE.txt](licenses/GxEPD2-LICENSE.txt) |
| Helix MP3 decoder (libhelix-mp3), © RealNetworks, Inc., as modified in the [SiFli SDK](https://github.com/OpenSiFli/SiFli-SDK) (`external/libhelix-mp3`) | RealNetworks Public Source License 1.0 (RPSL) | `MeshCore-TDisplaySF32-…-update.bin` and the `main.bin` in `MeshCore-TDisplaySF32-…-install.zip` | [Helix-RPSL.txt](licenses/Helix-RPSL.txt) (the SDK's `external/libhelix-mp3/RPSL.txt`) |
| GNU FreeFont (FreeSans / FreeSansBold) bitmap fonts, as converted in the Adafruit GFX Library, and Cairn's earlier CairnClockBold, CairnClockBold36 and CairnSans10 fonts rasterised from FreeSans | GPL-3.0 or later with the GNU FreeFont font exception | `MeshCore-WioL1Eink-…`, `MeshCore-HeltecT114-…-ble` | [GPL-3.0.txt](licenses/GPL-3.0.txt) |
| [MicroNMEA](https://github.com/stevemarple/MicroNMEA) 2.0.6, © Steve Marple | LGPL-2.1 | Every Cairn 138 image except `MeshCore-HeltecV2-…-repeater`. This includes the T-Display SF32 | [MicroNMEA-LICENSE.txt](licenses/MicroNMEA-LICENSE.txt) |
| [Arduino_LPS22HB](https://github.com/arduino-libraries/Arduino_LPS22HB) 1.0.3, by Arduino | LGPL-2.1 or later | `MeshCore-HeltecTrackerV2-…` (ble and repeater), `MeshCore-HeltecV3-…-repeater`, `MeshCore-HeltecV4-…-repeater`, `MeshCore-HeltecV4R8-…` (ble and repeater), `MeshCore-HeltecV4Touch-…`, `MeshCore-HeltecV4KitV1-…`, `MeshCore-HeltecT096-…` (ble, usb and repeater), `MeshCore-HeltecT114-…` (ble and repeater), `MeshCore-WioL1Pro-…`, `MeshCore-DV1-…`, `MeshCore-WioL1Eink-…`, `MeshCore-WioL1RoomServer-…` | [LGPL-2.1.txt](licenses/LGPL-2.1.txt) |

The source code of these works, as used in those releases, is available from the upstream projects linked above at the versions given.

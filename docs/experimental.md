# Experimental builds

Experimental builds are for testing: a new board brought up before it has been on the bench, or a change that needs trying on someone's hardware before it goes into a release. They are published as GitHub **pre-releases** tagged `experimental-<board>-<N>` (a group of boards shares one, as `experimental-eink-139`), separate from the normal `cairn-vN` releases.

**[All experimental builds](https://github.com/cvhviz/CAIRN/releases?q=experimental&expanded=true)** · [regular downloads](downloads.md)

## What "experimental" means

- **It may not work at all.** The screen may stay dark, a button may do the wrong thing, or the board may not stay on. Nothing in a Cairn build can damage the hardware, and you can always flash something else.
- **No online updates.** A device on an experimental build is never offered one, and the online updater never offers an experimental build: it reads only the latest normal release. To move on, flash the next build by hand.
- **Keep a copy of your current firmware** to go back to, and back up your node's identity first (see [Before a first install](install/esp32-s3.md#before-a-first-install-back-up-your-identity)).
- Each release's notes say what to test and what to send back. Most ask for a **serial log**: the build prints what it finds as it starts, and every button press, over USB.

Compared with 🧪 **preview** boards (built from the same tree in every normal release, untried on hardware), an experimental build is a one-off made to answer specific questions; once a board works, it moves into the normal releases. The ThinkNode M9 USB companion did that in Cairn 136 ([the M9 page](boards/thinknode-m9.md)). The Heltec Mesh Node T114 companion did that in Cairn 133 ([the T096 page](boards/heltec-t096.md#from-cairn-133)). The Heltec V4 + Expansion Kit V1 did that in Cairn 130 ([its page](boards/heltec-v4-kit-v1.md)). The LilyGO T-LoRa Pager did that in Cairn 125 ([its page](boards/lilygo-t-lora-pager.md)); its first test build stays in [the experimental releases](https://github.com/cvhviz/CAIRN/releases/tag/experimental-tlora-pager-124).

## Current

| Board | Build | Date | What it is for |
|---|---|---|---|
| E-ink boards (companion), five in one pre-release: Heltec MeshPocket, Elecrow ThinkNode M1 and M8, LilyGO T-Echo and T-Echo Lite | [Cairn 139](https://github.com/cvhviz/CAIRN/releases/tag/experimental-eink-139) | 22 Nov 2026 | Cairn's own e-paper driver (from Cairn 139) and the Wio Tracker L1 E-ink's screen, stretched to each board's glass; one `-ble.uf2` per board. MeshPocket: 2.13" 122x250 SSD1680 glass, one button, 350 contacts. ThinkNode M1: 1.54" 200x200 SSD1681 glass with front light, 510 contacts. ThinkNode M8: 1.54" 200x200 glass (SSD1681 assumed: the M8's controller isn't documented), rotary knob, 510 contacts. T-Echo: 1.54" 200x200 SSD1681 glass, 510 contacts. T-Echo Lite: 1.22" 192x176 SSD1681 glass, 350 contacts. Builds; never run on any of these boards |
| Heltec WiFi LoRa 32 V4, OLED (companion; the plain V4, not the V4-R8), and the V4 in the non-touch Expansion Kit | [Cairn 137](https://github.com/cvhviz/CAIRN/releases/tag/experimental-heltec-v4-137) | 18 Nov 2026 | The V4-R8 OLED companion's one-button screen and Wi-Fi on the plain V4's 2 MB PSRAM ([#53](https://github.com/cvhviz/CAIRN/issues/53)): `HeltecV4` for the V4 on its own (runs on one V4 updated over 107; another stops on "Loading..." after a fresh install, open in #53), `HeltecV4ExpKit` for the V4 in the glass-front Expansion Kit, with its BME280 and GXHTC3 sensors (telemetry to the app) and its buzzer (not yet run on a kit). Each has a `-ble-full.bin` (at `0x0`) and a `-ble-update.bin` (at `0x10000`). The V4 repeater stays in the normal release |
| GAT562 30S Mesh Kit (companion) | [Cairn 131](https://github.com/cvhviz/CAIRN/releases/tag/experimental-gat562-131) | 11 Nov 2026 | The L1 Pro's interface with the whole joystick, so up and down work in every list ([#45](https://github.com/cvhviz/CAIRN/issues/45)). Bluetooth and USB-serial images. Builds; not yet run on a kit |
| Heltec Vision Master T190 (companion) | [Cairn 130](https://github.com/cvhviz/CAIRN/releases/tag/experimental-t190-130) | 10 Nov 2026 | First build: the wheel-driven Cairn screen on the T190's 1.9" display, the app over Bluetooth and Wi-Fi. Bluetooth and USB-serial images |
| Heltec WiFi LoRa 32 V3 (companion) | [Cairn 130](https://github.com/cvhviz/CAIRN/releases/tag/experimental-heltec-v3-130) | 10 Nov 2026 | The T096's one-button screen on the V3's OLED, Bluetooth and USB-serial images. Builds; not run on a V3 since the Cairn 107 preview. The V3 repeater stays in the normal release |
| LilyGO T5 E-Paper S3 Pro (H752-01) | [Cairn 127](https://github.com/cvhviz/CAIRN/releases/tag/experimental-t5epd-127) | 3 Nov 2026 | Text at the panel's own 960x540 resolution, sharp instead of blocky; USB drive mode and the live page; a recovery for a panel power chip left latched by a crash ([#22](https://github.com/cvhviz/CAIRN/issues/22)) |
| LilyGO T-Display K230 Kit (LR2021) | [Cairn 126](https://github.com/cvhviz/CAIRN/releases/tag/experimental-tdisplay-k230-126) | 1 Nov 2026 | First build, tested on one kit: a Linux program, installed from the console. No Bluetooth |
| Seeed SenseCAP MeshPager X2 | [Cairn 127](https://github.com/cvhviz/CAIRN/releases/tag/experimental-meshpager-x2-127) | 3 Nov 2026 | Cairn 127's changes (blocking, the live page, sharper text). Bring-up continues |

## Sending a log

1. Flash the `-full.bin` at `0x0` ([ESP32-S3 guide](install/esp32-s3.md)).
2. Open a serial console on the board's USB port at **115200** baud: the [web flasher](https://espressif.github.io/esptool-js/)'s Console, Arduino IDE's Serial Monitor, `screen`, PuTTY.
3. Unplug and replug the board so the log starts from power-up, then do what the release notes ask.
4. [Open an issue](https://github.com/cvhviz/CAIRN/issues/new/choose) (**Bug report**) with the build's tag, the log, and a photo of the screen. "It works" is a useful report too.

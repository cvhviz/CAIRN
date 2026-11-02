# Experimental builds

Experimental builds are for testing: a new board brought up before it has been on the bench, or a change that needs trying on someone's hardware before it goes into a release. They are published as GitHub **pre-releases** tagged `experimental-<board>-<N>`, separate from the normal `cairn-vN` releases.

**[All experimental builds](https://github.com/cvhviz/CAIRN/releases?q=experimental&expanded=true)** · [regular downloads](downloads.md)

## What "experimental" means

- **It may not work at all.** The screen may stay dark, a button may do the wrong thing, or the board may not stay on. Nothing in a Cairn build can damage the hardware, and you can always flash something else.
- **No online updates.** A device on an experimental build is never offered one, and the online updater never offers an experimental build: it reads only the latest normal release. To move on, flash the next build by hand.
- **Keep a copy of your current firmware** to go back to, and back up your node's identity first (see [Before a first install](install/esp32-s3.md#before-a-first-install-back-up-your-identity)).
- Each release's notes say what to test and what to send back. Most ask for a **serial log**: the build prints what it finds as it starts, and every button press, over USB.

Compared with 🧪 **preview** boards (built from the same tree in every normal release, untried on hardware), an experimental build is a one-off made to answer specific questions; once a board works, it moves into the normal releases. The LilyGO T-LoRa Pager did that in Cairn 125 ([its page](boards/lilygo-t-lora-pager.md)); its first test build stays in [the experimental releases](https://github.com/cvhviz/CAIRN/releases/tag/experimental-tlora-pager-124).

## Current

| Board | Build | Date | What it is for |
|---|---|---|---|
| LilyGO T5 E-Paper S3 Pro (H752-01) | [Cairn 126](https://github.com/cvhviz/CAIRN/releases/tag/experimental-t5epd-126) | 1 Nov 2026 | First build, tested on one board: the 4.7" touch e-paper, GPS, microSD maps ([#22](https://github.com/cvhviz/CAIRN/issues/22)) |
| LilyGO T-Display K230 Kit (LR2021) | [Cairn 126](https://github.com/cvhviz/CAIRN/releases/tag/experimental-tdisplay-k230-126) | 1 Nov 2026 | First build, tested on one kit: a Linux program, installed from the console. No Bluetooth |
| Seeed SenseCAP MeshPager X2 | [Cairn 126](https://github.com/cvhviz/CAIRN/releases/tag/experimental-meshpager-x2-126) | 1 Nov 2026 | Bring-up continues: Cyrillic, and the power off, Band scan, air pressure, USB drive and Lift to wake checks from test 5. Earlier tests: [all X2 builds](https://github.com/cvhviz/CAIRN/releases?q=meshpager-x2) |

## Sending a log

1. Flash the `-full.bin` at `0x0` ([ESP32-S3 guide](install/esp32-s3.md)).
2. Open a serial console on the board's USB port at **115200** baud: the [web flasher](https://espressif.github.io/esptool-js/)'s Console, Arduino IDE's Serial Monitor, `screen`, PuTTY.
3. Unplug and replug the board so the log starts from power-up, then do what the release notes ask.
4. [Open an issue](https://github.com/cvhviz/CAIRN/issues/new/choose) (**Bug report**) with the build's tag, the log, and a photo of the screen. "It works" is a useful report too.

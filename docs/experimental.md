# Experimental builds

Experimental builds are for testing: a new board brought up before it has been on the bench, or a change that needs trying on someone's hardware before it goes into a release. They are published as GitHub **pre-releases** tagged `experimental-<board>-<N>`, separate from the normal `cairn-vN` releases.

**[All experimental builds](https://github.com/cvhviz/Cairn/releases?q=experimental&expanded=true)**

## What "experimental" means

- **It may not work at all.** The screen may stay dark, a button may do the wrong thing, or the board may not stay on. Nothing in a Cairn build can damage the hardware, and you can always flash something else.
- **No online updates.** A device on an experimental build is never offered one, and the online updater never offers an experimental build: it reads only the latest normal release. To move on, flash the next build by hand.
- **Keep a copy of your current firmware** to go back to, and back up your node's identity first (see [Before a first install](install/esp32-s3.md#before-a-first-install-back-up-your-identity)).
- Each release's notes say what to test and what to send back. Most ask for a **serial log**: the build prints what it finds as it starts, and every button press, over USB.

Compared with 🧪 **preview** boards (built from the same tree in every normal release, untried on hardware), an experimental build is a one-off made to answer specific questions; once a board works, it moves into the normal releases.

## Current

| Board | Build | Date | What it is for |
|---|---|---|---|
| SenseCAP MeshPager X2 (Seeed) | [Cairn 124 test](https://github.com/cvhviz/Cairn/releases/tag/experimental-meshpager-x2-124) | 26 Oct 2026 | First bring-up, made from Seeed's block diagram without the board in hand: screen, d-pad, OK, Back, power latch, LoRa, Bluetooth, GPS, microSD |

## Sending a log

1. Flash the `-full.bin` at `0x0` ([ESP32-S3 guide](install/esp32-s3.md)).
2. Open a serial console on the board's USB port at **115200** baud: the [web flasher](https://espressif.github.io/esptool-js/)'s Console, Arduino IDE's Serial Monitor, `screen`, PuTTY.
3. Unplug and replug the board so the log starts from power-up, then do what the release notes ask.
4. [Open an issue](https://github.com/cvhviz/Cairn/issues/new/choose) (**Bug report**) with the build's tag, the log, and a photo of the screen. "It works" is a useful report too.

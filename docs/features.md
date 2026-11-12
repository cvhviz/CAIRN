# Features by board

What each board's Cairn build does, as of the latest release. Each board's page (all listed on the [downloads page](downloads.md)) has the details, and the [L2 Pro page](boards/wio-tracker-l2-pro.md#features) describes the touch interface in full.

| Feature                       |  L1 Pro  | L2 Pro | Heltec V4 touch (Kit V2) | ThinkNode M9 |   T-Deck    | T-LoRa Pager | T-Display SF32 |   T096   | Preview |
| ----------------------------- | :------: | :----: | :----------------------: | :----------: | :---------: | :----------: | :------------: | :------: | :-----: |
| MeshCore apps over Bluetooth  |    ✅    |   ✅   |       ✅        |      ✅      |     ✅      |      ✅       |       ✅       |    ✅    |   ✅    |
| Input                         | joystick | touch  |      touch      |     keys     | touch, keys | keys, wheel  | touch, keypad  |  button  | button  |
| Color emoji                  |    –     |   ✅   |       ✅        |      ✅      |     ✅      |      ✅       |       ✅       |    –     |    –    |
| Wi-Fi                         |    –     |   ✅   |       ✅        |      ✅      |     ✅      |      ✅       |      ✅ ¹      |    –     |    –    |
| Online updates                |    –     |   ✅   |       ✅        |      ✅      |    ✅ ²     |     ✅ ⁷      |       ✅       |    –     |    –    |
| GPS                           |    ✅    |   ✅   |      ✅ ³       |      ✅      |    Plus     |      ✅       |       ✅       |    ✅    |  some   |
| microSD card                  |    –     |   ✅   |       ✅        |      ✅      |     ✅      |      ✅       |       ✅       |    –     |    –    |
| Offline map                   |    –     |   ✅   |       ✅        |      ✅      |     ✅      |      ✅       |       ✅       |    –     |    –    |
| Map downloads, online map     |    –     |   ✅   |       ✅        |      ✅      |     ✅      |      ✅       |       ✅       |    –     |    –    |
| Spectrum and band scan        |    –     |   ✅   |       ✅        |      ✅      |     ✅      |      ✅       |       ✅       | spectrum |    –    |
| Repeater scan and admin       |    –     |   ✅   |       ✅        |      ✅      |     ✅      |      ✅       |       ✅       |    –     |    –    |
| USB-serial companion          |    –     |   –    |        –        |      –       |      –      |      –       |       –        |    ✅    |   ✅    |
| Contact QR code               |    –     |   ✅   |       ✅        |      ✅      |     ✅      |      ✅       |       –        |    –     |    –    |
| Room server image             |    ✅    |   –    |        –        |      –       |      –      |      –       |       –        |    –     |    –    |
| Color themes                 |    –     |   ✅   |       ✅        |      ✅      |     ✅      |      ✅       |       ✅       |    ✅    | some ⁴  |
| Wi-Fi and Bluetooth scanners  |    –     |   ✅   |       ✅        |      ✅      |     ✅      |      ✅       |       ✅       |    –     |    –    |
| Music player                  |    –     |   ✅   |        –        |      –       |    ✅ ⁵     |      ✅       |       ✅       |    –     |    –    |
| Voice recorder                |    –     |  ✅ ⁶  |        –        |      –       |    ✅ ⁵     |      ✅       |       ✅       |    –     |    –    |
| Traffic log, packet details   |    –     |   ✅   |       ✅        |      ✅      |     ✅      |      ✅       |       ✅       |    –     |    –    |
| Spectrum, history to CairnOS  |    –     |   ✅   |       ✅        |      ✅      |     ✅      |      ✅       |       –        |    –     |    –    |
| File manager                  |    –     |   ✅   |       ✅        |      ✅      |     ✅      |      ✅       |       –        |    –     |    –    |
| USB drive (microSD)           |    –     |   ✅   |       ✅ ⁸      |      –       |     ✅      |      ✅       |       –        |    –     |    –    |
| Block nodes on the device     |    ✅    |   ✅   |       ✅        |      ✅      |     ✅      |      ✅       |       ✅       |    ✅    |    –    |
| Live page in a browser        |    –     |   ✅   |       ✅        |      ✅      |     ✅      |      ✅       |       –        |    –     |    –    |
| IR remote, climate sensors    |    –     |   –    |        –        |      –       |      –      |      –       |       ✅       |    –     |    –    |
| Imperial units, 12-hour clock |    ✅    |   ✅   |       ✅        |      ✅      |     ✅      |      ✅       |       ✅       |    ✅    |   ✅    |

¹ Clock sync and online updates; no app link over Wi-Fi. ² From Cairn 108 on. ³ With the Expansion Kit. ⁴ The color-screen boards (Wireless Tracker, T1). ⁵ From Cairn 113, tried on a T-Deck Plus. ⁶ From Cairn 115. ⁷ From Cairn 125. ⁸ From Cairn 127.

The **Heltec V4 + Expansion Kit V1** build (✅) is the Heltec V4 touch interface without the map, card storage, map downloads, the online map and the map cache; see [its page](boards/heltec-v4-kit-v1.md#against-the-expansion-kit-v2-build). The **Heltec Wireless Tracker V2 and V4-R8 (OLED) companions** (✅ beta, from Cairn 131) are the T096 column plus Wi-Fi for the app (no online updates); the Tracker V2 has the color themes, the V4-R8 is white on black; see [their page](boards/heltec-one-button.md). The **compact repeater** has its own short list on [its page](boards/compact-repeater.md#pages).

Back to the [README](../README.md).

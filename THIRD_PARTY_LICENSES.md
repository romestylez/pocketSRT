# Third-party licenses and notices

This document identifies the principal open-source libraries and reference implementations used by pocketSRT 5.0.0. The linked upstream license files contain the complete license terms.

## Runtime dependencies

| Component | Version | Purpose | License |
|---|---:|---|---|
| [srtdroid](https://github.com/ThibaultBee/srtdroid) | 1.9.5 | SRT protocol implementation and output transport | [Apache-2.0](https://github.com/ThibaultBee/srtdroid/blob/main/LICENSE.md) |
| [AndroidX Media3](https://github.com/androidx/media) | 1.6.1 | ExoPlayer-based FLV/RTMP ingest, decoding and playback clock | [Apache-2.0](https://github.com/androidx/media/blob/release/LICENSE) |
| [OkHttp](https://github.com/lysine-dev/okhttp) | 4.12.0 | Networking for the pocketBond/Moblink helper service | [Apache-2.0](https://github.com/lysine-dev/okhttp/blob/parent-4.12.0/LICENSE.txt) |
| [Kotlinx Serialization](https://github.com/Kotlin/kotlinx.serialization) | 1.7.3 | JSON serialization for the helper service and local API | [Apache-2.0](https://github.com/Kotlin/kotlinx.serialization/blob/master/LICENSE.txt) |
| [Kotlinx Coroutines](https://github.com/Kotlin/kotlinx.coroutines) | 1.9.0 | Android asynchronous runtime | [Apache-2.0](https://github.com/Kotlin/kotlinx.coroutines/blob/master/LICENSE.txt) |

pocketSRT also uses AndroidX, Kotlin and Material Components libraries distributed under the Apache License 2.0.

## Adapted and reference implementations

### Moblin

- Project: [eerimoq/moblin](https://github.com/eerimoq/moblin)
- Use: DJI BLE protocol, SRTLA client/scheduler behavior, adaptive-bitrate behavior, and reference for the native RTMP ingest
- License: [MIT](https://github.com/eerimoq/moblin/blob/main/LICENSE)
- Copyright: © 2023 Erik Moqvist

### HaishinKit

- Project: [HaishinKit/HaishinKit.swift](https://github.com/HaishinKit/HaishinKit.swift)
- Use: reference for parts of the native RTMP protocol implementation through Moblin's modified HaishinKit components
- License: [BSD-3-Clause](https://github.com/HaishinKit/HaishinKit.swift/blob/main/LICENSE.md)
- Copyright: © 2015 shogo4405

### BlackSharkLib.swift

- Project: [Spillmaker/BlackSharkLib.swift](https://github.com/Spillmaker/BlackSharkLib.swift)
- Use: reference for the BLE protocol of supported Black Shark MagCooler devices
- License: [MIT](https://github.com/Spillmaker/BlackSharkLib.swift/blob/main/LICENSE)
- Copyright: © 2025 Spillmaker

## License texts

- [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0)
- [MIT License](https://opensource.org/license/mit)
- [BSD 3-Clause License](https://opensource.org/license/bsd-3-clause)

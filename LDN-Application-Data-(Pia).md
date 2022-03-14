The application data field allows the host of an [LDN network](LDN-Protocol) to encode game-specific information into the [advertisement frame](LDN-Protocol#advertisement-frame). This page describes how the application data is structured in games that use the [Pia framework](Pia-Overview).

The application data starts with a short header:

| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 4 | Session id (random) |
| 0x4 | 4 | Unknown CRC32 (always 0?) |
| 0x8 | 1 | [System communication version](#system-communication-version) |
| 0x9 | 1 | Header size (always 24) |
| 0xA | 2 | Padding |
| 0xC | 4 | Session param (random) |
| 0x10 | 8 | Padding |
| 0x18 | | [Application data](#application-data) |

### System Communication Version
| Version | Pia Version |
| --- | --- |
| 2 | 5.9 |
| 5 | 5.18 |

### Application Data
The application data depends on the game.
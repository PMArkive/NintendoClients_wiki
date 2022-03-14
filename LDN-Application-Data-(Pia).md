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
The application data depends on the game:

* [Super Mario Maker 2](#super-mario-maker-2)

## Super Mario Maker 2
| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 8 | Network service account id |
| 0x8 | 11x2 | Nickname (wide chars) |
| 0x1E | 2 | Padding |
| 0x20 | 88 | [Mii info](#mii-info) |
| 0x88 | 24 | Unknown |

### Mii Info
| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 16 | Create id |
| 0x10 | 11x2 | Mii name (wide chars) |
| 0x26 | 1 | Font region |
| 0x27 | 1 | Favorite color |
| 0x28 | 1 | Gender |
| 0x29 | 1 | Mii height |
| 0x2A | 1 | Mii build |
| 0x2B | 1 | Is special |
| 0x2C | 1 | Region move |
| 0x2D | 1 | Faceline type |
| 0x2E | 1 | Faceline color |
| 0x2F | 1 | Faceline wrinkle |
| 0x30 | 1 | Faceline make |
| 0x31 | 1 | Hair type |
| 0x32 | 1 | Hair color |
| 0x33 | 1 | Is hair flip |
| 0x34 | 1 | Eye type |
| 0x35 | 1 | Eye color |
| 0x36 | 1 | Eye scale |
| 0x37 | 1 | Eye aspect |
| 0x38 | 1 | Eye rotate |
| 0x39 | 1 | Eye x |
| 0x3A | 1 | Eye y |
| 0x3B | 1 | Eyebrow type |
| 0x3C | 1 | Eyebrow color |
| 0x3D | 1 | Eyebrow scale |
| 0x3E | 1 | Eyebrow aspect |
| 0x3F | 1 | Eyebrow rotate |
| 0x40 | 1 | Eyebrow x |
| 0x41 | 1 | Eyebrow y |
| 0x42 | 1 | Nose type |
| 0x43 | 1 | Nose scale |
| 0x44 | 1 | Nose y |
| 0x45 | 1 | Mouth type |
| 0x46 | 1 | Mouth color |
| 0x47 | 1 | Mouth scale |
| 0x48 | 1 | Mouth aspect |
| 0x49 | 1 | Mouth y |
| 0x4A | 1 | Beard color |
| 0x4B | 1 | Beard type |
| 0x4C | 1 | Mustache type |
| 0x4D | 1 | Mustache scale |
| 0x4E | 1 | Mustache y |
| 0x4F | 1 | Glass type |
| 0x50 | 1 | Glass color |
| 0x51 | 1 | Glass scale |
| 0x52 | 1 | Glass y |
| 0x53 | 1 | Has mole |
| 0x54 | 1 | Mole scale |
| 0x55 | 1 | Mole x |
| 0x56 | 1 | Mole y |
| 0x57 | 1 | Padding |
This page describes the protocol that is used to communicate with nearby consoles in LDN mode, which is the default mode for local multiplayer.

Because LDN operates at the data link layer, it requires a good understanding of the [IEEE 802.11 specification](https://ieeexplore.ieee.org/document/9363693).

The host of the session broadcasts a custom action frame every 100 milliseconds. To find nearby consoles, the console scans for these action frames.

Also see: [[Local Wireless Communication on PC]].

### Action Frame Format
Defined by IEEE 802.11 specification:

| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 1 | Category (127 = vendor-specific) |
| 0x1 | 3 | OUI (`00:22:AA`) |

Defined by Nintendo:

| Offset | Size | Description |
| --- | --- | --- |
| 0x4 | 1 | Protocol id (4 = LDN) |
| 0x5 | 1 | Padding (always 0) |
| 0x6 | 2 | Packet type (257 = advertisement) |
| 0x8 | 2 | Must be 0 |
| 0xA | 2 | Padding (always 0) |
| 0xC | | [Advertisement frame](#advertisement-frame) |

#### Advertisement Frame
| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 32 | [Advertisement header](#advertisement-header) |
| 0x20 | 1 | [LDN version](#ldn-version) |
| 0x21 | 1 | Encryption type (1=plain, 2=AES-CTR) |
| 0x22 | 2 | Advertisement data size |
| 0x24 | 4 | Nonce for AES-CTR algorithm |
| 0x28 | 32 | SHA-256 hash, calculated over the whole advertisement frame with the hash set to zero |
| 0x48 | | [Advertisement data](#advertisement-data) |

If encryption is enabled, the hash and advertisement data are encrypted with AES-CTR. The input buffer for [key derivation](#key-derivation) is the [advertisement header](#advertisement-header), and the input key is `191884743e24c77d87c69e4207d0c438`.

#### Advertisement Header
| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 8 | Local communication id (usually the title id) |
| 0x8 | 2 | Padding (Always 0) |
| 0xA | 2 | Game mode |
| 0xC | 4 | Padding (always 0) |
| 0x10 | 16 | Random bytes for key generation |

#### Advertisement Data
| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 16 | Session key |
| 0x10 | 2 | Unknown |
| 0x12 | 1 | Is session closed |
| 0x13 | 3 | Unknown |
| 0x16 | 1 | Maximum number of participants |
| 0x17 | 1 | Current number of participants |
| 0x18 | 56 x 8 | [Participant](#participant-info) list |
| 0x1D8 | 2 | Unknown |
| 0x1DA | 2 | Beacon data size |
| 0x1DC | 384 | Beacon data |
| 0x35C | 420 | Unknown |

#### Participant Info
| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 4 | IP address |
| 0x4 | 6 | MAC address |
| 0xA | 1 | Is connected |
| 0xB | 0x2D | Unknown |

#### LDN Version
| System version | LDN version |
| --- | --- |
| 2.0.0 - 5.1.0 | 2 |
| 6.0.0 - 13.1.0 | 3 |

### Key Derivation
Given a 16-byte input key and an input buffer of arbitrary size, the LDN sysmodule derives encryption keys as follows:

1. `aes_kek_generation_source` is decrypted with master key generation 0.
2. The first 16 bytes of the SHA-256 hash of the input buffer are decrypted with the key from step 1.
3. The input key is decrypted with the key from step 2.
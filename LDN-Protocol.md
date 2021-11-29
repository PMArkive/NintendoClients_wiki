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
| 0x20 | 1 | Unknown |
| 0x21 | 1 | Encryption type (1=plain, 2=AES-CTR) |
| 0x22 | 2 | Advertisement data size |
| 0x24 | 4 | Unknown |
| 0x28 | 32 | SHA-256 hash, calculated over the whole decrypted advertisement frame with the hash set to zero |
| 0x48 | | [Advertisement data](#advertisement-data) |

If encryption is enabled, the SHA-256 hash and advertisement data are encrypted with AES-CTR. The input buffer for [key derivation](#key-derivation) is the [advertisement header](#advertisement-header), and the input key is `c3c078fa13206a7bf569d5194f83e199`.

#### Advertisement Header
| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 8 | Local communication id (usually the title id) |
| 0x8 | 2 | Always 0 |
| 0xA | 2 | Game mode (used for filtering) |
| 0xC | 4 | Padding (always 0) |
| 0x10 | 16 | Random bytes for key generation |

#### Advertisement Data

### Key Derivation
Given a 16-byte input key and an input buffer of arbitrary size, the LDN sysmodule derives encryption keys as follows:

1. The `aes_kek_generation_source` is decrypted with master key generation 0.
2. The first 16 bytes of the SHA-256 hash of the input buffer are decrypted with the key from step 1.
3. The input key is XORed with the LDN key mask, and the result is decrypted with the key from step 2.

The LDN key mask is: `dad8fc8e2d04ad0672af4b5b485325a1`
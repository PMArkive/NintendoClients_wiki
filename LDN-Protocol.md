[[Pia Overview]] > LDN Protocol
---

This page describes the protocol that is used to communicate with nearby consoles in LDN mode, which is the default mode for local multiplayer.

## Table of Contents
* [Overview](#overview)
* [LDN versions](#ldn-versions)
* [WLAN channels](#wlan-channels)
* [SSID](#ssid)
* [Authentication](#authentication)
* [Encryption keys](#encryption-keys)<br><br>
* [Advertisement frame](#advertisement-frame)
* [Authentication frame](#authentication-frame)

## Overview
LDN enables communication between nearby consoles. Because LDN operates at the data link layer, it requires a good understanding of the [IEEE 802.11 specification](https://ieeexplore.ieee.org/document/9363693).

The host of the session acts as an access point and broadcasts a vendor-specific [action frame](#advertisement-frame) every 100 milliseconds. To find nearby consoles, the console scans for these action frames. During host migration the network is destroyed and a new network is created by the new host, after which all consoles reconnect.

Also see: [[Local Wireless Communication on PC]].

## LDN Versions
| System version | LDN version | Changes |
| --- | --- | --- |
| 2.0.0 - 5.1.0 | 2 | Initial version |
| 6.0.0 - 13.2.1 | 3 | Authentication frame was updated |

## WLAN Channels
The channel on which LDN operates can be specified by games. Allowed channels are:

| Band | Channels |
| --- | --- |
| 2.4 GHz | 1, 6, 11 |
| 5 GHz | 36, 40, 44, 48 |

By default, LDN operates on one of the channels of the 2.4 GHz band (chosen arbitrarily).

During scanning, Nintendo uses a dwell time of 110 milliseconds.

## SSID
The SSID of the network contains 32 random hex digits. The network is hidden from other devices by zeroing the SSID in the beacon frame. To find the SSIDs of nearby networks, the console scans for [advertisement frames](#advertisement-frame).

## Authentication
When a suitable network has been found (by scanning for [advertisement frames](#advertisement-frame) on a given set of [channels](#wlan-channels)) the console may try to join the network, but Nintendo uses a custom authentication procedure:

1. The console joins the network using the open system authentication method. This is standard.
2. The console sends an encrypted [authentication request](#authentication-frame) to the access point. If the console does not send an authentication request within 5 seconds after step 1, the access point disassociates the console from the network.
3. The access point verifies the authentication request and sends an [authentication response](#authentication-frame) back to the console. If the console does not receive an authentication response from the access point within 700 milliseconds it reports an error.
4. The console verifies the authentication response. If it is valid, and indicates success, the console is now part of the network and may communicate with other consoles.

## Encryption Keys
LDN supports three different security levels:

1. Both advertisement frames and data frames are encrypted.
2. Advertisement frames are encrypted, data frames are plaintext.
3. Advertisement frames and data frames are both plaintext.

Given a 16-byte input key and a buffer of arbitrary size, encryption keys are derived as follows:

1. `aes_kek_generation_source` is decrypted with master key generation 0.
2. The input key is decrypted with the key from step 1.
3. `aes_key_generation_source` is decrypted with the key from step 2.
4. The first 16 bytes of the SHA-256 hash of the input buffer are decrypted with the key from step 3.

For data frames, the input key is `f1e7018419a84f711da714c2cf919c9c` and the input buffer looks as follows:

| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 16 | Network key (generated when the network is created) |
| 0x10 | N | Password specified by game (optional, up to 64 bytes) |

For advertisement frames, [see below](#advertisement-frame).

## Advertisement Frame
This is a vendor-specific action frame that is broadcasted by the access point every 100 milliseconds.

| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 1 | Category (127 = vendor-specific) |
| 0x1 | 3 | OUI (`00:22:AA`) |
| 0x4 | 1 | Protocol id (4 = LDN) |
| 0x5 | 1 | Padding (always 0) |
| 0x6 | 2 | Packet type (257 = advertisement) |
| 0x8 | 2 | Must be 0 |
| 0xA | 2 | Padding (always 0) |
| 0xC | | [Advertisement payload](#advertisement-payload) |

Everything is encoded in big-endian byte order.

### Advertisement Payload
| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 32 | [Session info](#session-info) |
| 0x20 | 1 | [LDN version](#ldn-versions) |
| 0x21 | 1 | Encryption type (1=plain, 2=AES-CTR) |
| 0x22 | 2 | Advertisement daa size |
| 0x24 | 4 | Nonce for AES-CTR algorithm |
| 0x28 | 32 | SHA-256 hash, calculated over the whole advertisement payload with the hash set to zero |
| 0x48 | | [Advertisement data](#advertisement-data) |

If encryption is enabled, the hash and advertisement data are encrypted with AES-CTR. The input buffer for [key derivation](#encryption-keys) is the [session info](#session-info), and the input key is `191884743e24c77d87c69e4207d0c438`.

### Advertisement Data
| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 16 | Network key |
| 0x10 | 2 | Security level |
| 0x12 | 1 | Station accept policy:<br>0 = Open participation<br>1 = Closed participation<br>2 = Blacklist (provided by game)<br>3 = Whitelist (provided by game) |
| 0x13 | 3 | Padding (always 0) |
| 0x16 | 1 | Maximum number of participants |
| 0x17 | 1 | Current number of participants |
| 0x18 | 56 x 8 | [Participant](#participant-info) list |
| 0x1D8 | 2 | Padding (always 0) |
| 0x1DA | 2 | Application data size |
| 0x1DC | 384 | Application data |
| 0x35C | 412 | Padding (always 0) |
| 0x4F8 | 8 | Authentication nonce (random) |

The authentication nonce was added in LDN version 3. In previous versions it is set to 0.

#### Participant Info
| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 4 | IP address |
| 0x4 | 6 | MAC address |
| 0xA | 1 | Is connected |
| 0xB | 1 | Padding (always 0) |
| 0xC | 32 | Username |
| 0x2C | 2 | Application communication version |
| 0x2E | 10 | Padding (always 0) |

## Authentication Frame
This is a data frame with ethertype 0x88B7 (OUI extended). It is usually [encrypted](#encryption-keys).

| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 3 | OUI (`00:22:AA`) |
| 0x3 | 2 | Packet type (258 = authentication) |
| 0x5 | 1 | Padding (always 0) |
| 0x6 | | [Authentication data](#authentication-data) |

### Authentication Data
| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 1 | [LDN version](#ldn-versions) |
| 0x1 | 1 | Payload size (`size & 0xFF`) |
| 0x2 | 1 | Status code |
| 0x3 | 1 | 0 = request, 1 = response |
| 0x4 | 1 | Payload size (`size >> 8`) |
| 0x5 | 3 | Padding (always 0) |
| 0x8 | 32 | [Session info](#session-info) |
| 0x28 | 16 | Network key |
| 0x38 | 16 | Authentication key (random bytes) |
| 0x48 | | Authentication payload ([request](#authentication-request) or [response](#authentication-response)) |

#### Authentication Request
| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 32 | Username |
| 0x20 | 2 | Application communication version |
| 0x22 | 30 | Padding (always 0) |

LDN version 3 and later:

| Offset | Size | Description |
| --- | --- | --- |
| 0x40 | 0x24 | Always 0 |
| 0x64 | 0x300 | [Authentication challenge](#challenge-request) (only present if enabled) |

For games, the authentication challenge is always enabled.

#### Authentication Response
LDN version 3 and later:

| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 0x84 | Unknown |
| 0x84 | 0x100 | [Challenge response](#challenge-response) (only present if enabled) |

#### Challenge Request
| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 4 | Unknown |
| 0x4 | 32 | HMAC-SHA256 |
| 0x24 | 20 | Unknown |
| 0x38 | 8 | Authentication nonce (generated at start of session) |
| 0x40 | 8 | Authentication nonce (random) |
| 0x48 | 8 | Device id |
| 0x50 | 0x2B0 | Unknown |

#### Challenge Response
| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 0x100 | Unknown |

## Session Info
| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 8 | Local communication id (usually the title id) |
| 0x8 | 2 | Padding (always 0) |
| 0xA | 2 | Game mode |
| 0xC | 4 | Padding (always 0) |
| 0x10 | 16 | SSID (random bytes) |
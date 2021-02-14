[[Pia Protocols]] > Monitoring Data Protocol
---

This protocol is used for the P2P monitoring server on the Switch. The messages are wrapped in unencrypted [Pia packets](Pia-Protocol) and sent to `g<game server id>-%.p.srv.nintendo.net` through UDP port 34343.

Wii U games send the monitoring data to the NEX server instead, through the [SendReport](Secure-Protocol#8-sendreport) method of the [secure connection protocol](Secure-Protocol).

The message payload is encoded as follows:

*Up to 5.6:*

| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 16 | [Monitoring data header](#monitoring-data-header) |
| 0x10 | | Payload, first zlib compressed, then encrypted with AES-ECB. The key is always: `901edf193dc5ef3c5290647bff20c385`. |

*5.7 and later:*

| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 16 | [Monitoring data header](#monitoring-data-header) |
| 0x10 | | Payload, first zlib compressed, then encrypted with AES-GCM. See [AES-GCM encryption](#aes-gcm-encryption) below. |
| | | AES-GCM authentication tag |

The content of the payload depends on the version number and data type in the monitoring data header.

| Data Type | Payload content |
| --- | --- |
| 0 | [Session begin monitoring content](#session-begin-monitoring-content) |
| 1 | [Session end monitoring data](#session-end-monitoring-data) |
| 2 | [Session end monitoring data](#session-end-monitoring-data) |

## AES-GCM Encryption
The key is chosen by the lower nybble of the encryption key id in the monitoring data header:

```
 0: c1d494af4a0a956c545d2e41fc1ceb24
 1: caf247fb40aa9655e58c2b02bff89e14
 2: bc6da24db8c7e22d2e3fdd97a2b5e3d2
 3: 3ef3a41d8a2e78518974679562afe5fa
 4: c0a02f90a2642ea6a64b199e01f46a57
 5: 9eb9c98fc889495c7056f2cd8015aac0
 6: 632acbe8c6c77246475b577b6b2d8c76
 7: 8dafd0578b2d3ff285e0292ce08d25a2
 8: cc082ad011d3c38c7b5ed28637f37c1c
 9: 6cd46046c71362116e36cb96c0098912
10: 54598618dc2a24474a9d5e80f783a145
11: f35eaa5cc8ebc1dc42ada6c3f4130556
12: 127d237973e98688548b5dac5eb6cc7b
13: f677ccf32241122aeeece3df23aaa736
14: d7cb0683d251030fc7613b4b2461224b
15: c587a79cbac8a2ddcee27409242a8702
```

The nonce is constructed as follows:

| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 8 | Nonce from monitoring data header |
| 0x8 | 4 | Always `5bd085fa` |

## Version Number
Monitoring was added to Pia in version 3.4.

| Pia version | Monitoring version |
| --- | --- |
| 3.4 | 1 |
| 3.5 | 2 |
| 3.6 | 3 |
| 3.7 | 4 |
| 3.8 | 5 |
| 3.9 | 6 |
| 3.10 | 7 |
| 4.5 | 9 |
| 4.6 | 10 |
| 4.9 | 11 |
| 4.10 | 12 |
| 5.2 - 5.4 | 15 |
| 5.5 | 16 |
| 5.6 | 17 |
| 5.7 - 5.9 | 18 |
| 5.10 - 5.12 | 19 |
| 5.14 | 20 |
| 5.17 - 5.19 | 22 |
| 5.20 | 23 |
| 5.21 - 5.31 | 24 |

## Monitoring Data Header
As described above, the message payload starts with a monitoring data header. Each monitoring data structure starts with a monitoring data header as well. The flags field is always 0xFC in the first monitoring data header, and 0xFF in all other monitoring data headers.

In the first monitoring data header, the payload size indicates the size of the compressed payload. In all other monitoring data headers, the payload size indicates the size of the structure, including the monitoring data header itself.

| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 1 | [Version number](#version-number) |
| 0x1 | 1 | Data type |
| 0x2 | 1 | Flags |
| 0x3 | 1 | Always 0xFF |
| 0x4 | 2 | Payload size |

*Up to 5.6:*
| Offset | Size | Description |
| --- | --- | --- |
| 0x6 | 10 | Padding (filled with 0xFF) |

*5.7 and later:*

This part is only relevant in the first monitoring data header. In all other monitoring data headers, it is filled with 0xFF.

| Offset | Size | Description |
| --- | --- | --- |
| 0x6 | 8 | AES-GCM nonce (random number) |
| 0xE | 1 | Encryption key id (random number) |
| 0xF | 1 | Always 0xFF |

## Session Begin Monitoring Content
All fields are initialized to 0xFF.

Version 18:

| Type | Description |
| --- | --- |
| [MonitoringDataHeader](#monitoring-data-header) | Monitoring data header |
| Uint32 | Pia version |
| Uint32 | SDK version |
| Uint32 | NEX version |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Platform id (3=Wii U, 4=Switch) |
| Uint8 | Language |
| Uint8 | Unknown |
| Uint32 | Pia heap size |
| Uint32 | Bitmask that describes which [protocols](Pia-Protocols) are created. |
| Uint64 | Unknown |
| Uint8 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint16 | Unknown |
| Uint16 | Unknown |
| Uint16 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint8 | Unknown |
| Uint16 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint16 | Unknown |
| Uint32 | Unknown |
| Uint16 | Unknown |
| Uint32 | Unknown |
| Uint16 | Relay route rtt max |
| Uint16 | Relay route num max |
| Uint16 | Unknown |
| Uint32 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint8 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint8 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint16 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint32 | Unknown |
| Uint16 | Unknown |
| Uint16 | Unknown |
| Uint16 | Unknown |
| Uint16 | Unknown |
| Uint16 | Unknown |
| Uint16 | Unknown |
| Uint16 | Unknown |
| Uint16 | Unknown |
| Uint8 | Unknown |
| Uint16 | Unknown |
| Uint16 | Unknown |
| Uint16 | Unknown |
| Uint8 | Unknown |
| Uint32 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint16 | Unknown |
| Uint32 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint32 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint16 | Unknown |
| Uint16 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint16 | Unknown |
| Uint16 | Unknown |
| Uint32[75] | Unknown |
| Uint8[62] | Unknown |
| Uint16 | Unknown |
| Uint16 | Unknown |
| Uint16 | Unknown |
| Uint16 | Unknown |
| Uint16 | Unknown |
| Uint8[15] | Unknown |
| Uint32 | Unknown |
| Uint16 | Unknown |
| Uint8[67] | Unknown |
| Uint8[150] | Unknown |
| Uint8[150] | Unknown |
| Uint8[32] | Unknown |
| Uint8[150] | Unknown |
| Uint8[176] | Unknown |
| Uint8[300] | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint8 | Unknown |
| Uint32 | Always `PiaM` |

## Session End Monitoring Data
| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 16 | [Monitoring data header](#monitoring-data-header) |
| ... | ... | ... |
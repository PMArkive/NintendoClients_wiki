[[Pia Protocols]] > Monitoring Data Protocol
---

This protocol is used for the P2P monitoring server on the Switch. The messages wrapped in unencrypted [Pia packets](Pia-Protocol) and sent to `g<game server id>-%.p.srv.nintendo.net` through UDP port 34343.

Wii U games send the monitoring data to the NEX server instead, through the [SendReport](https://github.com/kinnay/NintendoClients/wiki/Secure-Protocol#8-sendreport) method of the [secure connection protocol](https://github.com/kinnay/NintendoClients/wiki/Secure-Protocol).

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

## AES-GCM Encryption
The key is chosen based on the lower nybble of the encryption key id in the monitoring data header:

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

## Monitoring Data Header
| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 1 | Version number |
| 0x1 | 1 | Data type |
| 0x2 | 1 | Unknown |
| 0x3 | 1 | Always 0xFF |
| 0x4 | 2 | Payload size |

*Up to 5.6:*
| Offset | Size | Description |
| --- | --- | --- |
| 0x6 | 10 | Padding (filled with 0xFF) |

*5.7 and later:*
| Offset | Size | Description |
| --- | --- | --- |
| 0x6 | 8 | AES-GCM nonce |
| 0xE | 1 | Encryption key id (chosen randomly) |
| 0xF | 1 | Unknown |
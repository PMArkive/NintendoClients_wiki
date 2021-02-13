[[Pia Protocols]] > Monitoring Data Protocol
---

This protocol is used for the P2P monitoring server. The messages encapsulated in unencrypted [Pia packets](Pia-Protocol).

The server is at `g<game server id>-%.p.srv.nintendo.net`, port 34343.

The message payload is encoded as follows:

| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 16 | [Monitoring data header](#monitoring-data-header) |

## Monitoring Data Header
| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 1 | Unknown |
| 0x1 | 1 | Unknown |
| 0x2 | 1 | Unknown |
| 0x3 | 1 | Unknown |
| 0x4 | 2 | Unknown |
| 0x6 | 1 | Unknown |
| 0x7 | 1 | Unknown |
| 0x8 | 1 | Unknown |
| 0x9 | 1 | Unknown |
| 0xA | 1 | Unknown |
| 0xB | 1 | Unknown |
| 0xC | 1 | Unknown |
| 0xD | 1 | Unknown |
| 0xE | 1 | Unknown |
| 0xF | 1 | Unknown |
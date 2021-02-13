[[Pia Protocols]] > Monitoring Data Protocol
---

This protocol is used for the P2P monitoring server. The messages encapsulated in unencrypted [Pia packets](Pia-Protocol).

The server is at `g<game server id>-%.p.srv.nintendo.net`, port 34343.

The message payload is encoded as follows:

| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 16 | [MonitoringDataHeader](#monitoringdataheader) |

## MonitoringDataHeader
| Offset | Size | Description |
| --- | --- | --- |
| 0x0 | 1 | Unknown |
| 0x0 | 1 | Unknown |
| 0x0 | 1 | Unknown |
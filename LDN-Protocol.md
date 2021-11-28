This page describes the protocol that is used to communicate with nearby consoles in LDN mode, which is the default mode for local multiplayer.

Because LDN operates at the data link layer, it requires a good understanding of the [IEEE 802.11 specification](https://ieeexplore.ieee.org/document/9363693).

The host of the session broadcasts a custom action frame every 100 milliseconds. To find nearby consoles, the console scans for these action frames.

Also see: [[Local Wireless Communication on PC]].

### Action Frame Format
Defined by IEEE 802.11 specification:

| Offset | Size | Description | Value |
| --- | --- | --- | --- |
| 0x0 | 1 | Category | 127 (vendor-specific) |
| 0x1 | 3 | OUI | `00:22:AA` (Nintendo) |

Nintendo-specific action frame format:

| Offset | Size | Description | Value |
| --- | --- | --- | --- |
| 0x4 | 1 | Protocol id | 4 (LDN) |
| 0x5 | 1 | Padding | Always 0 |
| 0x6 | 2 | Packet type | 257 (advertisement) |
| 0x8 | | Advertisement frame | |

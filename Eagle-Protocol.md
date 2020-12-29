[[Server List]] > Eagle (relay servers)
---

Unlike most multiplayer games, Tetris 99 and Super Mario Bros. 35 use a relay server instead of [Pia](PIA-Overview), which seems to be called eagle. Match making is still done with [NEX](NEX-Overview-(Game-Servers)), but when the session is ready, the server sends a [notification event](#notification-event) to the clients, which contains the url of the eagle server and a token.

* [Notification Event](#notification-event)
* [Server URL](#server-url)
* [Token Format](#token-format)
* [Packet Format](#packet-format)

## Notification Event
When a [matchmake session](Matchmake-Extension-Protocol) is created, the server spawns a Kurbernetes instance that runs the eagle server. When the eagle server is ready, the NEX server sends a [notification event](Notification-Protocol) to everyone in the matchmake session. The notification event has the following fields set:

| Field | Description |
| --- | --- |
| m_pidSource | 257049437023956657 (Quazal Rendez-Vous) |
| m_uiType | 200000 |
| m_uiParam1 | The gathering id |
| m_mapParam | See table below |

Map param:

| Field | Description |
| --- | --- |
| `url` | The url of the eagle server |
| `token` | Base64 encoded token |

## Server URL
The URL is written as follows: `<scheme>://<host>:<port>/<path>`.

The scheme must be either `kdp` (see https://github.com/skywind3000/kcp), `tcp`, `tcps`, `ws` or `wss`.

The port is optional and defaults to 443 if the connection is secured with TLS (`tcps` or `wss`) or 30000 if the connection is not secured with TLS. The path is only required on WebSocket connections (`ws` or `wss`). If TCP is used (`tcp` or `tcps`) packets are prefixed by a 16-bit little-endian integer that indicates the size of the packet.

The real server always uses the following URL: `wss://<server name>.g.<server env>.e.srv.nintendo.net:443/<game id>/ess-d7d-<server id>`. Sometimes, the suffix `-b` or `-g` is added to the server name.

| Game | Server Name | Game ID |
| --- | --- | --- |
| Tetris 99 | `d7d-arzn` | `EA3nJiq9BKyoxmBjJ2TkfzcRHwQe88FJ` |
| Super Mario Bros. 35 | `d7d-ayam` | `EGrCObHITxTtIa3O1A01uw2WHSEypGYb` |

Example: `wss://d7d-arzn.g.lp1.e.srv.nintendo.net:443/EA3nJiq9BKyoxmBjJ2TkfzcRHwQe88FJ/ess-d7d-btb4mnggg9q5k2kdqb8g`

## Token Format
The token is a base64-encoded JSON object that contains the following fields:

| Field | Description |
| --- | --- |
| payload | Payload. See below. |
| signature | Base64-encoded signature (32 bytes) |
| version | Always 1 |

The payload has the following fields:

| Field | Description |
| --- | --- |
| expires_at | Timestamp in seconds (string) |
| server_env | Server environment (e.g. `lp1`) |
| server_id | A string of 20 lowercase alphanumeric characters. |
| user_id | Your pid (hex string) |

If the server name has the suffix `-b` or `-g`, the server id is given the suffix `-blue` or `-green` respectively.

## Packet Format
Packets are encoded as a stream of bits. Each packet starts with the following header:

| Bits | Description |
| --- | --- |
| 2 | Relay type |
| 8 | Payload id |
| [N](#library-versions) | Source node id |

The remainder of the packet depends on the relay type and payload id.

| Type | Description |
| --- | --- |
| 0 | No relay. |
| 1 | This packet is relayed to a single node. The header is followed by [N](#library-versions) bits that hold the destination node id. |
| 2 | This packet is relayed to multiple nodes. The header is followed by [M](#library-versions) bits that hold the destination nodes (one bit per node). |

The payload comes after header and relay destination, but the bit stream is first aligned to 8 bits before the payload starts.

| Payload ID | Description |
| --- | --- |
| 0 | [Connection accepted](#connection-accepted) |
| 1 | [Login request](#login-request) |
| 2 | [Login result](#login-result) |
| 3 | Client ready |
| 4 | Unknown |
| 5 | Unknown |
| 6 | Unknown |
| 7 | Unknown |
| 8 | Unknown |
| 9 | Unknown |

### Connection Accepted
The server time is monotonic clock (no timestamp).

| Bits | Description |
| --- | --- |
| 16 | Node id |
| 64 | Server time (in milliseconds) |

### Login Request
| Bits | Description |
| --- | --- |
| 7 | Login phase (0 or 1) |
| 1 | Last packet |

Login phase 0:
| Bits | Description |
| --- | --- |
| 8 | Unknown |
| 32 | Protocol version |
| 64 | App protocol version |
| 32 | DDL hash |
| 8 | Version string size (max 63 bytes) |
| | Version string |

Login phase 1:
| Bits | Description |
| --- | --- |
| 8 | Token string size |
| | Token string |

### Login Result
| Bits | Description |
| --- | --- |
| 32 | Unknown |
| 8 | Unknown |
| 16 | Payload size |
| | Payload |

## Library Versions
The eagle library was rewritten almost completely between Tetris 99 and Super Mario Bros 35.

| Game | N | M |
| --- | --- | --- |
| Tetris 99 | 9 | 128 |
| Super Mario Bros 35 | 11 | 1024 |

| Game | Version string |
| --- | --- |
| Tetris 99 | release/1.2.14 |
| Super Mario Bros 35 | 2.0.4 |
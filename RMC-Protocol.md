This is a simple remote method call protocol that lies on top of the [[PRUDP protocol]].

## Request Format
| Type | Description |
| --- | --- |
| Uint32 | Size, excluding this field |
| Uint8 | [Protocol id](NEX-Protocols), ORed with 0x80 |
| Uint16 | Extended protocol id. **Only present if the protocol id is 0x7F.** |
| Uint32 | Call id, an incrementing number used to match a response to the right request |
| Uint32 | Method id |
| ... | Method parameters |

## Response Format
| Type | Description |
| --- | --- |
| Uint32 | Size, excluding this field |
| Uint8 | [Protocol id](NEX-Protocols) |
| Uint16 | Extended protocol id. **Only present if the protocol id is 0x7F.** |
| Uint8 | 0=Error 1=Success |

**On success:**

| Type | Description |
| --- | --- |
| Uint32 | Call id |
| Uint32 | Method id, ORed with 0x8000 |
| ... | Response data |

**On error:**

| Type | Description |
| --- | --- |
| Uint32 | Error code, see [errors.py](https://github.com/Kinnay/NintendoClients/blob/master/nintendo/nex/errors.py) |
| Uint32 | Call id |

## Remarks
The following services never send an RMC response, even if an error occurred:

* [[Notification Protocol]]
* [[Nintendo Notification Event Protocol]]
* [[Message Delivery Protocol]]

Other services always send an RMC response.
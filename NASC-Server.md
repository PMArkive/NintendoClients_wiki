[[Server List]] > NASC Server
---

This is the account server of the 3DS. A single endpoint (`ac`) is used for all requests. Other requests are redirected to http://www.nintendo.com.

* [General](#general)
* [Headers](#headers)
* [Actions](#actions)
* [Errors](#errors)
* [Examples](#examples)

## General

Main server: https://nasc.nintendowifi.net/ac

Other servers:
* https://nasc.test.nintendowifi.net/ac
* https://nasc.dev.nintendowifi.net/ac

The common client certificate (`ctr-common-1`) is required to access these servers. If it is not provided, the server rejects the TLS handshake.

## Headers

| Header | Description |
| --- | --- |
| Host | `nasc.nintendowifi.net` |
| X-GameId | The current game id (`%08X`) |
| User-Agent | `CTR FPD/000F` |
| Content-Type | `application/x-www-form-urlencoded` |
| Content-Type | `application/x-www-form-urlencoded` |
| Content-Length | Content length |

Note that the Content-Type header is included twice.

## Actions
All form values are encoded with a custom base64 character set, where `+/=` are replaced by `.-*` respectively. This applies to both the request and the response.

The type of request is specified by the `action` parameter. Other parameters depend on the type of action. The action name in case insensitive.

* [LOGIN](#login)
* SVCLOC
* nzchk
* parse
* message

### LOGIN
This action provides the location of the game server and a token.

| Param | Description |
| --- | --- |
| `gameid` | Game server id (`%08X`). This is the same as the `X-GameId` header. |
| `sdkver` | Major and minor SDK version (`%03d%03d`). Always `000000`. |
| `titleid` | Title id (`%016X`) |
| `gamecd` | Product code, e.g. `AMKP` for Mario Kart 7 |
| `gamever` | Title version (`%04X`) |
| `mediatype` | 0=System, 1=Digital, 2=Cartridge |
| `romid` | Rom id, only present if the media type is 2 |
| `makercd` | Product maker code (company code) |
| `unitcd` | Always 2 |
| `macadr` | MAC address of the 3DS |
| `bssid` | BSSID of active wifi network |
| `apinfo` | Not sure, looks like `01:0000000000` |
| `fcdcert` | Device certificate |
| `devname` | Device name (UTF-16-LE) |
| `servertype` | Environment (`L1` for production) |
| `fpdver` | FPD version. Always `000F`, this is also included in the user agent. |
| `devtime` | Current device time (`%y%m%d%H%M%S`) |
| `lang` | Language code (`%02X`) |
| `region` | Region code (`%02X`) |
| `csnum` | Serial number |

Then, either:

| Param | Description |
| --- | --- |
| `uidhmac` | PID HMAC, received during [account creation](https://github.com/kinnay/NintendoClients/wiki/Account-Management-Protocol#27-nintendocreateaccount)) |
| `userid` | PID, received during [account creation](https://github.com/kinnay/NintendoClients/wiki/Account-Management-Protocol#27-nintendocreateaccount)) |

or:

| Param | Description |
| --- | --- |
| `passwd` | Unknown, the server seems to accept anything |

Finally, the following parameters are always present:

| Param | Description |
| --- | --- |
| `action` | `LOGIN` |
| `ingamesn` | Unknown (empty string in my traffic dumps) |

On success, the server sends the following response:

| Field | Description |
| --- | --- |
| `locator` | Host and port of game server |
| `retry` | Always 0 |
| `returncd` | Always `001` (success) |
| `token` | Token for logging in on game server |
| `datetime` | Current server time (`%Y%m%d%H%M%S`) |

## Errors
On error, the server sends the following response:

| Field | Description |
| --- | --- |
| `retry` | 0 or 1 |
| `returncd` | Error code (see below) |
| `datetime` | Current server time (`%Y%m%d%H%M%S`) |

### Known Errors
| Code | Description |
| --- | --- |
| `001` | Success |
| `109` | Missing or malformed parameter in request |
| `110` | Game server is no longer available |
| `121` | Device certificate is invalid |
| `122` | PID HMAC is invalid |
| `125` | Game id is invalid |

## Examples
Example error response:

```http
HTTP/1.1 200 OK
NODE: pd42wfiap01
Content-Type: text/plain;charset=ISO-8859-1
Content-Length: 56
Date: Wed, 19 Jan 2022 09:21:41 GMT
Server: Nintendo Wii (http)

retry=MA**&returncd=MDA5&datetime=MjAyMjAxMTkwOTIxNDE*
```

Redirect to http://www.nintendo.com

```http
HTTP/1.0 302 Moved Temporarily
Location: http://www.nintendo.com
Server: BigIP
Connection: Keep-Alive
Content-Length: 0
```
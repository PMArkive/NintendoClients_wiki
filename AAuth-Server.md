[[Server List]] > AAuth Server
---

URL: https://aauth-lp1.ndas.srv.nintendo.net

The aauth server provides application authorization tokens. These are required to access game-specific servers, such as [NEX](NEX-Overview-(Game-Servers)).

The aauth server takes form-encoded requests and responds with json-encoding. It uses base64url, and the client does not add any padding characters.

* [Headers](#headers)
* [Methods](#methods)
* [Errors](#errors)
* [Examples](#examples)

## Headers
| Header | Description |
| --- | --- |
| Host | `aauth-lp1.ndas.srv.nintendo.net` |
| User-Agent | [User agent](#user-agents) |
| Accept | `*/*` |
| X-Nintendo-PowerState | `FA` (fully awake) or `HA` (half awake). This header is only sent in the <code><a href="#post-v3application_auth_token">/v3/application_auth_token</a></code> request. |
| Content-Length | Content length |
| Content-Type | `application/x-www-form-urlencoded` |

#### User Agents
| System Version | User agent |
| --- | --- |
| 9.0.0 - 9.2.0 | `libcurl (nnAccount; 789f928b-138e-4b2f-afeb-1acae821d897; SDK 9.3.0.0; Add-on 9.3.0.0)` |
| 10.0.0 - 10.2.0 | `libcurl (nnAccount; 789f928b-138e-4b2f-afeb-1acae821d897; SDK 10.4.0.0; Add-on 10.4.0.0)` |
| 11.0.0 - 11.0.1 | `libcurl (nnHttp; 789f928b-138e-4b2f-afeb-1acae821d897; SDK 11.4.0.0; Add-on 11.4.0.0)` |
| 12.0.0 - 12.1.0 | `libcurl (nnHttp; 789f928b-138e-4b2f-afeb-1acae821d897; SDK 12.3.0.0; Add-on 12.3.0.0)` |
| 13.0.0 | `libcurl (nnHttp; 789f928b-138e-4b2f-afeb-1acae821d897; SDK 13.3.0.0; Add-on 13.3.0.0)` |

## Methods
| Method | URL |
| --- | --- |
| GET | <code><a href="#post-v1admin">/v1/time</a></code> |
| POST | <code><a href="#post-v3challenge">/v3/challenge</a></code> |
| POST | <code><a href="#post-v3application_auth_token">/v3/application_auth_token</a></code> |

### GET /v1/time
This method is unrelated to aauth. It returns a `text/plain` document that contains two lines:
1. The current server time in milliseconds
2. The external IP address of the client

It also returns this information in the `X-NINTENDO-UNIXTIME` and `X-NINTENDO-GLOBAL-IP` headers.

### POST /v3/challenge
This request is only required if the media type is `GAMECARD`.

| Param | Description |
| --- | --- |
| &device_auth_token | Device token from [dauth server](DAuth-Server) |

Note that the device_auth_token parameter is preceded by an ampersand, even though it is the first and only parameter in the request.

Response on success:

| Field | Description |
| --- | --- |
| value | Base64-encoded (16 bytes) |
| seed | Base64-encoded (15 bytes) |

### POST /v3/application_auth_token
The following parameters are always present:

| Param | Description |
| --- | --- |
| application_id | Title id (`%016x`) |
| application_version | Title version (`%08x`) |
| device_auth_token | Device token from [dauth server](DAuth-Server) |
| media_type | `GAMECARD`, `DIGITAL`, `SYSTEM` or `NO_CERT` |

The following parameters depend on the media type of the game:

#### GAMECARD
| Param | Description |
| --- | --- |
| gvt | Base64-encoded challenge reply, based on the seed and value from <code><a href="#post-v3challenge">/v3/challenge</a></code> (88 bytes) |
| cert | Base64-encoded gamecard certificate (stored on game card itself) |

#### DIGITAL
The certificate is read from ES save data (`escommon` or `espersonalized`). First the index of the ticket is looked up in `ticket_list.bin` by rights id. Then the certificate itself is read from `ticket.bin`.

The ticket is not sent to the server in plain text. Instead, it is encrypted with AES-CBC with a random key. The key itself is then encrypted with RSA-OAEP with SHA256.

| Param | Description |
| --- | --- |
| cert | Encrypted certificate (base64) |
| cert_key | Encrypted key (base64) |

Public exponent: `65537`

Public modulus:
```
2903599220185509629948246004681271806662185201109683699434876284
9306378942456577312580648895443616535088601867223713942187399041
4854872772034425863387471719375473684104853507768450203982749294
8967945831738920699512732919046223059402955082098739033920491649
6879108565068863591362496844602988110766097564477545097467537357
3183749964356608012071405755940871989007021731074728723470759285
8155278592486462922448753256166071381157786436864032235809243318
2591089355065715995209202752330511548478896205428626608544326862
4782505679727111312756904637828438785474471375120478991907979820
98870089661523253199182993983393803812441
```

#### Response on success:

| Field | Description |
| --- | --- |
| expires_in | Expiration in seconds (86400) |
| application_auth_token | Application authorization token |
| settings | Unknown (list) |
| online_play_policy | `MEMBERSHIP_REQUIRED` or `FREE` |
| policy_handler | `SYSTEM` or `GAME_SERVER` |

## Errors
On error, the server sends the following response:

| Field | Description |
| --- | --- |
| errors | List of errors |

Every error is encoded like this:

| Field | Description |
| --- | --- |
| code | Error code (string with 4 digits) |
| message | Error message |

### Known Errors
| Code | Dialog | Message |
| --- | --- | --- |
| 0103 | 2124-4603 | ? |
| 0105 | 2124-4605 | ROM ID has been banned. |
| 0106 | 2124-4606 | ? |
| 0107 | 2124-4607 | ? |
| 0108 | 2124-4608 | ? |
| 0109 | 2124-4609 | Service closed. |
| 0110 | 2124-4610 | ? |
| 0111 | 2124-3001 | Application update is required. |
| 0112 | 2124-4612 | ? |
| 0113 | 2124-4613 | ? |
| 0118 | 2124-4618 | Invalid parameter in request. |
| 0120 | 2124-4620 | ? |
| 0121 | 2124-4621 | ? |

## Examples
The `/v1/time` request is very simple:

```http
GET /v1/time HTTP/1.1
Host: aauth-lp1.ndas.srv.nintendo.net
Accept: */*
```

Example of `/v1/time` response:

```http
HTTP/1.1 200 OK
Server: nginx
Date: Thu, 30 Sep 2021 14:02:21 GMT
Content-Type: text/plain; charset=utf-8
Transfer-Encoding: chunked
Connection: keep-alive
...
X-NINTENDO-UNIXTIME: 1633003341066
X-NINTENDO-GLOBAL-IP: 93.184.216.34
...
X-Nintendo-Used-Directive: global auth
X-Nintendo-Request-Host-Header: aauth-lp1.ndas.srv.nintendo.net
X-Nintendo-Request-SNI: aauth-lp1.ndas.srv.nintendo.net

1633003341066
93.184.216.34
```

To authenticate game cards one must first obtain a challenge:

```http
POST /v3/challenge HTTP/1.1
Host: aauth-lp1.ndas.srv.nintendo.net
User-Agent: libcurl (nnHttp; 789f928b-138e-4b2f-afeb-1acae821d897; SDK 13.3.0.0; Add-on 13.3.0.0)
Accept: */*
Content-Length: 857
Content-Type: application/x-www-form-urlencoded

&device_auth_token=eyJqa3UiOiJodHRwczovL2RjZXJ0LWxwMS5uZGFzLnNydi5uaW50ZW5kby5uZXQva2V5cyIsImtpZCI6IjM2NzllMTg4LTI5ZWUtNDE4Zi04ZDkwLWI3MjRjYzg1MzQ0MSIsInR5cCI6IkpXVCIsImFsZyI6IlJTMjU2In0.eyJzdWIiOiI2ODMzN2FjYTI4ODE1Y2JiIiwiaXNzIjoiZGF1dGgtbHAxLm5kYXMuc3J2Lm5pbnRlbmRvLm5ldCIsImF1ZCI6IjhmODQ5YjVkMzQ3NzhkOGUiLCJleHAiOjE2MzI3NjMzMDEsImlhdCI6MTYzMjY3NjkwMSwianRpIjoiZTU5YTBiMGUtOTRlMS00NGFhLWI1ZGItMGZjMGNmNTAyYWRhIiwibmludGVuZG8iOnsic24iOiJYQVcxMDAxMjM0NTY3OCIsInBjIjoiSEFDIiwiZHQiOiJOWCBQcm9kIDEiLCJpc3QiOmZhbHNlfX0.Mdl42B_tWnQQZkpp0qkvEwpkAFGos1YQ8OBKDr_rJCQlNVZLrP6_sd53U8kvwI6TWbnuxFtNxcVJh21kbbY23WsjwQN9Ph2pbjEmneov5b5SfAjWSvfEqt_ViKFQVLv_MZZXQpBYZSQmJ3sA-BbOjeEO6JI5XI3_KR0uj9IxSH_LNSiEwMMNLkP0PcC3gO5cSKcmnb1NPW2BMMdlKOSIbxDSWE4sEuYt2Pl_u2F6hVMVeoC-4z43lIv2tv7aF9Pwv-D7MR-mOxQaxYVHw2Ux4FL0zPZOJMU6qPgfzACeItd6H_A4OBMKSQwBl4DEbSwdle5tph-ur01K91FhXhI6BA
```

```http
HTTP/1.1 200 OK
Server: nginx
Date: Sun, 26 Sep 2021 19:21:50 GMT
Content-Type: application/json; charset=utf-8
Transfer-Encoding: chunked
...
X-Nintendo-Used-Directive: global auth
X-Nintendo-Request-Host-Header: aauth-lp1.ndas.srv.nintendo.net
X-Nintendo-Request-SNI: aauth-lp1.ndas.srv.nintendo.net
Connection: keep-alive

{"value":"XLYSEWCMMwSUlU4wJC3VBA==","seed":"wLJ0JZCC3cu5KSU8bLbe"}
```
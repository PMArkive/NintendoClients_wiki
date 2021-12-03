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
| 13.1.0 - 13.2.0 | `libcurl (nnHttp; 789f928b-138e-4b2f-afeb-1acae821d897; SDK 13.4.0.0; Add-on 13.4.0.0)` |

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
| media_type | <code><a href="gamecard">GAMECARD</a></code>, <code><a href="#digital">DIGITAL</a></code>, <code><a href="#system">SYSTEM</a></code> or <code><a href="#no_cert">NO_CERT</a></code> |

Depending on the media type, additional parameters may be included in the request (see below).

Response on success:

| Field | Description |
| --- | --- |
| expires_in | Expiration in seconds (86400) |
| application_auth_token | Application token |
| settings | Settings (see below) |
| online_play_policy | `MEMBERSHIP_REQUIRED` or `FREE` |
| policy_handler | `SYSTEM` or `GAME_SERVER` |

The settings field contains a list of objects with the following fields:

| Field | Description |
| --- | --- |
| nas:client_id | Unknown |
| nas:redirect_uri | Unknown |

The purpose of these fields is unknown. I have only seen an empty list so far.

#### GAMECARD
Certificates can be dumped with [nxdumptool](https://github.com/DarkMatterCore/nxdumptool).

| Param | Description |
| --- | --- |
| gvt | Base64-encoded challenge reply, based on the seed and value from <code><a href="#post-v3challenge">/v3/challenge</a></code> (88 bytes) |
| cert | Base64-encoded gamecard certificate (512 bytes) |

The `gvt` parameter is calculated with <code><a href="https://switchbrew.org/wiki/Lotus3#ChallengeCardExistence">ChallengeCardExistence</a></code>. I have no idea how this works.

#### DIGITAL
Tickets can be dumped with [nxdumptool](https://github.com/DarkMatterCore/nxdumptool). Always dump the base ticket, and do not remove console specific data.

The ticket is not sent to the server in plain text. Instead, it is encrypted with AES-CBC with a random key. The key itself is then encrypted with RSA-OAEP with SHA256.

| Param | Description |
| --- | --- |
| cert | Encrypted ticket (base64) |
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

#### SYSTEM
This media type is used for system titles. It does not include any additional parameters.

#### NO_CERT
This media type is used if the Switch does not have a valid ticket for a digital title. This can only happen if the title was installed through unofficial means, which is usually a piracy attempt. Using `NO_CERT` will ban your device.

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
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
X-NINTENDO-UNIXTIME: 1633003341066
X-NINTENDO-GLOBAL-IP: 93.184.216.34
Vary: Accept
ETag: W/"7c7283f8b06feb54a9d29b679a4ca0af"
Cache-Control: max-age=0, private, must-revalidate
X-RequestId: 297b792a-f6f2-456b-a3ca-66c6e73620b7
X-Runtime: 0.000683
X-Nintendo-Used-Directive: global auth
X-Nintendo-Request-Host-Header: aauth-lp1.ndas.srv.nintendo.net
X-Nintendo-Request-SNI: aauth-lp1.ndas.srv.nintendo.net

1633003341066
93.184.216.34
```

To authenticate gamecards one must first obtain a challenge:

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
Date: Sun, 26 Sep 2021 19:21:43 GMT
Content-Type: application/json; charset=utf-8
Transfer-Encoding: chunked
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Vary: Accept
ETag: W/"eff6fe99a35dd733bdb7e43956f9db16"
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b782a5a4-739a-47d6-b061-aa2cbfa4bea2
X-Runtime: 0.005265
X-Nintendo-Used-Directive: global auth
X-Nintendo-Request-Host-Header: aauth-lp1.ndas.srv.nintendo.net
X-Nintendo-Request-SNI: aauth-lp1.ndas.srv.nintendo.net
Connection: keep-alive

{"value":"XLYSEWCMMwSUlU4wJC3VBA==","seed":"wLJ0JZCC3cu5KSU8bLbe"}
```

Then one can obtain an application token for a gamecard:

```http
POST /v3/application_auth_token HTTP/1.1
Host: aauth-lp1.ndas.srv.nintendo.net
User-Agent: libcurl (nnHttp; 789f928b-138e-4b2f-afeb-1acae821d897; SDK 13.3.0.0; Add-on 13.3.0.0)
Accept: */*
X-Nintendo-PowerState: FA
Content-Length: 1749
Content-Type: application/x-www-form-urlencoded
Expect: 100-continue

application_id=0100abf008968000&application_version=00070000&device_auth_token=eyJqa3UiOiJodHRwczovL2RjZXJ0LWxwMS5uZGFzLnNydi5uaW50ZW5kby5uZXQva2V5cyIsImtpZCI6IjM2NzllMTg4LTI5ZWUtNDE4Zi04ZDkwLWI3MjRjYzg1MzQ0MSIsInR5cCI6IkpXVCIsImFsZyI6IlJTMjU2In0.eyJzdWIiOiI2ODMzN2FjYTI4ODE1Y2JiIiwiaXNzIjoiZGF1dGgtbHAxLm5kYXMuc3J2Lm5pbnRlbmRvLm5ldCIsImF1ZCI6IjhmODQ5YjVkMzQ3NzhkOGUiLCJleHAiOjE2MzI3NjMzMDEsImlhdCI6MTYzMjY3NjkwMSwianRpIjoiZTU5YTBiMGUtOTRlMS00NGFhLWI1ZGItMGZjMGNmNTAyYWRhIiwibmludGVuZG8iOnsic24iOiJYQVcxMDAxMjM0NTY3OCIsInBjIjoiSEFDIiwiZHQiOiJOWCBQcm9kIDEiLCJpc3QiOmZhbHNlfX0.Mdl42B_tWnQQZkpp0qkvEwpkAFGos1YQ8OBKDr_rJCQlNVZLrP6_sd53U8kvwI6TWbnuxFtNxcVJh21kbbY23WsjwQN9Ph2pbjEmneov5b5SfAjWSvfEqt_ViKFQVLv_MZZXQpBYZSQmJ3sA-BbOjeEO6JI5XI3_KR0uj9IxSH_LNSiEwMMNLkP0PcC3gO5cSKcmnb1NPW2BMMdlKOSIbxDSWE4sEuYt2Pl_u2F6hVMVeoC-4z43lIv2tv7aF9Pwv-D7MR-mOxQaxYVHw2Ux4FL0zPZOJMU6qPgfzACeItd6H_A4OBMKSQwBl4DEbSwdle5tph-ur01K91FhXhI6BA&media_type=GAMECARD&gvt=xvzGsqK2NF5qWDKzGb71HYGqqIMVe4B78jBDy8zRXg9X3eMNDhtBHS6QVn_07O2eAdaCAKDgrd2CJ6vOgkfisWG4MIGViKO98YiaTEu6xT9SkmKDOTgJog&cert=_W2lx8BZrU3zHi3eeV6VBzEpxWYeyzAdy_Q49_Sq7u7my6ZY_QxzTggxvMIfhkFGiLPhEmtH5McHbAA3Ecb5wnr7Q0C2UD8Kijkt7QgwBGe6gY__nyhe34o-8Y-PFPzaos5b9UmWTAPPHMhIav1Br7XuK0wHKbdYToc_UZ45YFVUWcKWZbSkPRI4zVP_hKNtWvFMmzhRGIEvcA3tA1ormTWDUSSBaxasgo3FSEKQHJaJpq-K3XwWRX4h8DRXierAYwpLCPRpI92C8QJjWhwumAVDa4Dlc1YtE08iEjQ0ZuFAGV2UPXoz57OznzeqP077uodFnKZmMv07576XEbobyENFUlQAAAAAAAAAAAAAAABy4lviwORBYWj1Lz_TAxxdABAAAAAAAAAAAAlTU7O6Za21K9jZis87UO27ERAIoxTcyvpqMWZb7_qhzPystmkcIvWH0ENCfilg6fb2d5m5nY-RQhToEMU2qa_GCZrsPFUENAaN4jVfjYWk5GXX4tk3e-XJTcfyv2Q0oysuwqFGuyww_Ok7XjyTmvVu_7KhPM8oP4ixzoNTHe1cxAmsGi7qATnUN9ke5dIzlhqd7RNqIxz2kibJXV8iKX_BXvRgeepYfVQoIpVxQNFyitqOKy_RZ6LDvA82-C5E1d6hMTj6YQ0oxBhMTRg9N0tNwoQJQ4Y
```

For a digital title:

```http
POST /v3/application_auth_token HTTP/1.1
Host: aauth-lp1.ndas.srv.nintendo.net
User-Agent: libcurl (nnHttp; 789f928b-138e-4b2f-afeb-1acae821d897; SDK 13.3.0.0; Add-on 13.3.0.0)
Accept: */*
X-Nintendo-PowerState: FA
Content-Length: 2254
Content-Type: application/x-www-form-urlencoded
Expect: 100-continue

application_id=0100abf008968000&application_version=00070000&device_auth_token=eyJqa3UiOiJodHRwczovL2RjZXJ0LWxwMS5uZGFzLnNydi5uaW50ZW5kby5uZXQva2V5cyIsImtpZCI6IjM2NzllMTg4LTI5ZWUtNDE4Zi04ZDkwLWI3MjRjYzg1MzQ0MSIsInR5cCI6IkpXVCIsImFsZyI6IlJTMjU2In0.eyJzdWIiOiI2ODMzN2FjYTI4ODE1Y2JiIiwiaXNzIjoiZGF1dGgtbHAxLm5kYXMuc3J2Lm5pbnRlbmRvLm5ldCIsImF1ZCI6IjhmODQ5YjVkMzQ3NzhkOGUiLCJleHAiOjE2MzI3NjMzMDEsImlhdCI6MTYzMjY3NjkwMSwianRpIjoiZTU5YTBiMGUtOTRlMS00NGFhLWI1ZGItMGZjMGNmNTAyYWRhIiwibmludGVuZG8iOnsic24iOiJYQVcxMDAxMjM0NTY3OCIsInBjIjoiSEFDIiwiZHQiOiJOWCBQcm9kIDEiLCJpc3QiOmZhbHNlfX0.Mdl42B_tWnQQZkpp0qkvEwpkAFGos1YQ8OBKDr_rJCQlNVZLrP6_sd53U8kvwI6TWbnuxFtNxcVJh21kbbY23WsjwQN9Ph2pbjEmneov5b5SfAjWSvfEqt_ViKFQVLv_MZZXQpBYZSQmJ3sA-BbOjeEO6JI5XI3_KR0uj9IxSH_LNSiEwMMNLkP0PcC3gO5cSKcmnb1NPW2BMMdlKOSIbxDSWE4sEuYt2Pl_u2F6hVMVeoC-4z43lIv2tv7aF9Pwv-D7MR-mOxQaxYVHw2Ux4FL0zPZOJMU6qPgfzACeItd6H_A4OBMKSQwBl4DEbSwdle5tph-ur01K91FhXhI6BA&media_type=DIGITAL&cert=Ea_BETtJ5tBzI730PfZO2md_qU705gnovFqRjsgw4NbPqQDw_b8H_ecpqm2NbBYs4i3ls95PjSUNHAcV5Yqv36v_wO2eSKyz09YCMo5-eN5DYmyjXaSgy8Fb-Qu0H0VGciRIrx5PNpUJIs7JqV6faPacffFoL4Ac74x6oLtWlRGdgTW7J-cq5ij0O3YNAX_3PoucRi0-xapIVHwRiFUzsj8KM3ug4QttmqVMPW8OAFUWFkGqmsyW_riWRsfDu0srLna4UEc9RxQMbecR-Qw3wyMl5JjCkfA05QLo0MECrhiQE10-yfmlu-ti1pg3wu9y_yiWEJdvgN58H4vlW_n4KL-xDFIdlkQsc4pd3RuL8NwxTSKP_Z2HTyDULs_XpbBejThr59xMGMUdrLOGnxwKiCsjM6SS0P6EpSQSjn4ASns6S1ImTbIvgj8LH4M8wck51XxjOBUz3T_03JQIn9PxObe_OOVfCobKeQXCtKjrvIq40AXg2v2ljj_K7vu8ZmtLMpliexg3dHhr6RgP1TA_tWDLaG_osxnk3XnPDz9FYLLhfugWL2ujsaoNezBOZuKw4CXQ5-IRFk0tWj9lIQvXs8_UFkJXSLIvsS_rs5X3ZaZ0Oc1F8Crt-0Iqgo6g3l259EtwMy6o89yWvU7hSMJ2DfiCEf298eVPMYs95SiTb3bW-wZYfGxVaMJ1XErqlojCi_rSmn9UlHCLgV9PEBK2iF-uAPt1CVxIaejB_7XHtg0bLdMq2OkiyAKHmEFHNPfOvKeJSNh5VQVp18EWbXrio2BXdn0-2UygI8AiTuqq3ummNd6yrNOfU-NNrt5Hccaa6QxsDXCeUlRDmds-lJJJAARL04_E4nZZTnxQE5_sImSkFLBQv8UMjTt0QIFBL_TeR3BkeAi7PSa1YQ0c0_2Bmix7OUuCO1G2mCBGkePVedGPEenm6A9iFNJkyiAhtKBc&cert_key=Tkyp0lOXSP-SEDZ5ShslGnoM1JweZj5kavHTdTnzZaAazXZdTkhaosxZYv2YVL1oqOD7Vmf4orO0Ns85HFGJ8s7cd6dQzvrpyu1uaN4Wum_w5OCf5ld_ga4M8F9TTEUYlAQz0Ft3f9zED0IWOGXqMU0t536XejUQxIUZlNWKBsWT_PZn1nOEcNSeTVHJ5He7QBF6Om99JUvl_qy3v_OppBsBoLdZf_F2miwjCFs0AO7wyf_boK7uU4v-6MtGA8fyyJQgXlAn8SAQTEL3lYVFJyED-Xkel99V8W_3egdnIMvvbJLSRIpLdqjfHqlK32KAcRpzT8J6koc3BkvBhYzNEQ
```

Or for a system title:

```http
POST /v3/application_auth_token HTTP/1.1
Host: aauth-lp1.ndas.srv.nintendo.net
User-Agent: libcurl (nnHttp; 789f928b-138e-4b2f-afeb-1acae821d897; SDK 13.3.0.0; Add-on 13.3.0.0)
Accept: */*
X-Nintendo-PowerState: FA
Content-Length: 935
Content-Type: application/x-www-form-urlencoded

application_id=010000000000003e&application_version=00000000&device_auth_token=eyJqa3UiOiJodHRwczovL2RjZXJ0LWxwMS5uZGFzLnNydi5uaW50ZW5kby5uZXQva2V5cyIsImtpZCI6IjM2NzllMTg4LTI5ZWUtNDE4Zi04ZDkwLWI3MjRjYzg1MzQ0MSIsInR5cCI6IkpXVCIsImFsZyI6IlJTMjU2In0.eyJzdWIiOiI2ODMzN2FjYTI4ODE1Y2JiIiwiaXNzIjoiZGF1dGgtbHAxLm5kYXMuc3J2Lm5pbnRlbmRvLm5ldCIsImF1ZCI6IjhmODQ5YjVkMzQ3NzhkOGUiLCJleHAiOjE2MzI3NjMzMDEsImlhdCI6MTYzMjY3NjkwMSwianRpIjoiZTU5YTBiMGUtOTRlMS00NGFhLWI1ZGItMGZjMGNmNTAyYWRhIiwibmludGVuZG8iOnsic24iOiJYQVcxMDAxMjM0NTY3OCIsInBjIjoiSEFDIiwiZHQiOiJOWCBQcm9kIDEiLCJpc3QiOmZhbHNlfX0.Mdl42B_tWnQQZkpp0qkvEwpkAFGos1YQ8OBKDr_rJCQlNVZLrP6_sd53U8kvwI6TWbnuxFtNxcVJh21kbbY23WsjwQN9Ph2pbjEmneov5b5SfAjWSvfEqt_ViKFQVLv_MZZXQpBYZSQmJ3sA-BbOjeEO6JI5XI3_KR0uj9IxSH_LNSiEwMMNLkP0PcC3gO5cSKcmnb1NPW2BMMdlKOSIbxDSWE4sEuYt2Pl_u2F6hVMVeoC-4z43lIv2tv7aF9Pwv-D7MR-mOxQaxYVHw2Ux4FL0zPZOJMU6qPgfzACeItd6H_A4OBMKSQwBl4DEbSwdle5tph-ur01K91FhXhI6BA&media_type=SYSTEM
```

Response example:

```http
HTTP/1.1 200 OK
Server: nginx
Date: Sun, 26 Sep 2021 19:21:43 GMT
Content-Type: application/json; charset=utf-8
Transfer-Encoding: chunked
Connection: keep-alive
...
X-Nintendo-Used-Directive: global auth
X-Nintendo-Request-Host-Header: aauth-lp1.ndas.srv.nintendo.net
X-Nintendo-Request-SNI: aauth-lp1.ndas.srv.nintendo.net

{"expires_in":86400,"application_auth_token":"eyJqa3UiOiJodHRwczovL2FjZXJ0LWxwMS5uZGFzLnNydi5uaW50ZW5kby5uZXQva2V5cyIsImtpZCI6IjZiMjVhNGU4LTRiOWItNDJhMy1hZDJiLWVhYzRiZGJjOWQ0NiIsInR5cCI6IkpXVCIsImFsZyI6IlJTMjU2In0.eyJzdWIiOiIwMTAwYWJmMDA4OTY4MDAwIiwiZXhwIjoxNjMyNzYzMzAxLCJpYXQiOjE2MzI2NzY5MDEsImlzcyI6ImFhdXRoLWxwMS5uZGFzLnNydi5uaW50ZW5kby5uZXQiLCJqdGkiOiI4MmRmNjY3Yi0wZGExLTQzODEtODdlNC0xYWU0MDNjOGI1NjgiLCJuaW50ZW5kbyI6eyJhaSI6IjAxMDBhYmYwMDg5NjgwMDAiLCJhdiI6IjAwMDciLCJhdCI6MTYzMjY3NjkwMSwiZWRpIjoiYjQ2YmRhNGUxZGQ1ZTdjZTAwMjQzMGE2OGIyYzZkNGUiLCJvcHAiOiJNRU1CRVJTSElQX1JFUVVJUkVEIiwicGgiOiJHQU1FX1NFUlZFUiJ9fQ.bVRnffmMbfN3Q-XAEHAt8qa-QPQf-jOBQMwhhMu0hWOUK3UGviDiG4fti_ws6-0vaYxsAisiong051wUhDi0MyzN9BSsJ1nTA0mB6rRfCeqdsdbgRz6hWP4lRgeuzeyVSX6NTIQvdIJTYsqd800i1tkpR2ynTBVwUHwcle9vqNWuIkzZgl-osk439AP70vV2okLSFoSP49EGH6UW7ocgstto9xwy39DiY93y8Di0uX-GvYQK_inAxaIgMUCLBcKJzZ8iwUKV8E1MeD-yWNWGJ9nW9F5kPa6mvDFBOdzcvIYYTjnKh2JSJLS2-nlNyTZoN8t3OfTVLwd3KlDj0HhzZA","settings":[],"online_play_policy":"MEMBERSHIP_REQUIRED","policy_handler":"GAME_SERVER"}
```

Or if an error has occurred:

```http
HTTP/1.1 400 Bad Request
Server: nginx
Date: Sun, 26 Sep 2021 19:21:43 GMT
Content-Type: application/json; charset=utf-8
Transfer-Encoding: chunked
Connection: keep-alive
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
X-Download-Options: noopen
X-Permitted-Cross-Domain-Policies: none
Referrer-Policy: strict-origin-when-cross-origin
Vary: Accept
Cache-Control: no-cache
X-Request-Id: ae8b948d-a0ca-4073-a41a-2393a69f12c6
X-Runtime: 0.006897

{"errors": [{"code": "0118", "message": "Invalid parameter in request."}]}
```
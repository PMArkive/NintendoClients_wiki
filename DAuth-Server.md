[Switch Servers](Server-List#switch) > Device Authentication
---

URL: https://dauth-lp1.ndas.srv.nintendo.net

Almost all Switch servers can only be accessed after obtaining a token from the dauth server. The dauth server only accepts requests with a valid client certificate. Every Switch has its own client certificate, which stored in [PRODINFO](https://switchbrew.org/wiki/Calibration).

![](https://www.dropbox.com/s/cwubnhmd5neum9k/dauth.png?raw=1)

Because the certificate is signed by Nintendo there is only one way to get a valid certificate: buy a Switch and dump it.

The dauth server takes form-encoded requests and responds with json-encoding. It uses base64url, and the client does not add any padding characters.

* [Headers](#headers)
* [Methods](#methods)
* [Errors](#errors)
* [Examples](#examples)

## Headers
| Header | Description |
| --- | --- |
| Host | `dauth-lp1.ndas.srv.nintendo.net` |
| User-Agent | [User agent](#user-agents) |
| Accept | `*/*` |
| X-Nintendo-PowerState | `FA` (fully awake) or `HA` (half awake) |
| Content-Length | Content length |
| Content-Type | `application/x-www-form-urlencoded` |

#### User Agents
| System Version | User agent |
| --- | --- |
| 9.0.0 - 9.2.0 | `libcurl (nnDauth; 16f4553f-9eee-4e39-9b61-59bc7c99b7c8; SDK 9.3.0.0)` |
| 10.0.0 - 10.2.0 | `libcurl (nnDauth; 16f4553f-9eee-4e39-9b61-59bc7c99b7c8; SDK 10.4.0.0)` |
| 11.0.0 - 11.0.1 | `libcurl (nnDauth; 16f4553f-9eee-4e39-9b61-59bc7c99b7c8; SDK 11.4.0.0)` |
| 12.0.0 - 12.1.0 | `libcurl (nnDauth; 16f4553f-9eee-4e39-9b61-59bc7c99b7c8; SDK 12.3.0.0)` |
| 13.0.0 | `libcurl (nnDauth; 16f4553f-9eee-4e39-9b61-59bc7c99b7c8; SDK 13.3.0.0)` |
| 13.1.0 - 13.2.1 | `libcurl (nnDauth; 16f4553f-9eee-4e39-9b61-59bc7c99b7c8; SDK 13.4.0.0)` |

## Methods
9.0.0 - 12.1.0:

| Method | URL |
| --- | --- |
| POST | <code><a href="#post-v6challenge">/v6/challenge</a></code> |
| POST | <code><a href="#post-v6device_auth_token">/v6/device_auth_token</a></code> |
| POST | <code><a href="#post-v6edge_token">/v6/edge_token</a></code> |

13.0.0 - 13.2.1:

| Method | URL |
| --- | --- |
| POST | <code><a href="#post-v7challenge">/v7/challenge</a></code> |
| POST | <code><a href="#post-v7device_auth_token">/v7/device_auth_token</a></code> |
| POST | <code><a href="#post-v7edge_token">/v7/edge_token</a></code> |

### POST /v6/challenge
| Param | Description |
| --- | --- |
| key_generation | [Master key revision](#master-key-revisions) |

Response:

| Field | Description |
| --- | --- |
| challenge | Base64-encoded challenge (32 bytes) |
| data | Base64-encoded AES key required for MAC calculation (16 bytes) |

### POST /v6/device_auth_token
This method returns a device token as JWT.

| Param | Description |
| --- | --- |
| challenge | Base64-encoded challenge (retrieved from <code><a href="#post-v6challenge">/v6/challenge</a></code>) |
| client_id | Application-specific [client id](#known-client-ids) |
| ist | `true` or `false` (depends on [platform region](https://switchbrew.org/wiki/Settings_services#GetT)) |
| key_generation | [Master key revision](#master-key-revisions) |
| system_version | [System version digest](https://switchbrew.org/wiki/System_Version_Title) |
| mac | Base64-encoded AES-CMAC of all previous fields in form-encoding |

Response on success:

| Field | Description |
| --- | --- |
| expires_in | Expiration in seconds (86400) |
| device_auth_token | Device token |

The key for the AES-CMAC is calculated as follows:
1. The `aes_kek_generation_source` is decrypted with the master key.
2. The dauth key source is decrypted with the key from step 1.
3. The key from the `data` field of the challenge is decrypted with the key from step 2.

The dauth key source is: `8be45abcf987021523ca4f5e2300dbf0`

### POST /v6/edge_token
This method returns a different kind of device token. It takes the same parameters as <code><a href="#post-v6device_auth_token">/v6/device_auth_token</a></code>.

Response on success:

| Field | Description |
| --- | --- |
| expires_in | Expiration in seconds (86400) |
| dtoken | Device token |

### POST /v7/challenge
This is the same as <code><a href="#post-v6challenge">/v6/challenge</a></code>.

### POST /v7/device_auth_token
This is the same as <code><a href="#post-v6device_auth_token">/v6/device_auth_token</a></code>.

### POST /v7/edge_token
This method is similar to <code><a href="#post-v6edge_token">/v6/edge_token</a></code>. The only difference is that a `vendor_id` parameter was added:

| Param | Description |
| --- | --- |
| challenge | Base64-encoded challenge |
| client_id | Application-specific [client id](#known-client-ids) |
| ist | `true` or `false` (depends on [platform region](https://switchbrew.org/wiki/Settings_services#GetT)) |
| key_generation | [Master key revision](#master-key-revisions) |
| system_version | [System version digest](https://switchbrew.org/wiki/System_Version_Title) |
| vendor_id | `akamai`, `llnw` or `lumen` |
| mac | Base64-encoded AES-CMAC of all previous fields in form-encoding |

### Master Key Revisions
| System version | Key generation |
| --- | --- |
| 9.0.0 - 9.0.1 | 10 |
| 9.1.0 - 12.1.0 | 11 |
| 13.0.0 - 13.2.1 | 13 |

### Known Client IDs
| Client ID | Description |
| --- | --- |
| `146c8ac7b8a0db52` | SCSI storage |
| `41f4a6491028e3c4` | Pushmo and Tagaya |
| `67bf9945b45248c6` | BCAT |
| `6ac5a6873fe5f68c` | SATA storage |
| `81333c548b2e876d` | [Account server](Account-Server-(Switch)) |
| `83b72b05dc3278d7` | NPNS |
| `8f849b5d34778d8e` | [AAuth](AAuth-Server) and [BaaS](BAAS-Server) |
| `93af0acb26258de9` | Beach |
| `d5b6cac2c1514c56` | Dragons |
| `dc656ea03b63cf68` | Parental controls |
| `df51c436bc01c437` | Prepo |

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
| --- | --- | --- 
| 0004 | 2181-4004 | Unauthorized device. |
| 0007 | 2181-4007 | System update is required. |
| 0008 | 2181-4008 | Device has been banned. |
| 0009 | 2181-4009 | ? |
| 0010 | 2181-4010 | ? |
| 0011 | 2181-4011 | ? |
| 0013 | 2181-4013 | ? |
| 0014 | 2181-4014 | Invalid parameter in request. |
| 0015 | 2181-4015 | ? |
| 0016 | 2181-4016 | Invalid parameter in request. |
| 0017 | 2181-4017 | ? |
| 0018 | 2181-4018 | ? |
| 0019 | 2181-4019 | ? |
| 0020 | 2181-4020 | ? |
| 0021 | 2181-4021 | ? |
| 0022 | 2181-4022 | ? |
| 0023 | 2181-4023 | ? |
| 0024 | 2181-4024 | ? |
| 0025 | 2181-4025 | ? |
| 0026 | 2181-4026 | ? |
| 0027 | 2181-4027 | ? |
| 0028 | 2181-4028 | ? |
| 0029 | 2181-4029 | ? |
| 0030 | 2181-4030 | ? |
| 0031 | 2181-4031 | ? |

## Examples
Note that the client must always use a valid device certificate as the client certificate. If the client does not provide a certificate, the nginx server rejects the request:

```
HTTP/1.1 400 Bad Request
Server: nginx
Date: Sun, 26 Sep 2021 19:21:43 GMT
Content-Type: text/html
Content-Length: 246
Connection: close

<html>
<head><title>400 No required SSL certificate was sent</title></head>
<body bgcolor="white">
<center><h1>400 Bad Request</h1></center>
<center>No required SSL certificate was sent</center>
<hr><center>nginx</center>
</body>
</html>
```

Before anything else, one must obtain a challenge:

```
POST /v7/challenge HTTP/1.1
Host: dauth-lp1.ndas.srv.nintendo.net
User-Agent: libcurl (nnDauth; 16f4553f-9eee-4e39-9b61-59bc7c99b7c8; SDK 13.3.0.0)
Accept: */*
X-Nintendo-PowerState: FA
Content-Length: 17
Content-Type: application/x-www-form-urlencoded

key_generation=13
```

```
HTTP/1.1 200 OK
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
ETag: W/"eb797bb39b7f70a033c7bbd5020bf9f0"
Cache-Control: max-age=0, private, must-revalidate
X-Request-Id: b1afb7d0-b6d9-4eff-8561-0159c97cdf58
X-Runtime: 0.009675
X-Nintendo-Used-Directive: global auth
X-Nintendo-Request-Host-Header: dauth-lp1.ndas.srv.nintendo.net
X-Nintendo-Request-SNI: dauth-lp1.ndas.srv.nintendo.net

{"challenge":"mtAvqNqzYSoCEixxL_rjWoHfdDjAH51h5XcKZ6ksq2s=","data":"1OikFLkHptkhDpqy7VHb3g=="}
```

Then, one can obtain a device token:

```
POST /v7/device_auth_token HTTP/1.1
Host: dauth-lp1.ndas.srv.nintendo.net
User-Agent: libcurl (nnDauth; 16f4553f-9eee-4e39-9b61-59bc7c99b7c8; SDK 13.3.0.0)
Accept: */*
X-Nintendo-PowerState: FA
Content-Length: 211
Content-Type: application/x-www-form-urlencoded

challenge=mtAvqNqzYSoCEixxL_rjWoHfdDjAH51h5XcKZ6ksq2s=&client_id=8f849b5d34778d8e&ist=false&key_generation=13&system_version=CusHY#000d0000#r1xneESd4PiTRYIhVIl0bK1ST5L5BUmv_uGPLqc4PPo=&mac=AW9LE1TSN0xrzY1FfHHXwg
```

```
HTTP/1.1 200 OK
Server: nginx
Date: Sun, 26 Sep 2021 19:21:43 GMT
Content-Type: application/json; charset=utf-8
Transfer-Encoding: chunked
Connection: keep-alive
...
X-Nintendo-Used-Directive: global auth
X-Nintendo-Request-Host-Header: dauth-lp1.ndas.srv.nintendo.net
X-Nintendo-Request-SNI: dauth-lp1.ndas.srv.nintendo.net

{"expires_in":86400,"device_auth_token":"eyJqa3UiOiJodHRwczovL2RjZXJ0LWxwMS5uZGFzLnNydi5uaW50ZW5kby5uZXQva2V5cyIsImtpZCI6IjM2NzllMTg4LTI5ZWUtNDE4Zi04ZDkwLWI3MjRjYzg1MzQ0MSIsInR5cCI6IkpXVCIsImFsZyI6IlJTMjU2In0.eyJzdWIiOiI2ODMzN2FjYTI4ODE1Y2JiIiwiaXNzIjoiZGF1dGgtbHAxLm5kYXMuc3J2Lm5pbnRlbmRvLm5ldCIsImF1ZCI6IjhmODQ5YjVkMzQ3NzhkOGUiLCJleHAiOjE2MzI3NjMzMDEsImlhdCI6MTYzMjY3NjkwMSwianRpIjoiZTU5YTBiMGUtOTRlMS00NGFhLWI1ZGItMGZjMGNmNTAyYWRhIiwibmludGVuZG8iOnsic24iOiJYQVcxMDAxMjM0NTY3OCIsInBjIjoiSEFDIiwiZHQiOiJOWCBQcm9kIDEiLCJpc3QiOmZhbHNlfX0.Mdl42B_tWnQQZkpp0qkvEwpkAFGos1YQ8OBKDr_rJCQlNVZLrP6_sd53U8kvwI6TWbnuxFtNxcVJh21kbbY23WsjwQN9Ph2pbjEmneov5b5SfAjWSvfEqt_ViKFQVLv_MZZXQpBYZSQmJ3sA-BbOjeEO6JI5XI3_KR0uj9IxSH_LNSiEwMMNLkP0PcC3gO5cSKcmnb1NPW2BMMdlKOSIbxDSWE4sEuYt2Pl_u2F6hVMVeoC-4z43lIv2tv7aF9Pwv-D7MR-mOxQaxYVHw2Ux4FL0zPZOJMU6qPgfzACeItd6H_A4OBMKSQwBl4DEbSwdle5tph-ur01K91FhXhI6BA"}
```

Or an edge token:

```
POST /v7/edge_token HTTP/1.1
Host: dauth-dd1.ndas.srv.nintendo.net
User-Agent: libcurl (nnDauth; 16f4553f-9eee-4e39-9b61-59bc7c99b7c8; SDK 13.3.0.0)
Accept: */*
X-Nintendo-PowerState: FA
Content-Length: 228
Content-Type: application/x-www-form-urlencoded

challenge=mtAvqNqzYSoCEixxL_rjWoHfdDjAH51h5XcKZ6ksq2s=&client_id=67bf9945b45248c6&ist=false&key_generation=13&system_version=CusHY#000d0000#r1xneESd4PiTRYIhVIl0bK1ST5L5BUmv_uGPLqc4PPo=&vendor_id=akamai&mac=8HKiiCC5Zqp3zxut8sSWZw
```

```
HTTP/1.1 200 OK
Server: nginx
Date: Sun, 26 Sep 2021 19:21:43 GMT
Content-Type: application/json; charset=utf-8
Transfer-Encoding: chunked
Connection: keep-alive
...
X-Nintendo-Used-Directive: global auth
X-Nintendo-Request-Host-Header: dauth-dd1.ndas.srv.nintendo.net
X-Nintendo-Request-SNI: dauth-dd1.ndas.srv.nintendo.net

{"expires_in": 86400, "dtoken": "exp=1632763301~acl=%2F%2A~data=sub=68337aca28815cbb.sn=XAW10012345678.id=a73ff2b9-e772-4dc6-a01e-0861227bd202~hmac=bb7c0f27edddeb50777ec6a2fba6deacd8b8fc04faeaaaa864027c54767dea6c"}
```

Example of an error response:

```
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
X-Request-Id: 84a8a661-a312-480a-b389-35cf83106b51
X-Runtime: 0.007699

{"errors": [{"code": "0014", "message": "Invalid parameter in request."}]}
```
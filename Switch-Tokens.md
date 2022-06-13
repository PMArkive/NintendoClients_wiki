Many Switch servers use JWTs (json web tokens) for authentication. JWTs are a simple and standardized way to pass information between servers without storing it in a database. A JWT consists of three parts separated by dots, and each part is encoded with base64url.

JWTs are described formally in [RFC 7515](https://tools.ietf.org/html/rfc7515), [RFC 7518](https://tools.ietf.org/html/rfc7518) and [RFC 7519](https://tools.ietf.org/html/rfc7519).

Details on specific kinds of token:
* [Device auth tokens](#dauth-tokens)
* [Application auth tokens](#aauth-tokens)
* [BaaS access tokens](#baas-access-tokens)
* [BaaS user tokens](#baas-user-tokens)
* [ID tokens](#id-tokens)

### Header
The first part contains metadata about the JWT, such as the signature algorithm that is used.

| Field | Description |
| --- | --- |
| `jku` | **JWK Set URL:** The URL of a server that provides a [JWK set](#jwk-set). This server provides the public keys that are used to verify the signature of the JWT. |
| `kid` | **Key ID:** Selects a key from the JWK set provided by the `jku` server. This is a uuid v4 on Nintendo's servers. |
| `alg` | **Algorithm:** Always `RS256`. |
| `typ` | **Type:** Always `JWT`. Not present in tokens returned by baas server. |

Example:

```json
{
  "jku": "https://dcert-lp1.ndas.srv.nintendo.net/keys",
  "kid": "2567fb65-eacb-48ba-9eb0-ed815a9f1a06",
  "typ": "JWT",
  "alg": "RS256"
}
```

### Payload
The second part contains the information that's stored in the JWT, such as the user id. The content of the payload depends on the type of token, but the following fields are always present:

| Field | Description |
| --- | --- |
| `sub` | **Subject:** An id that identifies what the JWT is about, such as a user id. |
| `exp` | **Expiration Time:** A timestamp that specifies the expiration date of the JWT. |
| `iat` | **Issued At:** A timestamp that specifies the time at which the token was generated. |
| `iss` | **Issuer:** The server that generated the JWT. |
| `jti` | **JWT ID:** A unique id per generated JWT. |

### Signature
The third part contains the signature. This prevents the JWT from being modified by anyone. Nintendo uses the RS256 algorithm everywhere, which is formally called RSASSA-PKCS1-v1_5.

The signature is calculated over both the [header](#header) and the [payload](#payload) in base64-encoded form with a dot in between. Only the server can generate the signature, because only the server knows the private keys. Anyone can verify the signature though, because anyone can download the public keys from the server that hosts the JWK set.

### JWK Set
The JWK set contains a set of public keys that can be used to verify the [signature](#signature) of the JWT. It's hosted by the server that's specified in the `jku` field in the [header](#header).

Each JWK contains the following fields:

| Field | Description |
| --- | --- |
| `kty` | **Key Type:** Always `RSA`. |
| `e` | **Exponent:** The public exponent of the RSA key (base64url). |
| `n` | **Modulus:** The public modulus of the RSA key (base64url). |
| `alg` | **Algorithm:** Always `RS256`. |
| `use` | **Public Key Use:** Always `sig`. |
| `kid` | **Key ID:** A unique id that identifies the key. This id is also specified in the [JWT header](#header). |

The baas server also returns the following fields:

| Field | Description |
| --- | --- |
| `usage` | `developer` or `internal` |
| `x5c` | X.509 Certificate Chain |

JWKs are described formally in [RFC 7517](https://tools.ietf.org/html/rfc7517) and [RFC 7518](https://tools.ietf.org/html/rfc7518).

Most JWKs are regenerated every 24 hours. The only exception is the JWK for BaaS [access](#baas-access-tokens) and [user](#baas-user-tokens) tokens, which never changes. To ensure that all valid tokens can be verified, even after the a new JWK is generated, the JWK set contains the three previous JWKs as well.

### Example
```
eyJqa3UiOiJodHRwczovL2RjZXJ0LWxwMS5uZGFzLnNydi5uaW50ZW5kby5uZXQva2V5cyIsImtpZCI6IjM2NzllMT
g4LTI5ZWUtNDE4Zi04ZDkwLWI3MjRjYzg1MzQ0MSIsInR5cCI6IkpXVCIsImFsZyI6IlJTMjU2In0.eyJzdWIiOiI2
ODMzN2FjYTI4ODE1Y2JiIiwiaXNzIjoiZGF1dGgtbHAxLm5kYXMuc3J2Lm5pbnRlbmRvLm5ldCIsImF1ZCI6IjhmOD
Q5YjVkMzQ3NzhkOGUiLCJleHAiOjE2MzI3NjMzMDEsImlhdCI6MTYzMjY3NjkwMSwianRpIjoiZTU5YTBiMGUtOTRl
MS00NGFhLWI1ZGItMGZjMGNmNTAyYWRhIiwibmludGVuZG8iOnsic24iOiJYQVcxMDAxMjM0NTY3OCIsInBjIjoiSE
FDIiwiZHQiOiJOWCBQcm9kIDEiLCJpc3QiOmZhbHNlfX0.Mdl42B_tWnQQZkpp0qkvEwpkAFGos1YQ8OBKDr_rJCQl
NVZLrP6_sd53U8kvwI6TWbnuxFtNxcVJh21kbbY23WsjwQN9Ph2pbjEmneov5b5SfAjWSvfEqt_ViKFQVLv_MZZXQp
BYZSQmJ3sA-BbOjeEO6JI5XI3_KR0uj9IxSH_LNSiEwMMNLkP0PcC3gO5cSKcmnb1NPW2BMMdlKOSIbxDSWE4sEuYt
2Pl_u2F6hVMVeoC-4z43lIv2tv7aF9Pwv-D7MR-mOxQaxYVHw2Ux4FL0zPZOJMU6qPgfzACeItd6H_A4OBMKSQwBl4
DEbSwdle5tph-ur01K91FhXhI6BA
```

## DAuth Tokens
| Field | Value |
| --- | --- |
| `jku` | https://dcert-lp1.ndas.srv.nintendo.net/keys |

Payload fields:

| Field | Description |
| --- | --- |
| `sub` | Device id |
| `iss` | dauth-lp1.ndas.srv.nintendo.net |
| `aud` | Client id |
| `nintendo` | [Device information](#device-information) |

### Device Information
| Field | Description |
| --- | --- |
| `sn` | Serial number |
| `pc` | Product code: `HAC` |
| `dt` | Device type: `NX Prod 1` |
| `ist` | IsT (bool) |

### Example
```json
{
    "sub": "68337aca28815cbb",
    "iss": "dauth-lp1.ndas.srv.nintendo.net",
    "aud": "8f849b5d34778d8e",
    "exp": 1632763301,
    "iat": 1632676901,
    "jti": "e59a0b0e-94e1-44aa-b5db-0fc0cf502ada",
    "nintendo": {
        "sn": "XAW10012345678",
        "pc": "HAC",
        "dt": "NX Prod 1",
        "ist" :false
    }
}
```

## AAuth Tokens
| Field | Value |
| --- | --- |
| `jku` | https://acert-lp1.ndas.srv.nintendo.net/keys |

Payload fields:

| Field | Description |
| --- | --- |
| `sub` | Title id (`%016x`) |
| `iss` | aauth-lp1.ndas.srv.nintendo.net |
| `nintendo` | [Application information](#application-information) |

### Application Information
| Field | Description |
| --- | --- |
| `ai` | Application id (`%016x`) |
| `av` | Application version (`%04x`) |
| `at` | Application time (current timestamp) |
| `edi` | Unique id (32 hex digits) |
| `opp` | Online play policy: `MEMBERSHIP_REQUIRED` or `FREE` |
| `ph` | Policy handler: `SYSTEM` or `GAME_SERVER` |

### Example
```json
{
    "sub": "0100abf008968000",
    "exp": 1632763301,
    "iat": 1632676901,
    "iss": "aauth-lp1.ndas.srv.nintendo.net",
    "jti": "82df667b-0da1-4381-87e4-1ae403c8b568",
    "nintendo": {
        "ai": "0100abf008968000",
        "av": "0007",
        "at": 1632676901,
        "edi": "b46bda4e1dd5e7ce002430a68b2c6d4e",
        "opp": "MEMBERSHIP_REQUIRED",
        "ph": "GAME_SERVER"
    }
}
```

## BaaS Access Tokens
| Field | Value |
| --- | --- |
| `jku` | https://e0d67c509fb203858ebcb2fe3f88c2aa.baas.nintendo.com/1.0.0/internal_certificates |
| `kid` | `3083c1b2-5d68-434b-be32-11f915570500` |

Payload fields:

| Field | Description |
| --- | --- |
| `sub` | `ed9e2f05d286f7b8` |
| `aud` | `ed9e2f05d286f7b8` |
| `iss` | https://e0d67c509fb203858ebcb2fe3f88c2aa.baas.nintendo.com |
| `typ` | Always `token` |
| `bs:sts` | Status (always `[385]`) |
| `bs:grt` | Grant type (always 1) |
| `nintendo` | [Device information](#device-information-0) |

### Device Information
| Field | Description |
| --- | --- |
| `dt` | Device type: `NX Prod 1` |
| `pc` | Product code: `HAC` |
| `di` | Device id |
| `sn` | Serial number |
| `ist` | IsT (bool) |

### Example
```json
{
    "sub": "ed9e2f05d286f7b8",
    "aud": "ed9e2f05d286f7b8",
    "bs:sts": [385],
    "nintendo": {
        "dt": "NX Prod 1",
        "pc": "HAC",
        "di": "68337aca28815cbb",
        "sn": "XAW10012345678",
        "ist": false
    },
    "iss": "https://e0d67c509fb203858ebcb2fe3f88c2aa.baas.nintendo.com",
    "typ": "token",
    "bs:grt": 1,
    "exp": 1632687701,
    "iat": 1632676901,
    "jti": "878d0735-571a-4b94-82a6-2bf183114db1"
}
```

## BaaS User Tokens
| Field | Value |
| --- | --- |
| `jku` | https://e0d67c509fb203858ebcb2fe3f88c2aa.baas.nintendo.com/1.0.0/internal_certificates |
| `kid` | `3083c1b2-5d68-434b-be32-11f915570500` |

Payload fields:

| Field | Description |
| --- | --- |
| `sub` | User id (`%016x`) |
| `aud` | `ed9e2f05d286f7b8` |
| `iss` | https://e0d67c509fb203858ebcb2fe3f88c2aa.baas.nintendo.com |
| `typ` | Always `token` |
| `bs:sts` | Status (always `[10414578180576298,272640,1,0,0,19316357715722240,16]`) |
| `bs:grt` | Grant type (always 2) |
| `bs:did` | Device account id |

Example:

```json
{
    "aud": "ed9e2f05d286f7b8",
    "sub": "b4922963e6b8deb2",
    "bs:sts": [10414578180576298, 272640, 1, 0, 0, 19316357715722240, 16],
    "iss": "https://e0d67c509fb203858ebcb2fe3f88c2aa.baas.nintendo.com",
    "typ": "token",
    "bs:grt": 2,
    "exp": 1644766994,
    "iat": 1644756194,
    "bs:did": "2ded458f5e0beee2",
    "jti": "aedb91a6-1cf9-4a0e-bfbd-1ccdd191b4e3"
}
```

## ID Tokens
| Field | Value |
| --- | --- |
| `jku` | https://e0d67c509fb203858ebcb2fe3f88c2aa.baas.nintendo.com/1.0.0/certificates |

Payload fields:

| Field | Description |
| --- | --- |
| `aud` | Always `ed9e2f05d286f7b8` |
| `sub` | User id (`%016x`) |
| `iss` | https://e0d67c509fb203858ebcb2fe3f88c2aa.baas.nintendo.com |
| `typ` | Always `id_token` |
| `bs:did` | Device account id (`%016x`) |
| `nintendo` | [Application information](#application-information-1) (only present if an aauth token is provided) |

### Application Information
| Field | Description |
| --- | --- |
| `ai` | Application id (`%016x`) |
| `av` | Application version (`%04x`) |
| `at` | Application time (current timestamp) |
| `edi` | Unique id (copied from aauth token) |

### Example
```json
{
    "aud": "ed9e2f05d286f7b8",
    "sub": "b4922963e6b8deb2",
    "nintendo": {
        "at": 1644756194,
        "av": "0007",
        "ai": "0100abf008968000",
        "edi": "84e16d390427028b3788ef082d342ce0"
    },
    "iss": "https://e0d67c509fb203858ebcb2fe3f88c2aa.baas.nintendo.com",
    "typ": "id_token",
    "exp": 1644766994,
    "iat": 1644756194,
    "bs:did": "2ded458f5e0beee2",
    "jti": "164eea2b-508c-47d0-9d48-9eca1cac0f56"
}
```

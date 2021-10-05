[[Server List]] > Account Server (Switch)
---

This server takes form-encoded requests and responds with json-encoding.

* [Headers](#headers)
* [Methods](#methods)
* [Errors](#errors)

## Headers
| Header | Description |
| --- | --- |
| Host | `accounts.nintendo.com` |
| User-Agent | [User agent](#user-agents) |
| Accept | `*/*` |
| Content-Length | Content length |
| Content-Type | `application/x-www-form-urlencoded` |

#### User Agents
| System Version | User agent |
| --- | --- |
| 9.0.0 - 9.2.0 | `libcurl (nnAccount; 789f928b-138e-4b2f-afeb-1acae821d897; SDK 9.3.0.0; Add-on 9.3.0.0)` |
| 10.0.0 - 10.2.0 | `libcurl (nnAccount; 789f928b-138e-4b2f-afeb-1acae821d897; SDK 10.4.0.0; Add-on 10.4.0.0)` |
| 11.0.0 - 11.0.1 | `libcurl (nnAccount; 789f928b-138e-4b2f-afeb-1acae821d897; SDK 11.4.0.0; Add-on 11.4.0.0)` |
| 12.0.0 - 12.1.0 | `libcurl (nnAccount; 789f928b-138e-4b2f-afeb-1acae821d897; SDK 12.3.0.0; Add-on 12.3.0.0)` |
| 13.0.0 | `libcurl (nnAccount; 789f928b-138e-4b2f-afeb-1acae821d897; SDK 13.3.0.0; Add-on 13.3.0.0)` |

## Methods
**accounts.nintendo.com:**

| Method | URL |
| --- | --- |
| GET | `/api/1.0.0/users/<id>/qrcode_param` |
| POST | <code><a href="#post-connect100apitoken">/connect/1.0.0/api/token</a></code> |
| POST | `/connect/1.0.0/authorize` |
| GET | `/profile` |

**api.accounts.nintendo.com:**

| Method | URL |
| --- | --- |
| GET | `/2.0.0/users/me` |

**c-lp1.accounts.nintendo.com:**

| Method | URL |
| --- | --- |
| GET | `/v1/apps/<id>/catalog.json` |
| GET | `/v1/apps/<id>/nx.jpg` |

### POST /connect/1.0.0/api/token
| Param | Description |
| --- | --- |
| grant_Type | `refresh_token` |
| client_id | Client id |
| code_verifier | |
| refresh_token | |
| device_authentication_token | [Device token](DAuth-Server) |

Response on success:

| Field | Description |
| --- | --- |
| token_type | `Bearer` |
| expires_in | 900 |
| scope | List of scopes |
| access_token | Access token |

## Errors
On error, the server sends the following response:

| Field | Description |
| --- | --- |
| error | Error name |
| error_description | Error description |
| error_detail | Error details (optional) |

### Known Errors
`/2.0.0/users/me` and `/api/1.0.0/users/<id>/qrcode_param`:

| Name | Description |
| --- | --- |
| invalid_token | ? |
| insufficient_scope | ? |
| under_maintenance | ? |

`/connect/1.0.0/api/token`:

| Name | Detail | Description |
| --- | --- | --- |
| invalid_request | | The request does not satisfy the schema |
| invalid_client | | Client authentication failed |
| invalid_grant | | ? |
| invalid_grant | user_deleted | ? |
| invalid_grant | user_banned | ? |
| invalid_grant | user_suspended | ? |
| invalid_grant | user_withdrawn | ? |
| invalid_grant | user_terms_agreement_required | ? |
| invalid_scope | | ? |
| invalid_scope | scope_token_unknown | The requested scope is invalid |
| invalid_scope | scope_token_prohibited | ? |
| invalid_scope | scope_token_not_authorized | ? |
| unauthorized_client | | ? |
| unsupported_grant_type | | ? |
| server_error | | ? |
| under_maintenance | | ? |

Others:

| Name | Detail | Description |
| --- | --- | --- |
| unauthorized_client | | ? |
| access_denied | | ? |
| access_denied | id_token_hint_invalid | ? |
| access_denied | user_deleted | ? |
| invalid_scope | | ? |
| invalid_scope | scope_token_unknown | ? |
| invalid_scope | scope_token_prohibited | ? |
| server_error | | ? |
| login_required | | ? |
| login_required | user_not_logged_in | ? |
| login_required | user_different_from_id_token_hint | ? |
| consent_required | | ? |
| interaction_required | | ? |
| interaction_required | user_banned | ? |
| interaction_required | user_suspended | ? |
| interaction_required | user_terms_agreement_required | ? |
| under_maintenance | | ? |
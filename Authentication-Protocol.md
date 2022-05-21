[[NEX Protocols]] > Ticket Granting (10)
---
This is the only protocol that's available on the authentication server. Other protocols are only available on the secure server.

| Method ID | Name (Wii U) | Name (Switch) |
| --- | --- | --- |
| 1 | [Login](#1-login) | [ValidateAndRequestTicket](#1-login) |
| 2 | [LoginEx](#2-loginex) | [ValidateAndRequestTicketWithCustomData](#2-loginex) |
| 3 | [RequestTicket](#3-requestticket) | [RequestTicket](#3-requestticket) |
| 4 | [GetPID](#4-getpid) | [GetPID](#4-getpid) |
| 5 | [GetName](#5-getname) | [GetName](#5-getname) |
| 6 | [LoginWithContext](#6-loginwithcontext) | [ValidateAndRequestTicketWithParam](#6-validateandrequestticketwithparam) |

# (1) Login
Usernames are not case sensitive.

If the username does not exist, the `%retval%` field is set to `RendezVous::InvalidUsername` and the other fields are left blank.

## Request
| Type | Name | Description |
| --- | --- | --- |
| [String] | strUserName | Username |

## Response
| Type | Name | Description |
| --- | --- | --- |
| [Result] | %retval% | Result code |
| [PID] | pidPrincipal |  User pid |
| [Buffer] | pbufResponse | [Kerberos ticket](Kerberos-Authentication#kerberos-ticket) |
| [RVConnectionData] | pConnectionData | Connection info for secure server.<br><br>The Nintendo Switch allows the secure server to be at the same address as the authentication server. In that case, the secure server station url points to  0.0.0.1 with port 1. |
| [String] | strReturnMsg | Server build name |

Examples of server build names:

| Server | Build name |
| --- | --- |
| Friends | branch:origin/feature/45925_FixAutoReconnect build:3_10_11_2006_0 |
| DKC:TF | branch:origin/release/ngs/3.4.x.3 build:3_4_13_3_0 |
| MK8 | branch:origin/project/wup-amk build:3_5_17_2011_0 |

# (2) LoginEx
Usernames are not case sensitive.

If the username does not exist, the `%retval%` field is set to `RendezVous::InvalidUsername` and the other fields are left blank.

Wii U servers don't seem to check what's in the extra data.

## Request
| Type | Name | Description |
| --- | --- | --- |
| [String] | strUserName | Username |
| [Any]&lt;[AuthenticationInfo](#authenticationinfo-structure)&gt; | oExtraData | Authentication info |

### AuthenticationInfo ([Structure])
| This structure inherits from [Data] |
| --- |

| Type | Name | Description |
| --- | --- | --- |
| [String] | m_authToken | Token, as received from the account server |
| Uint32 | m_ngsVersion | Always 3 on Wii U. Always 4 on Switch. |
| Uint8 | m_authTokenType | Always 1 on Wii U. Always 2 on Switch. |
| Uint32 | m_serverVersion | See below |

The server version is in the build name of the server. If the build name is `3_x_y_z_0` then `z` is the server version. Click [here](https://kinnay.github.io/view.html?page=nexwiiu) for a list of server build names.

## Response
| Type | Name | Description |
| --- | --- | --- |
| [Result] | %retval% | Result code |
| [PID] | pidPrincipal | User pid |
| [Buffer] | pbufResponse | [Kerberos ticket](Kerberos-Authentication#kerberos-ticket) |
| [RVConnectionData] | pConnectionData | Connection info for secure server.<br><br>The Nintendo Switch allows the secure server to be at the same address as the authentication server. In that case, the secure server station url points to  0.0.0.1 with port 1. |
| [String] | strReturnMsg | Server build name |
| [String] | pSourceKey | **Only present on Switch.** If this is a non-empty hex string, key derivation is skipped and this string is used as the key to decrypt the ticket instead. |

# (3) RequestTicket
If the source or target pid is invalid, the `%retval%` field is set to `Core::AccessDenied` and the ticket is empty.

## Request
| Type | Name | Description |
| --- | --- | --- |
| [PID] | idSource | User pid |
| [PID] | idTarget | Secure server pid |

## Response
| Type | Name | Description |
| --- | --- | --- |
| [Result] | %retval% | Result code |
| [Buffer] | bufResponse | [Kerberos ticket](Kerberos-Authentication#kerberos-ticket) |
| [String] | pSourceKey | **Only present on Switch.** If this is a non-empty hex string, key derivation is skipped and this string is used as the key to decrypt the ticket instead. |

# (4) GetPID
This is the reverse of the [GetName](#5-getname) method. It looks up the pid that belongs to a given username. On all normal accounts the username is the same as the user pid.

Usernames are not case sensitive.

Returns 0 if the username does not exist.

## Request
| Type | Name | Description |
| --- | --- | --- |
| [String] | strUserName | Username |

## Response
| Type | Name | Description |
| --- | --- | --- |
| [PID] | %retval% | PID |

# (5) GetName
This is the reverse of the [GetPID](#4-getpid) method. It returns the name associated with the given user pid. Returns an empty string if the pid does not exist.

## Request
| Type | Name | Description |
| --- | --- | --- |
| [PID] | id | PID |

## Response
| Type | Name | Description |
| --- | --- | --- |
| [String] | %retval% | Username |

# (6) LoginWithContext
## Request
| Type | Name | Description |
| --- | --- | --- |
| [Any] | loginData | Login data |

## Response
| Type | Name | Description |
| --- | --- | --- |
| [Result] | %retval% | Result code |
| [PID] | pidPrincipal | User pid |
| [Buffer] | pbufResponse | [Kerberos ticket](Kerberos-Authentication#kerberos-ticket) |
| [RVConnectionData] | pConnectionData | Connection info for secure server |

# (6) ValidateAndRequestTicketWithParam
## Request
| Type | Name |
| --- | --- |
| [ValidateAndRequestTicketParam](#validateandrequestticketparam-structure) | param |

### ValidateAndRequestTicketParam ([Structure])
| Type | Name | Description |
| --- | --- | --- |
| Uint32 | platformType | Always 3 |
| [String] | userName | Username (your pid) |
| [Any] | extraData | [NullData](#nulldata-structure) or [AuthenticationInfo](#authenticationinfo-structure) |
| Bool | ignoreApiVersionCheck | |
| Uint32 | apiVersionGeneral | NEX version (e.g. 40601) |
| Uint32 | apiVersionCustom | Client version |

### NullData ([Structure])
| This structure inherits from [Data] |
| --- |

This struct does not have any fields.

## Response
| Type | Name |
| --- | --- |
| [ValidateAndRequestTicketResult](#validateandrequestticketparam-structure) | result |

### ValidateAndRequestTicketResult ([Structure])
| Type | Name | Description |
| --- | --- | --- |
| [PID] | sourcePid | User id |
| [Buffer] | bufResponse | [Kerberos ticket](Kerberos-Authentication#kerberos-ticket) |
| [StationURL] | serviceNodeUrl | Secure server location |
| [DateTime] | currentUtcTime | Server time |
| [String] | returnMsg | Server build name |
| [String] | sourceKey | Kerberos key. If present, key derivation is skipped and this key is used to decrypt the ticket instead. |

[Result]: NEX-Common-Types#result
[String]: NEX-Common-Types#string
[Buffer]: NEX-Common-Types#buffer
[Structure]: NEX-Common-Types#structure
[StationURL]: NEX-Common-Types#stationurl
[List]: NEX-Common-Types#list
[PID]: NEX-Common-Types#pid
[DateTime]: NEX-Common-Types#datetime
[Data]: NEX-Common-Types#data-structure
[Any]: NEX-Common-Types#anydataholder
[RVConnectionData]: NEX-Common-Types#rvconnectiondata-structure
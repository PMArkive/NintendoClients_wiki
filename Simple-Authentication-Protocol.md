## [[NEX Protocols]] > Simple Authentication (16)

| Method ID | Method Name |
| --- | --- |
| 1 | [Authenticate](#1-authenticate) |
| 2 | [LoginWithToken](#2-loginwithtoken) |
| 3 | [LoginWithTokenEx](#3-loginwithtokenex) |
| 4 | [Login](#4-login) |
| 5 | [LoginWithSubAccount](#5-loginwithsubaccount) |
| 6 | [Register](#6-register) |
| 7 | [RegisterEx](#7-registerex) |
| 8 | [LoginWithTokenCafe](#8-loginwithtokencafe) |
| 9 | [LoginWithTokenCafeEx](#9-loginwithtokencafeex) |

# (1) Authenticate
## Request
| Type | Name |
| --- | --- |
| [String] | strUserName |

## Response
| Type | Name |
| --- | --- |
| [Result] | %retval% |
| Uint32 | pidPrincipal |
| [RVConnectionData] | pConnectionData |
| [String] | strReturnMsg |

# (2) LoginWithToken
## Request
| Type | Name |
| --- | --- |
| [String] | strToken |

## Response
| Type | Name |
| --- | --- |
| [Result] | %retval% |
| Uint32 | pidPrincipal |
| [RVConnectionData] | pConnectionData |
| [String] | strReturnMsg |

# (3) LoginWithTokenEx
## Request
| Type | Name |
| --- | --- |
| [String] | strToken |
| [Data] | oAnyData |

## Response
| Type | Name |
| --- | --- |
| [Result] | %retval% |
| Uint32 | pidPrincipal |
| [RVConnectionData] | pConnectionData |
| [String] | strReturnMsg |

# (4) Login
## Request
| Type | Name |
| --- | --- |
| [String] | strUsername |
| [String] | strPassword |

## Response
| Type | Name |
| --- | --- |
| [Result] | %retval% |
| Uint32 | pidPrincipal |
| [RVConnectionData] | pConnectionData |
| [String] | strReturnMsg |

# (5) LoginWithSubAccount
## Request
| Type | Name |
| --- | --- |
| [Data] | loginData |

## Response
| Type | Name |
| --- | --- |
| [Result] | %retval% |
| Uint32 | pidPrincipal |
| [RVConnectionData] | pConnectionData |
| [String] | strReturnMsg |

# (6) Register
## Request
| Type | Name |
| --- | --- |
| [List]&lt;[StationURL]&gt; | vecMyURLs |

## Response
| Type | Name |
| --- | --- |
| [Result] | %retval% |
| Uint32 | pidConnectionID |
| [StationURL] | urlPublic |

# (7) RegisterEx
## Request
| Type | Name |
| --- | --- |
| [List]&lt;[StationURL]&gt; | vecMyURLs |
| [Data] | hCustomData |

## Response
| Type | Name |
| --- | --- |
| [Result] | %retval% |
| Uint32 | pidConnectionID |
| [StationURL] | urlPublic |

# (8) LoginWithTokenCafe
## Request
| Type | Name |
| --- | --- |
| [String] | strNintendoToken |

## Response
| Type | Name |
| --- | --- |
| [Result] | %retval% |
| Uint32 | pidPrincipal |
| [RVConnectionData] | pConnectionData |
| [String] | strReturnMsg |

# (9) LoginWithTokenCafeEx
## Request
| Type | Name |
| --- | --- |
| [String] | strNintendoToken |
| [Data] | oAnyData |

## Response
| Type | Name |
| --- | --- |
| [Result] | %retval% |
| Uint32 | pidPrincipal |
| [RVConnectionData] | pConnectionData |
| [String] | strReturnMsg |

[Result]: NEX-Common-Types#result
[String]: NEX-Common-Types#string
[Buffer]: NEX-Common-Types#buffer
[qBuffer]: NEX-Common-Types#qbuffer
[List]: NEX-Common-Types#list
[Map]: NEX-Common-Types#map
[DateTime]: NEX-Common-Types#datetime
[Structure]: NEX-Common-Types#structure
[Data]: NEX-Common-Types#anydataholder
[StationURL]: NEX-Common-Types#stationurl
[Variant]: NEX-Common-Types#variant
[RVConnectionData]: NEX-Common-Types#rvconnectiondata-structure
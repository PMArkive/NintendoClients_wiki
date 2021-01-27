## [[NEX Protocols]] > User Storage Admin

| Method ID | Method Name |
| --- | --- |
| 1 | [GetContentsToModerate](#1-getcontentstomoderate) |
| 2 | [FlagContentAsVerified](#2-flagcontentasverified) |
| 3 | [BanContent](#3-bancontent) |
| 4 | [BanUser](#4-banuser) |
| 5 | [BanUserFromContentType](#5-banuserfromcontenttype) |
| 6 | [UnbanUser](#6-unbanuser) |
| 7 | [UnbanUserFromContentType](#7-unbanuserfromcontenttype) |
| 8 | [GetContentsToModerateWithThreshold](#8-getcontentstomoderatewiththreshold) |
| 9 | [UpdateMetaData](#9-updatemetadata) |

# (1) GetContentsToModerate
## Request
| Type | Name |
| --- | --- |
| Uint32 | typeID |
| Uint32 | offset |
| Uint32 | size |

## Response
| Type | Name |
| --- | --- |
| [List]&lt;[UserContent](User-Content-Protocol#usercontent-structure)&gt; | contents |
| Uint32 | totalResults |

# (2) FlagContentAsVerified
## Request
| Type | Name |
| --- | --- |
| [UserContentKey](User-Content-Protocol#usercontentkey-structure) | contentKey |

## Response
This method does not return anything.

# (3) BanContent
## Request
| Type | Name |
| --- | --- |
| [UserContentKey](User-Content-Protocol#usercontentkey-structure) | contentKey |

## Response
This method does not return anything.

# (4) BanUser
## Request
| Type | Name |
| --- | --- |
| Uint32 | pid |
| [String] | reason |
| Bool | banContents |
| [DateTime] | expireDate |

## Response
This method does not return anything.

# (5) BanUserFromContentType
## Request
| Type | Name |
| --- | --- |
| Uint32 | typeID |
| Uint32 | pid |
| [String] | reason |
| Bool | banContents |
| [DateTime] | expireDate |

## Response
This method does not return anything.

# (6) UnbanUser
## Request
| Type | Name |
| --- | --- |
| Uint32 | pid |

## Response
This method does not return anything.

# (7) UnbanUserFromContentType
## Request
| Type | Name |
| --- | --- |
| Uint32 | typeID |
| Uint32 | pid |

## Response
This method does not return anything.

# (8) GetContentsToModerateWithThreshold
## Request
| Type | Name |
| --- | --- |
| Uint32 | typeID |
| Uint32 | threshold |
| Uint32 | offset |
| Uint32 | size |

## Response
| Type | Name |
| --- | --- |
| [List]&lt;[UserContent](User-Content-Protocol#usercontent-structure)&gt; | contents |
| Uint32 | totalResults |

# (9) UpdateMetaData
## Request
| Type | Name |
| --- | --- |
| [UserContentKey](User-Content-Protocol#usercontentkey-structure) | contentKey |
| [List]&lt;[ContentProperty](User-Content-Protocol#contentproperty-structure)&gt; | properties |

## Response
This method does not return anything.

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
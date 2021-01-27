## [[NEX Protocols]] > Privileges (35)

| Method ID | Method Name |
| --- | --- |
| 1 | [GetPrivileges](#1-getprivileges) |
| 2 | [ActivateKey](#2-activatekey) |
| 3 | [ActivateKeyWithExpectedPrivileges](#3-activatekeywithexpectedprivileges) |
| 4 | [GetPrivilegeRemainDuration](#4-getprivilegeremainduration) |
| 5 | [GetExpiredPrivileges](#5-getexpiredprivileges) |
| 6 | [GetPrivilegesEx](#6-getprivilegesex) |

# (1) GetPrivileges
## Request
| Type | Name |
| --- | --- |
| [String] | localeCode |

## Response
| Type | Name |
| --- | --- |
| [Map]&lt;Uint32, [Privilege]&gt; | privileges |

# (2) ActivateKey
## Request
| Type | Name |
| --- | --- |
| [String] | uniqueKey |
| [String] | languageCode |

## Response
| Type | Name |
| --- | --- |
| [PrivilegeGroup] | privilege |

# (3) ActivateKeyWithExpectedPrivileges
## Request
| Type | Name |
| --- | --- |
| [String] | uniqueKey |
| [String] | languageCode |
| [List]&lt;Uint32&gt; | expectedPrivilegeIDs |

## Response
| Type | Name |
| --- | --- |
| [PrivilegeGroup] | privilege |

# (4) GetPrivilegeRemainDuration
## Request
| Type | Name |
| --- | --- |
| Uint32 | privilegeID |

## Response
| Type | Name |
| --- | --- |
| Sint32 | seconds |

# (5) GetExpiredPrivileges
## Request
This method does not take any parameters.

## Response
| Type | Name |
| --- | --- |
| [List]&lt;[PrivilegeEx]&gt; | expiredPrivileges |

# (6) GetPrivilegesEx
## Request
| Type | Name |
| --- | --- |
| [String] | localeCode |

## Response
| Type | Name |
| --- | --- |
| [List]&lt;[PrivilegeEx]&gt; | privilegesEx |

# Types
## Privilege ([Structure])
| Type | Name |
| --- | --- |
| Uint32 | m_ID |
| [String] | m_description |

## PrivilegeEx ([Structure])
| Type | Name |
| --- | --- |
| Uint32 | m_ID |
| [String] | m_description |
| Sint32 | m_duration |

## PrivilegeGroup ([Structure])
| Type | Name |
| --- | --- |
| [String] | m_description |
| [List]&lt;[Privilege]&gt; | m_privileges |

[Result]: NEX-Common-Types#result
[String]: NEX-Common-Types#string
[Buffer]: NEX-Common-Types#buffer
[qBuffer]: NEX-Common-Types#qbuffer
[List]: NEX-Common-Types#list
[Map]: NEX-Common-Types#map
[DateTime]: NEX-Common-Types#date-time
[Structure]: NEX-Common-Types#structure
[Data]: NEX-Common-Types#any-data-holder
[Variant]: NEX-Common-Types#variant

[Privilege]: #privilege-structure
[PrivilegeGroup]: #privilegegroup-structure
[PrivilegeEx]: #privilegeex-structure
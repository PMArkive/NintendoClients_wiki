[[NEX Protocols]] > Tracking 3 (36)
---

| Method ID | Method Name |
| --- | --- |
| 1 | [SendTag](#1-sendtag) |
| 2 | [SendTagAndUpdateUserInfo](#2-sendtagandupdateuserinfo) |
| 3 | [SendUserInfo](#3-senduserinfo) |
| 4 | [GetConfiguration](#4-getconfiguration) |
| 5 | [SendTags](#5-sendtags) |

# (1) SendTag
## Request
| Type | Name |
| --- | --- |
| Uint32 | trackingID |
| [String] | tag |
| [String] | attributes |
| Uint32 | deltaTime |

## Response
This method does not return anything.

# (2) SendTagAndUpdateUserInfo
## Request
| Type | Name |
| --- | --- |
| Uint32 | trackingID |
| [String] | tag |
| [String] | attributes |
| Uint32 | deltaTime |
| [String] | userID |

## Response
This method does not return anything.

# (3) SendUserInfo
## Request
| Type | Name |
| --- | --- |
| Uint32 | deltaTime |

## Response
| Type | Name |
| --- | --- |
| [TrackingInformation] | userInfo |
| Uint32 | trackingID |

# (4) GetConfiguration
## Request
This method does not take any parameters.

## Response
| Type | Name |
| --- | --- |
| [List]&lt;[String]&gt; | tags |

# (5) SendTags
## Request
| Type | Name |
| --- | --- |
| [List]&lt;[TrackingTag]&gt; | tagData |

## Response
This method does not return anything.

# Types
## TrackingInformation ([Structure])
| Type | Name |
| --- | --- |
| Uint32 | ipn |
| [String] | userID |
| [String] | machineID |
| [String] | visitorID |
| [String] | utsVersion |

## TrackingTag ([Structure])
| Type | Name |
| --- | --- |
| Uint32 | trackingID |
| [String] | tag |
| [String] | attributes |
| Uint32 | deltaTime |
| [String] | newUserId |

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

[TrackingInformation]: #trackinginformation-structure
[TrackingTag]: #trackingtag-structure
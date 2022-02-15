## [[NEX Protocols]] > [Matchmake Extension](Matchmake-Extension-Protocol) > MK8 (109)

This page describes the methods that are only seen in Mario Kart 8.

Methods 36 - 39 and 41 belong to the SimpleSearchProtocol instead of the MatchmakeExtensionProtocol.

| Method ID | Method Name |
| --- | --- |
| 36 | [CreateSimpleSearchObject](#36-createsimplesearchobject) |
| 37 | [UpdateSimpleSearchObject](#37-updatesimplesearchobject) |
| 38 | [DeleteSimpleSearchObject](#38-deletesimplesearchobject) |
| 39 | [SearchSimpleSearchObject](#39-searchsimplesearchobject) |
| 40 | JoinMatchmakeSessionWithExtraParticipants |
| 41 | [SearchSimpleSearchObjectByObjectIds](#41-searchsimplesearchobjectbyobjectids) |

# (36) CreateSimpleSearchObject
## Request
| Type | Description |
| --- | --- |
| [SimpleSearchObject] | Object |

## Response
| Type | Description |
| --- | --- |
| Uint32 | Object id |

# (37) UpdateSimpleSearchObject
## Request
| Type | Description |
| --- | --- |
| Uint32 | Object id |
| [SimpleSearchObject] | New object |

## Response
This method does not return anything.

# (38) DeleteSimpleSearchObject
## Request
| Type | Description |
| --- | --- |
| Uint32 | Object id |

## Response
This method does not return anything.

# (39) SearchSimpleSearchObject
## Request
| Type | Description |
| --- | --- |
| [SimpleSearchParam] | Param |

## Response
| Type | Description |
| --- | --- |
| [List]&lt;[SimpleSearchObject]&gt; | Objects |

# (41) SearchSimpleSearchObjectByObjectIds
## Request
| Type | Description |
| --- | --- |
| [List]&lt;Uint32&gt; | Object ids |

## Response
| Type | Description |
| --- | --- |
| [List]&lt;[SimpleSearchObject]&gt; | Objects |

# Types
## SimpleSearchObject ([Structure])
| Type | Description |
| --- | --- |
| Uint32 | Unknown |
| [PID] | Unknown |
| [List]&lt;Uint32&gt; | Attributes |
| [qBuffer] | Unknown |
| Uint32 | Unknown |
| [String] | Unknown |
| [SimpleSearchDateTimeAttribute] | Datetime attribute |

## SimpleSearchDateTimeAttribute ([Structure])
| Type | Description |
| --- | --- |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| [DateTime] | Unknown |
| [DateTime] | Unknown |

## SimpleSearchParam ([Structure])
| Type | Description |
| --- | --- |
| Uint32 | Unknown |
| [PID] | Unknown |
| [List]&lt;[SimpleSearchCondition]&gt; | Conditions |
| [String] | Unknown |
| [ResultRange] | Result range |
| [DateTime] | Unknown |

## SimpleSearchCondition ([Structure])
| Type | Description |
| --- | --- |
| Uint32 | Value |
| Uint32 | Comparison operator |

[String]: NEX-Common-Types#string
[Data]: NEX-Common-Types#anydataholder
[List]: NEX-Common-Types#list
[DateTime]: NEX-Common-Types#datetime
[Buffer]: NEX-Common-Types#buffer
[qBuffer]: NEX-Common-Types#qbuffer
[PID]: NEX-Common-Types#pid
[Structure]: NEX-Common-Types#structure
[ResultRange]: NEX-Common-Types#resultrange-structure

[SimpleSearchObject]: #simplesearchobject-structure
[SimpleSearchDateTimeAttribute]: #simplesearchdatetimeattribute-structure
[SimpleSearchParam]: #simplesearchparam-structure
[SimpleSearchCondition]: #simplesearchcondition-structure
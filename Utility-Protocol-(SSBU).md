## [[NEX Protocols]] > [Utility](Utility-Protocol) > SSBU (110)

This page describes the methods that are only seen in SSBU.

| Method ID | Method Name |
| --- | --- |
| 9 | [Unknown](#9-unknown) |
| 10 | [Unknown](#10-unknown) |
| 11 | [GetGameEvents](#11-getgameevents) |

# (9) Unknown
## Request
| Type | Description |
| --- | --- |
| [MethodParam9](#methodparam9-structure) | Param |

## Response
| Type | Description |
| --- | --- |
| [UnknownStruct](#unknownstruct-structure) | Unknown |

# (10) Unknown
## Request
| Type | Description |
| --- | --- |
| [MethodParam10](#methodparam10-structure) | Param |

## Response
| Type | Description |
| --- | --- |
| [UnknownStruct2](#unknownstruct2-structure) | Param |

# (11) GetGameEvents
## Request
| Type | Description |
| --- | --- |
| [GetGameEventsParam](#getgameeventsparam-structure) | Param |

## Response
| Type | Description |
| --- | --- |
| [List]&lt;[GameEvent](#gameevent-structure)&gt; | Game events |

# Types
## GameEvent ([Structure])
| Type | Description |
| --- | --- |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint16 | Unknown |
| [String] | Unknown |
| [String] | Unknown |
| [DateTime] | Unknown |
| [DateTime] | Unknown |
| [DateTime] | Unknown |
| [DateTime] | Unknown |
| [Map]&lt;[String], [Variant]&gt; | Unknown |
| [Map]&lt;[String], [List]&lt;[Variant]&gt;&gt; | Unknown |
| [List]&lt;[GameEventPeriod](#gameeventperiod-structure)&gt; | Periods |

## GameEventPeriod ([Structure])
| Type | Description |
| --- | --- |
| Uint32 | Unknown |
| Uint32 | Unknown |
| [DateTime] | Unknown |
| [DateTime] | Unknown |
| [Map]&lt;[String], [Variant]&gt; | Unknown |
| [Map]&lt;[String], [List]&lt;[Variant]&gt;&gt; | Unknown |
| Uint32 | Unknown |

## GetGameEventsParam ([Structure])
| Type | Description |
| --- | --- |
| Uint32 | Unknown |
| [String] | Unknown |

## MethodParam9 ([Structure])
| Type | Description |
| --- | --- |
| Uint32 | Unknown |
| Uint32 | Unknown |
| [String] | Unknown |

## MethodParam10 ([Structure])
| Type | Description |
| --- | --- |
| [UnknownStruct](#unknownstruct-structure) | Unknown |
| Uint32 | Unknown |

## UnknownStruct ([Structure])
| Type | Description |
| --- | --- |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |

## UnknownStruct2 ([Structure])
| Type | Description |
| --- | --- |
| Bool | Unknown |
| Uint32 | Unknown |

[Result]: NEX-Common-Types#result
[String]: NEX-Common-Types#string
[Buffer]: NEX-Common-Types#buffer
[qBuffer]: NEX-Common-Types#qbuffer
[List]: NEX-Common-Types#list
[Map]: NEX-Common-Types#map
[Variant]: NEX-Common-Types#variant
[DateTime]: NEX-Common-Types#datetime
[Structure]: NEX-Common-Types#structure
[Data]: NEX-Common-Types#anydataholder
[PID]: NEX-Common-Types#pid
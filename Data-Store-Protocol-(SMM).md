## [[NEX Protocols]] > [Data Store (0x73)](Data-Store-Protocol) > SMM

This page describes the methods that are only seen in Super Mario Maker. Most method and structure names listed here are not the official names, they are merely guesses. This page is very incomplete. Any help would be appreciated.

| Method ID | Method Name |
| --- | --- |
| 45 | [GetFileServerObjectInfos](#45-getfileserverobjectinfos) |
| 46 | ? |
| 47 | ? |
| 48 | ? |
| 49 | ? |
| 50 | [GetInfoStuff](#50-getinfostuff) |
| 51 | ? |
| 52 | ? |
| 53 | ? |
| 54 | ? |
| 55 | ? |
| 56 | ? |
| 57 | [CompletePostObjectEx](#57-completepostobjectex) |
| 58 | ? |
| 59 | ? |
| 60 | ? |
| 61 | ? |
| 62 | ? |
| 63 | ? |
| 64 | ? |
| 65 | ? |
| 66 | ? |
| 67 | ? |
| 68 | ? |
| 69 | ? |
| 70 | ? |
| 71 | ? |
| 72 | ? |
| 73 | ? |
| 74 | ? |
| 75 | ? |
| 76 | ? |
| 77 | ? |
| 78 | ? |
| 79 | ? |
| 80 | ? |
| 81 | ? |
| 82 | [Method82](#method-82) |
| 83 | ? |
| 84 | ? |
| 85 | ? |
| 86 | ? |
| 87 | [Method87](#87-method87) |

# (45) GetFileServerObjectInfos
## Request
| Type | Description |
| --- | --- |
| [List]&lt;Uint64&gt; | Object ids |

## Response
| Type | Description |
| --- | --- |
| [List]&lt;[DataStoreFileServerObjectInfo](#datastorefileserverobjectinfo)&gt; | Object infos |

# (48) Method48
## Request
| Type | Description |
| --- | --- |
| [List]&lt;[UnknownStruct6]&gt; | Unknown |

## Response
This method does not return anything.

# (49) Method49
## Request
| Type | Description |
| --- | --- |
| [MethodParam49](#methodparam49-structure) | Unknown |

## Response
| Type | Description |
| --- | --- |
| [List]&lt;[DataStoreInfoStuff]&gt; | Infos |
| [List]&lt;[Result]&gt; | Result codes |

# (50) Method50
## Request
| Type | Description |
| --- | --- |
| [MethodParam50](#methodparam50-structure) | Param |

## Response
| Type | Description |
| --- | --- |
| [List]&lt;[DataStoreInfoStuff]&gt; | Infos |
| [List]&lt;[Result]&gt; | Result codes |

# (53) Method53
## Request
| Type | Description |
| --- | --- |
| [List]&lt;[UnknownStruct4]&gt; | Unknown |
| [List]&lt;[qBuffer]&gt; | Unknown |

## Response
| Type | Description |
| --- | --- |
| [List]&lt;[Result]&gt; | Results |

# (54) Method54
## Request
| Type | Description |
| --- | --- |
| [UnknownStruct4] | Unknown |

## Response
| Type | Description |
| --- | --- |
| [List]&lt;[qBuffer]&gt; | Unknown |

# (57) CompletePostObjectEx
## Request
| Type | Description |
| --- | --- |
| [DataStoreCompletePostParam] | Complete post param |

## Response
| Type | Description |
| --- | --- |
| [String] | Unknown |

# (59) Method59
## Request
| Type | Description |
| --- | --- |
| [MethodParam59](#methodparam59-structure) | Param |

## Response
| Type | Description |
| --- | --- |
| [DataStoreReqPostInfo] | POST request info |

# (60) Method60
## Request
| Type | Description |
| --- | --- |
| Uint32 | Unknown |
| [DataStoreMetaRelated] | Unknown |
| [DataStoreChangeMetaCompareParam] | Compare param |

## Response
| Type | Description |
| --- | --- |
| [List]&lt;[DataStoreInfoStuff]&gt; | Infos |

# (61) Method61
## Request
| Type | Description |
| --- | --- |
| Uint32 | Unknown |

## Response
| Type | Description |
| --- | --- |
| [List]&lt;Uint32&gt; | Unknown |

# (64) Method64
## Request
| Type | Description |
| --- | --- |
| [DataStoreMetaRelated] | Unknown |
| [DataStoreChangeMetaCompareParam] | Compare param |

## Response
| Type | Description |
| --- | --- |
| [List]&lt;[DataStoreInfoStuff]&gt; | Infos |

# (65) Method65
## Request
| Type | Description |
| --- | --- |
| [DataStoreMetaRelated] | Unknown |
| [DataStoreChangeMetaCompareParam] | Compare param |

## Response
| Type | Description |
| --- | --- |
| [List]&lt;[DataStoreInfoStuff]&gt; | Infos |

# (66) Method66
## Request
| Type | Description |
| --- | --- |
| [DataStoreMetaRelated] | Unknown |
| [DataStoreChangeMetaCompareParam] | Compare param |

## Response
| Type | Description |
| --- | --- |
| [List]&lt;[DataStoreInfoStuff]&gt; | Infos |

# (67) Method67
## Request
| Type | Description |
| --- | --- |
| [DataStoreMetaRelated] | Unknown |
| [DataStoreChangeMetaCompareParam] | Compare param |

## Response
| Type | Description |
| --- | --- |
| [List]&lt;[DataStoreInfoStuff]&gt; | Infos |

# (68) Method68
## Request
| Type | Description |
| --- | --- |
| [DataStoreMetaRelated] | Unknown |
| [DataStoreChangeMetaCompareParam] | Compare param |

## Response
| Type | Description |
| --- | --- |
| [List]&lt;[DataStoreInfoStuff]&gt; | Infos |

# (71) Method71
## Request
| Type | Description |
| --- | --- |
| [MethodParam71](#methodparam71-structure) | Param |

## Response
This method does not return anything.

# (72) Method72
## Request
| Type | Description |
| --- | --- |
| [UnknownStruct2] | Unknown |

## Response
| Type | Description |
| --- | --- |
| [UnknownStruct3] | Unknown |

# (74) Method74
## Request
| Type | Description |
| --- | --- |
| Uint32 | Unknown |

## Response
| Type | Description |
| --- | --- |
| [List]&lt;[String]&gt; | Unknown |

# (76) Method76
## Request
| Type | Description |
| --- | --- |
| [List]&lt;Uint64&gt; | Unknown |

## Response
| Type | Description |
| --- | --- |
| [List]&lt;Uint32&gt; | Unknown |

# (78) Method78
## Request
| Type | Description |
| --- | --- |
| [List]&lt;[UnknownStruct2]&gt; | Unknown |
| [DataStoreGetMetaParam] | Get meta param |

## Response
| [List]&lt;[DataStoreMetaInfo]&gt; | Meta infos |
| [List]&lt;[UnknownStruct3]&gt; | Unknown |
| [List]&lt;[Result]&gt; | Results |

# (79) Method79
## Request
| Type | Description |
| --- | --- |
| Uint32 | Unknown |

## Response
| Type | Description |
| --- | --- |
| Bool | Unknown |

# (81) Method81
## Request
| Type | Description |
| --- | --- |
| [DataStoreMetaRelated] | Unknown |
| [DataStoreChangeMetaCompareParam] | Compare param |

## Response
| Type | Description |
| --- | --- |
| [List]&lt;[DataStoreInfoStuff]&gt; | Unknown |

# (82) Method82
## Request
| Type | Description |
| --- | --- |
| [DataStoreMetaRelated] | Unknown |
| [DataStoreChangeMetaCompareParam] | Compare param |

## Response
| Type | Description |
| --- | --- |
| [List]&lt;[DataStoreInfoStuff]&gt; | Unknown |

# (87) Method87
## Request
| Type | Description |
| --- | --- |
| [MethodParam87](#methodparam87-structure) | 

## Response
This method does not return anything.

# Types
## DataStoreFileServerObjectInfo ([Structure])
| Type | Description |
| --- | --- |
| Uint64 | Unknown |
| [DataStoreReqGetInfo] | GET request info |

## DataStoreInfoStuff ([Structure])
| Type | Description |
| --- | --- |
| Uint32 | Unknown |
| Uint32 | Unknown |
| [DataStoreMetaInfo] | Meta info |

## DataStoreMetaRelated ([Structure])
| Type | Description |
| --- | --- |
| Uint8 | Unknown |
| [List]&lt;Uint32&gt; | Unknown |
| Uint8 | Unknown |
| [List]&lt;Uint32&gt; | Unknown |
| Uint16 | Unknown |
| [DateTime] | Unknown |
| [DateTime] | Unknown |
| [DateTime] | Unknown |
| [DateTime] | Unknown |
| Uint32 | Unknown |
| [DataStoreChangeMetaCompareParam] | Compare param |
| Uint8 | Unknown |
| Uint8 | Unknown |
| [UnknownStruct] | Unknown |
| Uint8 | Unknown |
| Uint32 | Unknown |
| Bool | Unknown |

## MethodParam49 ([Structure])
| Type | Description |
| --- | --- |
| Uint32 | Unknown |
| [UnknownStruct5] | Unknown |
| Uint8 | Unknown |
| [UnknownStruct] | Unknown |

## MethodParam50 ([Structure])
| Type | Description |
| --- | --- |
| Uint32 | Unknown |
| [List]&lt;Uint64&gt; | Unknown |
| Uint8 | Unknown |

## MethodParam59 ([Structure])
| Type | Description |
| --- | --- |
| [DataStorePreparePostParam] | Prepare post param |
| Uint64 | Unknown |
| [String] | Unknown |

## MethodParam71 ([Structure])
| Type | Description |
| --- | --- |
| Uint64 | Unknown |
| Uint8 | Unknown |
| Uint32 | Unknown |

## MethodParam87 ([Structure])
| Type | Description |
| --- | --- |
| Uint64 | Unknown |
| [String] | Unknown |
| Uint8 | Unknown |
| [String] | Unknown |

## UnknownStruct ([Structure])
| Type | Description |
| --- | --- |
| Uint32 | Unknown |
| Uint32 | Unknown |

## UnknownStruct2 ([Structure])
| Type | Description |
| --- | --- |
| Uint64 | Unknown |
| Uint8 | Unknown |

## UnknownStruct3 ([Structure])
| Type | Description |
| --- | --- |
| Uint64 | Unknown |
| Uint8 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| [DateTime] | Unknown |
| [DateTime] | Unknown |

## UnknownStruct4 ([Structure])
| Type | Description |
| --- | --- |
| Uint64 | Unknown |
| Uint32 | Unknown |

## UnknownStruct5 ([Structure])
| Type | Description |
| --- | --- |
| Uint8 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |

## UnknownStruct6 ([Structure])
| Type | Description |
| --- | --- |
| Uint64 | Unknown |
| Uint32 | Unknown |
| Uint32 | Unknown |
| Uint16 | Unknown |

[DataStoreMetaRelated]: #datestoremetarelated-struct
[DataStoreInfoStuff]: #datastoreinfostuff-structure
[UnknownStruct]: #unknownstruct-struct
[UnknownStruct2]: #unknownstruct2-struct
[UnknownStruct3]: #unknownstruct3-struct
[UnknownStruct4]: #unknownstruct4-struct
[UnknownStruct5]: #unknownstruct5-struct
[UnknownStruct6]: #unknownstruct6-struct

[DataStoreChangeMetaCompareParam]: Data-Store-Protocol#datastorechangemetacompareparam-structure
[DataStoreGetMetaParam]: Data-Store-Protocol#datastoregetmetaparam-structure
[DataStorePreparePostParam]: Data-Store-Protocol#datastorepreparepostparam-structure
[DataStoreCompletePostParam]: Data-Store-Protocol#datastorecompletepostparam-structure
[DataStoreReqGetInfo]: Data-Store-Protocol#datastorereqgetinfo-structure
[DataStoreReqPostInfo]: Data-Store-Protocol#datastorereqpostinfo-structure
[DataStoreMetaInfo]: Data-Store-Protocol#datastoremetainfo-structure

[Result]: NEX-Common-Types#result
[String]: NEX-Common-Types#string
[Buffer]: NEX-Common-Types#buffer
[qBuffer]: NEX-Common-Types#qbuffer
[List]: NEX-Common-Types#list
[Map]: NEX-Common-Types#map
[DateTime]: NEX-Common-Types#date-time
[Structure]: NEX-Common-Types#structure
[Data]: NEX-Common-Types#any-data-holder
[PID]: NEX-Common-Types#pid
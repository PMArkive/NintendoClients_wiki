## [[NEX Protocols]] > News (31)

| Method ID | Method Name |
| --- | --- |
| 1 | [GetChannels](#1-getchannels) |
| 2 | [GetChannelsByTypes](#2-getchannelsbytypes) |
| 3 | [GetSubscribableChannels](#3-getsubscribablechannels) |
| 4 | [GetChannelsByIDs](#4-getchannelsbyids) |
| 5 | [GetSubscribedChannels](#5-getsubscribedchannels) |
| 6 | [SubscribeChannel](#6-subscribechannel) |
| 7 | [UnsubscribeChannel](#7-unsubscribechannel) |
| 8 | [GetNewsHeaders](#8-getnewsheaders) |
| 9 | [GetNewsMessages](#9-getnewsmessages) |
| 10 | [GetNumberOfNews](#10-getnumberofnews) |
| 11 | [GetChannelByType](#11-getchannelbytype) |
| 12 | [GetNewsHeadersByType](#12-getnewsheadersbytype) |
| 13 | [GetNewsMessagesByType](#13-getnewsmessagesbytype) |

# (1) GetChannels
## Request
| Type | Name |
| --- | --- |
| [ResultRange](NEX-Common-Types#resultrange-structure) | resultRange |

## Response
| Type | Name |
| --- | --- |
| [List]&lt;[NewsChannel]&gt; | channels |

# (2) GetChannelsByTypes
## Request
| Type | Name |
| --- | --- |
| [List]&lt;[String]&gt; | newsChannelTypes |
| [ResultRange](NEX-Common-Types#resultrange-structure) | resultRange |

## Response
| Type | Name |
| --- | --- |
| [List]&lt;[NewsChannel]&gt; | channels |

# (3) GetSubscribableChannels
## Request
| Type | Name |
| --- | --- |
| [ResultRange](NEX-Common-Types#resultrange-structure) | resultRange |

## Response
| Type | Name |
| --- | --- |
| [List]&lt;[NewsChannel]&gt; | channels |

# (4) GetChannelsByIDs
## Request
| Type | Name |
| --- | --- |
| [List]&lt;Uint32&gt; | newsChannelIDs |

## Response
| Type | Name |
| --- | --- |
| [List]&lt;[NewsChannel]&gt; | channels |

# (5) GetSubscribedChannels
## Request
| Type | Name |
| --- | --- |
| [ResultRange](NEX-Common-Types#resultrange-structure) | resultRange |

## Response
| Type | Name |
| --- | --- |
| [List]&lt;[NewsChannel]&gt; | channels |

# (6) SubscribeChannel
## Request
| Type | Name |
| --- | --- |
| Uint32 | newsChannelID |

## Response
This method does not return anything.

# (7) UnsubscribeChannel
## Request
| Type | Name |
| --- | --- |
| Uint32 | newsChannelID |

## Response
This method does not return anything.

# (8) GetNewsHeaders
## Request
| Type | Name |
| --- | --- |
| [NewsRecipient] | recipient |
| [ResultRange](NEX-Common-Types#resultrange-structure) | range |

## Response
| Type | Name |
| --- | --- |
| [List]&lt;[NewsHeader]&gt; | newsHeaders |

# (9) GetNewsMessages
## Request
| Type | Name |
| --- | --- |
| [List]&lt;Uint32&gt; | newsMessageIDs |

## Response
| Type | Name |
| --- | --- |
| [List]&lt;[NewsMessage]&gt; | newsMessages |

# (10) GetNumberOfNews
## Request
| Type | Name |
| --- | --- |
| [NewsRecipient] | recipient |

## Response
| Type | Name |
| --- | --- |
| Uint32 | numberOfNews |

# (11) GetChannelByType
## Request
| Type | Name |
| --- | --- |
| [String] | newsChannelType |

## Response
| Type | Name |
| --- | --- |
| [NewsChannel] | channel |

# (12) GetNewsHeadersByType
## Request
| Type | Name |
| --- | --- |
| [String] | newsChannelType |
| [ResultRange](NEX-Common-Types#resultrange-structure) | range |

## Response
| Type | Name |
| --- | --- |
| [List]&lt;[NewsHeader]&gt; | newsHeaders |

# (13) GetNewsMessagesByType
## Request
| Type | Name |
| --- | --- |
| [String] | newsChannelType |
| [ResultRange](NEX-Common-Types#resultrange-structure) | range |

## Response
| Type | Name |
| --- | --- |
| [List]&lt;[NewsMessage]&gt; | newsMessages |

# Types
## NewsChannel ([Structure])
| Type | Name |
| --- | --- |
| Uint32 | m_ID |
| Uint32 | m_ownerPID |
| [String] | m_name |
| [String] | m_description |
| [DateTime] | m_creationTime |
| [DateTime] | m_expirationTime |
| [String] | m_type |
| [String] | m_locale |
| Bool | m_subscribable |

## NewsHeader ([Structure])
| Type | Name |
| --- | --- |
| Uint32 | m_ID |
| Uint32 | m_recipientID |
| Uint32 | m_recipientType |
| Uint32 | m_publisherPID |
| [String] | m_publisherName |
| [DateTime] | m_publicationTime |
| [DateTime] | m_displayTime |
| [DateTime] | m_expirationTime |
| [String] | m_title |
| [String] | m_link |

## NewsMessage ([Structure])
| Type | Name |
| --- | --- |
| [String] | m_body |

## NewsRecipient ([Structure])
| Type | Name |
| --- | --- |
| Uint32 | m_recipientID |
| Uint32 | m_recipientType |

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

[NewsChannel]: #newschannel-structure
[NewsRecipient]: #newsrecipient-structure
[NewsHeader]: #newsheader-structure
[NewsMessage]: #newsmessage-structure
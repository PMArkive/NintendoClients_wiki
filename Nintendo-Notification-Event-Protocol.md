## [[NEX Protocols]] > Nintendo Notifications (100)

This protocol is used by the 3DS / Wii U friend server for notifications about friends.

There is no known difference between the two methods, except that the server sends some events through method 1 and others through method 2. The client treats them exactly the same.

| Method ID | Method Name |
| --- | --- |
| 1 | [ProcessNintendoNotificationEvent](#processnintendonotificationevent) |
| 2 | [ProcessNintendoNotificationEvent](#processnintendonotificationevent) |

# ProcessNintendoNotificationEvent
## Request
| Type | Description |
| --- | --- |
| [NintendoNotificationEvent](#nintendonotificationevent-structure) | Event object |

## Response
No RMC response is sent.

# Types
## NintendoNotificationEvent ([Structure])
| Type | Name | Description |
| --- | --- | --- |
| Uint32 | m_uiType | [Event type](#friend-events) |
| [PID] | m_pidSender | Pid of the user that triggered the notification event |
| [Data] | m_dataholder | Information about the event (depends on the event type) |

## NintendoNotificationEventGeneral ([Structure])
| This structure inherits from [Data] |
| --- |

| Type | Name |
| --- | --- |
| Uint32 | m_u32Param |
| Uint64 | m_u64Param1 |
| Uint64 | m_u64Param2 |
| [String] | m_strParam |

## NintendoNotificationEventProfile ([Structure])
| This structure inherits from [Data] |
| --- |

| Type | Name |
| --- | --- |
| Uint8 | m_region |
| Uint8 | m_country |
| Uint8 | m_area |
| Uint8 | m_language |
| Uint8 | m_platform |

# Friend Events
| Type | Method | Data Type | Description |
| --- | --- | --- | --- |
| 10 | 1 | [NintendoNotificationEventGeneral] | A friend went offline |
| 21 | 2 | [NNAInfo] | A friend changed or edited their mii |
| 22 | | | Mii related |
| 23 | | [PrincipalPreference] | A friend updated their preferences |
| 24 | 2 | [NintendoPresenceV2] | A friend started a game/app |
| 25 | | | Friend request related |
| 26 | 1 | [NintendoNotificationEventGeneral] | A friend removed you from their from friend list or canceled their friend request |
| 27 | 2 | [FriendRequest] | You received a friend request |
| 28 | | | Friend request related |
| 29 | | | Blacklist related |
| 30 | 1 | [FriendInfo] | You became friends |
| 31 | | | Blacklist related |
| 32 | | | Blacklist related |
| 33 | 1 | [NintendoNotificationEventGeneral] | A friend changed their status message |
| 34 | | | |
| 35 | | | Related to friend relationships |
| 36 | | [PersistentNotificationList] | This seems to delete persistent notifications |

[Data]: NEX-Common-Types#anydataholder
[PID]: NEX-Common-Types#pid
[Structure]: NEX-Common-Types#structure
[String]: NEX-Common-Types#string
[FriendRequest]: Friends-Protocol-(Wii-U)#friendrequest
[NintendoPresenceV2]: Friends-Protocol-(Wii-U)#nintendopresencev2
[FriendInfo]: Friends-Protocol-(Wii-U)#friendinfo
[NNAInfo]: Friends-Protocol-(Wii-U)#nnainfo
[MiiV2]: Friends-Protocol-(Wii-U)#miiv2
[PrincipalPreference]: Friends-Protocol-(Wii-U)#principalpreference
[PersistentNotificationList]: Friends-Protocol-(Wii-U)#persistentnotificationlist
[NintendoNotificationEventGeneral]: #nintendonotificationeventgeneral-structure
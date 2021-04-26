## [[NEX Protocols]] > Notifications (14)

| Method ID | Method Name |
| --- | --- |
| 1 | [ProcessNotificationEvent](#1-processnotificationevent) |

# (1) ProcessNotificationEvent
## Request
| Type | Name | Description |
| --- | --- | --- |
| [NotificationEvent](#notificationevent-structure) | oEvent | Event object |

## Response
No RMC response is sent.

# NotificationEvent ([Structure])
Most notification types are predefined. However, some games also implement their own notification types (see [libeagle](Eagle-Protocol) for example).

**Wii U:**

| Type | Name |
| --- | --- |
| [PID] | m_pidSource |
| Uint32 | m_uiType |
| Uint32 | m_uiParam1 |
| Uint32 | m_uiParam2 |
| [String] | m_strParam |

**Switch:**

The following fields are always present (revision 0 and 1):

| Type | Name |
| --- | --- |
| [PID] | m_pidSource |
| Uint32 | m_uiType |
| Uint64 | m_uiParam1 |
| Uint64 | m_uiParam2 |
| [String] | m_strParam |
| Uint64 | m_uiParam3 |

The following field is only present in revision 1:

| Type | Name |
| --- | --- |
| [Map]&lt;[String], [Variant]&gt; | m_mapParam |

## Notification Types
Notification types 3001 - 3008 are only sent to the owner of the gathering. The others are sent to all participants.

| Type | Description |
| --- | --- |
| 3001 | New participant |
| 3002 | Participation cancelled |
| 3007 | Participant disconnected |
| 3008 | Participation ended |
| 4000 | Ownership change |
| 109000 | Gathering unregistered |

Notification type 3001:

| Field | Description |
| --- | --- |
| m_pidSource | Principal id |
| m_uiParam1 | Gathering id |
| m_uiParam2 | Principal id |
| m_strParam | Message |
| m_uiParam3 | Number of participants |

Notification type 3002, 3007 and 3008:

| Field | Description |
| --- | --- |
| m_pidSource | Principal id |
| m_uiParam1 | Gathering id |
| m_uiParam2 | Principal id |
| m_strParam | Message |

Notification type 4000:

| Field | Description |
| --- | --- |
| m_pidSource | Previous owner |
| m_uiParam1 | Gathering id |
| m_uiParam2 | New owner |
| m_strParam | Unknown |


Notification type 109000:

| Field | Description |
| --- | --- |
| m_pidSource | Principal id |
| m_uiParam1 | Gathering id |

[PID]: NEX-Common-Types#pid
[String]: NEX-Common-Types#string
[Structure]: NEX-Common-Types#structure
[Map]: NEX-Common-Types#map
[Variant]: NEX-Common-Types#variant
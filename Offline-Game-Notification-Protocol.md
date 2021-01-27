## [[NEX Protocols]] > Offline Game Notifications (71)

| Method ID | Method Name |
| --- | --- |
| 1 | [PollNotifications](#1-pollnotifications) |
| 2 | [PollSpecificOfflineNotifications](#2-pollspecificofflinenotifications) |
| 3 | [PollAnyOfflineNotifications](#3-pollanyofflinenotifications) |

# (1) PollNotifications
## Request
This method does not take any parameters.

## Response
| Type | Name |
| --- | --- |
| [List]&lt;[NotificationEvent](Notification-Protocol#notificationevent-structure)&gt; | listNotifications |
| Uint32 | nbRemainingNotifs |

# (2) PollSpecificOfflineNotifications
## Request
| Type | Name |
| --- | --- |
| [List]&lt;Uint32&gt; | majortype |

## Response
| Type | Name |
| --- | --- |
| [List]&lt;[TimedNotification]&gt; | listTimedNotification |
| Uint32 | ret |

# (3) PollAnyOfflineNotifications
## Request
This method does not take any parameters.

## Response
| Type | Name |
| --- | --- |
| [List]&lt;[TimedNotification]&gt; | listTimedNotification |
| Uint32 | nbRemainingNotifs |

# Types
## TimedNotification ([Structure])
| Type | Name |
| --- | --- |
| [DateTime] | timestamp |
| [NotificationEvent](Notification-Protocol#notificationevent-structure) | Notification |

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

[TimedNotification]: #timednotification-structure
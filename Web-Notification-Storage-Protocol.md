## [[NEX Protocols]] > Web Notifications Storage

| Method ID | Method Name |
| --- | --- |
| 1 | [RegisterUser](#1-registeruser) |
| 2 | [PollNotifications](#2-pollnotifications) |
| 3 | [UnregisterUser](#3-unregisteruser) |

# (1) RegisterUser
## Request
This method does not take any parameters.

## Response
This method does not return anything.

# (2) PollNotifications
## Request
This method does not take any parameters.

## Response
| Type | Name |
| --- | --- |
| [String] | listNotifications |
| Sint32 | nbNotifications |

# (3) UnregisterUser
## Request
This method does not take any parameters.

## Response
This method does not return anything.

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
## [[NEX Protocols]] > [Matchmake Referee](Matchmake-Referee-Protocol) > Eagle (120)

Games that use [libeagle](Eagle-Protocol) use a customized matchmake referee protocol. This page describes the differences to the original matchmake referee protocol.


## MatchmakeRefereeStartRoundParam ([Structure])
| Type | Name |
| --- | --- |
| Uint32 | personalDataCategory |
| Uint32 | gid |
| [List]&lt;[PID]&gt; | pids |
| Uint8 | reportSummaryMode |
| Uint32 | eventId |

## MatchmakeRefereePersonalRoundResult ([Structure])
| Type | Name |
| --- | --- |
| [PID] | pid |
| Uint32 | personalRoundResultFlag |
| Uint32 | roundWinLoss |
| Sint32 | ratingValueChange |
| [qBuffer] | buffer |
| Uint8 | reportSummaryMode |
| Uint32 | eventId |

[Result]: NEX-Common-Types#result
[String]: NEX-Common-Types#string
[Buffer]: NEX-Common-Types#buffer
[qBuffer]: NEX-Common-Types#qbuffer
[List]: NEX-Common-Types#list
[Map]: NEX-Common-Types#map
[PID]: NEX-Common-Types#pid
[DateTime]: NEX-Common-Types#datetime
[Structure]: NEX-Common-Types#structure
[Data]: NEX-Common-Types#anydataholder
[StationURL]: NEX-Common-Types#stationurl
[Variant]: NEX-Common-Types#variant
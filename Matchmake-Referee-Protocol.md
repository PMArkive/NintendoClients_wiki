## [[NEX Protocols]] > Matchmake Referee (120)

Games that use [libeagle](Eagle-Protocol) use a [customized matchmake referee protocol](Matchmake-Referee-Protocol-(Eagle)).

The remainder of this page describe the standard matchmake referee protocol.

| Method ID | Method Name |
| --- | --- |
| 1 | [StartRound](#1-startround) |
| 2 | [GetStartRoundParam](#2-getstartroundparam) |
| 3 | [EndRound](#3-endround) |
| 4 | [EndRoundWithoutReport](#4-endroundwithoutreport) |
| 5 | [GetRoundParticipants](#5-getroundparticipants) |
| 6 | [GetNotSummarizedRound](#6-getnotsummarizedround) |
| 7 | [GetRound](#7-getround) |
| 8 | [GetStatsPrimary](#8-getstatsprimary) |
| 9 | [GetStatsPrimaries](#9-getstatsprimaries) |
| 10 | [GetStatsAll](#10-getstatsall) |
| 11 | [CreateStats](#11-createstats) |
| 12 | [GetOrCreateStats](#12-getorcreatestats) |
| 13 | [ResetStats](#13-resetstats) |

# (1) StartRound
Raises `Core::InvalidArgument` if the list of pids is empty.

## Request
| Type | Name |
| --- | --- |
| [MatchmakeRefereeStartRoundParam] | param |

## Response
| Type | Name |
| --- | --- |
| Uint64 | roundId |

# (2) GetStartRoundParam
## Request
| Type | Name |
| --- | --- |
| Uint64 | roundId |

## Response
| Type | Name |
| --- | --- |
| [MatchmakeRefereeStartRoundParam] | param |

# (3) EndRound
## Request
| Type | Name |
| --- | --- |
| [MatchmakeRefereeEndRoundParam] | endRoundParam |

## Response
This method does not return anything.

# (4) EndRoundWithoutReport
## Request
| Type | Name |
| --- | --- |
| Uint64 | roundId |

## Response
This method does not return anything.

# (5) GetRoundParticipants
## Request
| Type | Name |
| --- | --- |
| Uint64 | roundId |

## Response
| Type | Name |
| --- | --- |
| [List]&lt;Uint64&gt; | pids |

# (6) GetNotSummarizedRound
## Request
This method does not take any parameters.

## Response
| Type | Name |
| --- | --- |
| [List]&lt;[MatchmakeRefereeRound]&gt; | rounds |

# (7) GetRound
## Request
| Type | Name |
| --- | --- |
| Uint64 | roundId |

## Response
| Type | Name |
| --- | --- |
| [MatchmakeRefereeRound] | round |

# (8) GetStatsPrimary
## Request
| Type | Name |
| --- | --- |
| [MatchmakeRefereeStatsTarget] | target |

## Response
| Type | Name |
| --- | --- |
| [MatchmakeRefereeStats] | stats |

# (9) GetStatsPrimaries
## Request
| Type | Name |
| --- | --- |
| [List]&lt;[MatchmakeRefereeStatsTarget]&gt; | targets |

## Response
| Type | Name |
| --- | --- |
| [List]&lt;[MatchmakeRefereeStats]&gt; | stats |
| [List]&lt;[Result]&gt; | results |

# (10) GetStatsAll
## Request
| Type | Name |
| --- | --- |
| [MatchmakeRefereeStatsTarget] | target |

## Response
| Type | Name |
| --- | --- |
| [List]&lt;[MatchmakeRefereeStats]&gt; | stats |

# (11) CreateStats
## Request
| Type | Name |
| --- | --- |
| [MatchmakeRefereeStatsInitParam] | param |

## Response
This method does not return anything.

# (12) GetOrCreateStats
## Request
| Type | Name |
| --- | --- |
| [MatchmakeRefereeStatsInitParam] | param |

## Response
| Type | Name |
| --- | --- |
| [MatchmakeRefereeStats] | stats |

# (13) ResetStats
## Request
This method does not take any parameters.

## Response
This method does not return anything.

# Types
## MatchmakeRefereeEndRoundParam ([Structure])
| Type | Name |
| --- | --- |
| Uint64 | roundId |
| [List]&lt;[MatchmakeRefereePersonalRoundResult]&gt; | personalRoundResults |

## MatchmakeRefereeRound ([Structure])
| Type | Name |
| --- | --- |
| Uint64 | roundId |
| Uint32 | gid |
| Uint32 | state |
| Uint32 | personalDataCategory |
| [List]&lt;[MatchmakeRefereePersonalRoundResult]&gt; | normalizedPersonalRoundResults |

## MatchmakeRefereeStats ([Structure])
| Type | Name |
| --- | --- |
| Uint64 | uniqueId |
| Uint32 | category |
| [PID] | pid |
| Uint32 | recentDisconnection |
| Uint32 | recentViolation |
| Uint32 | recentMismatch |
| Uint32 | recentWin |
| Uint32 | recentLoss |
| Uint32 | recentDraw |
| Uint32 | totalDisconnect |
| Uint32 | totalViolation |
| Uint32 | totalMismatch |
| Uint32 | totalWin |
| Uint32 | totalLoss |
| Uint32 | totalDraw |
| Uint32 | ratingValue |

## MatchmakeRefereeStartRoundParam ([Structure])
| Type | Name |
| --- | --- |
| Uint32 | personalDataCategory |
| Uint32 | gid |
| [List]&lt;[PID]&gt; | pids |

## MatchmakeRefereeStatsTarget ([Structure])
| Type | Name |
| --- | --- |
| [PID] | pid |
| Uint32 | category |

## MatchmakeRefereeStatsInitParam ([Structure])
| Type | Name |
| --- | --- |
| Uint32 | category |
| Uint32 | initialRatingValue |

## MatchmakeRefereePersonalRoundResult ([Structure])
| Type | Name |
| --- | --- |
| [PID] | pid |
| Uint32 | personalRoundResultFlag |
| Uint32 | roundWinLoss |
| Sint32 | ratingValueChange |
| [qBuffer] | buffer |

[Result]: NEX-Common-Types#result
[String]: NEX-Common-Types#string
[PID]: NEX-Common-Types#pid
[Buffer]: NEX-Common-Types#buffer
[qBuffer]: NEX-Common-Types#qbuffer
[List]: NEX-Common-Types#list
[Map]: NEX-Common-Types#map
[DateTime]: NEX-Common-Types#datetime
[Structure]: NEX-Common-Types#structure
[Data]: NEX-Common-Types#anydataholder
[StationURL]: NEX-Common-Types#stationurl
[Variant]: NEX-Common-Types#variant

[MatchmakeRefereeStartRoundParam]: #matchmakerefereestartroundparam-structure
[MatchmakeRefereeEndRoundParam]: #matchmakerefereeendroundparam-structure
[MatchmakeRefereeRound]: #matchmakerefereeround-structure
[MatchmakeRefereeStatsTarget]: #matchmakerefereestatstarget-structure
[MatchmakeRefereeStats]: #matchmakerefereestats-structure
[MatchmakeRefereeStatsInitParam]: #matchmakerefereestatsinitparam-structure
[MatchmakeRefereePersonalRoundResult]: #matchmakerefereepersonalroundresult-structure
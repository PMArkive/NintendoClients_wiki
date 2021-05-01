## [[NEX Protocols]] > [Ranking 2](Ranking-2-Protocol) > Eagle (122)

This page describes the methods that are only seen in Super Mario Bros. 35 and PAC-MAN 99.

| Method ID | Method Name |
| --- | --- |
| 11 | [GetEstimateMyScoreRank](#11-getestimatemyscorerank) |

# (11) GetEstimateMyScoreRank
## Request
| Type | Name |
| --- | --- |
| [Ranking2EstimateMyScoreRankInput] | input |

## Response
| Type | Name |
| --- | --- |
| [Ranking2EstimateScoreRankOutput] | output |

# Types
## Ranking2EstimateMyScoreRankInput ([Structure])
| Type | Name |
| --- | --- |
| Uint32 | category |
| Uint8 | numSeasonsToGoBack |

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

[Ranking2EstimateMyScoreRankInput]: #ranking2estimatemyscorerankinput-structure
[Ranking2EstimateScoreRankOutput]: Ranking-Protocol-2#ranking2estimatescorerankoutput-structure
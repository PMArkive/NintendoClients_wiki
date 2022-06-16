NPLN provides modern game services through [gRPC](https://grpc.io/). The decompiled protobuf files can be found [here](https://github.com/kinnay/NPLN-Protocols).

The NPLN server is at `https://<tenant id>.lp1.t.npln.srv.nintendo.net`. The tenant id is always `t-<server id>-lp1`.

* [Metadata](#metadata)
* [List of services](#list-of-services)
* [List of games](#list-of-games)
* [Useful tools](#useful-tools)

## Metadata
The following metadata fields may be included in requests:

| Field | Description |
| --- | --- |
| `authorization` | `bearer <access token>` |
| `npln-tenant-id` | Tenant id (like `t-e1c218b5-lp1`) |
| `uid` | User id (like `u-15p9o26ew2zitiv073ii`) |

The `npln-tenant-id` field is always required. The `authorization` and `uid` fields are only required if the request requires authorization.

If the metadata is invalid, the server returns status code 12 (Unimplemented) on production servers, or 14 (Unavailable) on development servers.

The official library sets the user agent to `grpc-c++/1.31.1 grpc-c/11.0.0 (nintendo; chttp2)`.

## List of services
Services are never modified in a backward incompatible way, but new methods and services may be added in the future.

* `nn.npln.auth.v1.Auth`
* `nn.npln.friends.v1.Friends`
* `nn.npln.friends.v1.PresenceService`
* `nn.npln.gamesync.v1.Gamesync`
* `nn.npln.hydro.v1.Datastore`
* `nn.npln.leaderboard.v1.LeaderboardService`
* `nn.npln.maintenance.v1.MaintenanceScheduleService`
* `nn.npln.matchmaking.v1.GameSessionService`
* `nn.npln.matchmaking.v1.Matchmaker`
* `nn.npln.messaging.v1.Messaging`

## List of games
* [SDK version table](https://kinnay.github.io/view.html?page=switch&sort=npln&npln=1)

| Game | Tenant ID |
| --- | ---
| Monster Hunter Rise | `e1c218b5` |
| Monster Hunter Rise Demo | `f124d2cb` |
| Monster Hunter Rise: Sunbreak Demo | `bc33b7d4` |
| Pokemon Legends: Arceus | `e047112f` |

## Useful Tools
* [grpcui](https://github.com/fullstorydev/grpcui) - a simple user interface for gRPC
* [grpc-dump](https://github.com/bradleyjkemp/grpc-tools) - a proxy that dumps gRPC messages (for mitm)
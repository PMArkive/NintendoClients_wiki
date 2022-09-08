NPLN identifies resources by name. A resource name is a path-like string that uniquely identifies a resource, even across tenants. This page lists currently known resource names.

The server always sends the full resource name, but the client may use `current` to refer to the currently active resource (e.g. `tenants/current`).

| Resource Type | Name |
| --- | --- |
| `nn.npln.auth.v1.Account` | `accounts/<id>` |
| | `tenants/<id>`
| | `tenants/<id>/categories/<id>`
| | `tenants/<id>/categories/<id>/seasons/<id>`
| | `tenants/<id>/content/<id>`
| | `tenants/<id>/documents/<path>`
| `nn.npln.toyohr.v1.FestResult` | `tenants/<id>/festResults/<id>`
| `nn.npln.toyohr.v1.FestSchedule` | `tenants/<id>/festSchedules/<id>`
| `nn.npln.toyohr.v1.Fest` | `tenants/<id>/fests/<id>` |
| `nn.npln.toyohr.v1.FestDecryptionKey` | `tenants/<id>/fests/<id>/decryptionKey`
| `nn.npln.matchmaking.v1.GameSessionCreationTicket` | `tenants/<id>/gameSessionCreationTickets/<id>`
| | `tenants/<id>/gameSessionSearchConfigs/<id>`
| `nn.npln.matchmaking.v1.GameSession` | `tenants/<id>/gameSessions/<id>`
| `nn.npln.matchmaking.v1.UserSession` | `tenants/<id>/gameSessions/<id>/userSessions/<id>`
| `nn.npln.matchmaking.v1.IceServerSet` | `tenants/<id>/iceServerSets/<name>`
| `nn.npln.matchmaking.v1.LatencyMeasurementServer` | `tenants/<id>/latencyMeasurementServers/<name>`
| | `tenants/<id>/matchmakingConfigs/<name>`
| `nn.npln.matchmaking.v1.MatchmakingTicket` | `tenants/<id>/matchmakingTickets/<id>`
| | `tenants/<id>/saveEventTypes/<name>`
| `nn.npln.toyohr.v1.SaveRecord` | `tenants/<id>/saveRecords/<id>`
| `nn.npln.toyohr.v1.SeasonSchedule` | `tenants/<id>/seasonSchedules/<id>`
| | `tenants/<id>/targets/<name>`
| `nn.npln.toyohr.v1.CoopSchedule` | `tenants/<id>/targets/<name>/coopSchedules/<id>`
| `nn.npln.toyohr.v1.VsParams` | `tenants/<id>/targets/<name>/vsParams/<id>`
| `nn.npln.toyohr.v1.VsSchedule` | `tenants/<id>/targets/<name>/vsSchedules/<id>`
| `nn.npln.auth.v1.UserExternalId` | `tenants/<id>/userExternalIds/<id>` |
| `nn.npln.auth.v1.User` | `tenants/<id>/users/<id>`
| `nn.npln.friends.v1.FriendUser` | `tenants/<id>/users/<id>/friendUsers/<id>`
| `nn.npln.friends.v1.Presence` | `tenants/<id>/users/<id>/presence`
| | `tenants/<id>/users/<id>/violations/<type>`

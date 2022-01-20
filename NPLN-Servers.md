The NPLN servers provide game services through [gRPC](https://grpc.io/).

* [Decompiled protobuf files](https://github.com/kinnay/NPLN-Protocols)
* [SDK version table](https://kinnay.github.io/view.html?page=switch&sort=npln&npln=1)

The NPLN server is at `https://<tenant id>.lp1.t.npln.srv.nintendo.net`. The tenant id is always `t-<server id>-lp1`. The following server ids are known:

| Game | Server ID |
| --- | --- |
| Pokemon Legends Arceus | `e047112f` |
| Monster Hunter Rise | `e1c218b5` |
| Monster Hunter Rise Demo | `f124d2cb` |

In the metadata, `npln-tenant-id` must be set to the tenant id (for example `t-e1c218b5-lp1`). If the tenant id is invalid, the server returns status code 12 (Unimplemented).

The official library sets the user agent to `grpc-c++/1.31.1 grpc-c/11.0.0 (nintendo; chttp2)`.
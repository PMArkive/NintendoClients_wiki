## Switch
Replace '%' by one of the following:

| Environment | Description |
| --- | --- |
| lp1 | Live production |
| dd1, jd1, sd1, sp1, dp1, td1, xd1 | Development |

| Server | Description |
| --- | --- |
| - ctest.cdn.nintendo.net<br>- ctest-ul-%.cdn.nintendo.net<br>- ctest-dl-%.cdn.nintendo.net | [Connection test](Connection-Test) |
| - dauth-%.ndas.srv.nintendo.net | [Device authentication](DAuth-Server) |
| - aauth-%.ndas.srv.nintendo.net | [Application authentication](AAuth-Server) |
| - dcert-%.ndas.srv.nintendo.net<br>- acert-%.ndas.srv.nintendo.net | [JWK servers](Switch-Tokens) |
| - e0d67c509fb203858ebcb2fe3f88c2aa.baas.nintendo.com<br>- e97b8a9d672e4ce4845ec6947cd66ef6-sb.baas.nintendo.com<br>- cdn-image-e0d67c509fb203858ebcb2fe3f88c2aa.baas.nintendo.com<br>- cdn-image-e97b8a9d672e4ce4845ec6947cd66ef6-sb.baas.nintendo.com | [Switch accounts](BAAS-Server) |
| - accounts.nintendo.com<br>- cdn.accounts.nintendo.com<br>- api.accounts.nintendo.com<br>- e97b8a9d672e4ce4845ec6947cd66ef6-sb.accounts.nintendo.com<br>- e97b8a9d672e4ce4845ec6947cd66ef6-sb-api.accounts.nintendo.com | [Nintendo accounts](Account-Server-(Switch)) |
| - t-&lt;game id&gt;-%.%.t.npln.srv.nintendo.net | [Game servers (NPLN)](NPLN-Servers) |
| - g&lt;game server id&gt;-%.s.n.srv.nintendo.net | [Game servers (NEX)](NEX-Overview-(Game-Servers)) |
| - g&lt;game server id&gt;-%.r.n.srv.nintendo.net | P2P relay |
| - g&lt;game server id&gt;-%.p.srv.nintendo.net | [P2P monitoring](Monitoring-Data-Protocol) |
| - nncs1-%.n.n.srv.nintendo.net<br>- nncs2-%.n.n.srv.nintendo.net | [NAT check server](NAT-Check-Server) |
| - api-%.znc.srv.nintendo.net<br>- web-%.znc.srv.ninendo.net | [Smartphone services](ZNC-Server) |
| - api.hac.%.acbaa.srv.nintendo.net | <a href="https://github.com/Kinnay/NintendoClients/wiki/AC:NH-Server">Animal Crossing API</a> |
| - d7d-&lt;server name&gt;.g.%.e.srv.nintendo.net | [Eagle (relay servers)](Eagle-Protocol) |
| - fw-api.%.nso.nintendo.net | NSO rewards |
| - storage.%.scsi.srv.nintendo.net<br>- migration.%.scsi.srv.nintendo.net<br>- storage.%.sata.srv.nintendo.net<br>- permission.%.sata.srv.nintendo.net<br>- pp.%.sata.srv.nintendo.net<br>- scsi-policy-%.cdn.nintendo.net | [Online save storage](OLSC-Servers) |
| - ecs-%.hac.shop.nintendo.net<br>- ias-%.hac.shop.nintendo.net | [eShop services](REST-Services) |
| - bugyo.hac.%.eshop.nintendo.ent<br>- tagaya.hac.%.eshop.nintendo.net | [eShop applet](eShop-Applet-(Switch)) |
| - api-%.frs.srv.nintendo.net | [Friends](Friends-API) |
| - consumer.%.npns.srv.nintendo.net<br>- broker.%.npns.srv.nintendo.net<br>- provider-%.npns.srv.nintendo.net<br>- app-a03.%.npns.srv.nintendo.net<br>- app-b01.%.npns.srv.nintendo.net | [Push notifications](NPNS-Servers) |
| - aqua.hac.%.d4c.nintendo.net<br>- atum.hac.%.d4c.nintendo.net<br>- atumn.hac.%.d4c.nintendo.net<br>- beach.hac.%.eshop.nintendo.net<br>- pearljam.hac.%.eshop.nintendo.net<br>- pushmo.hac.%.eshop.nintendo.net<br> - sun.hac.%.d4c.nintendo.net<br>- superfly.hac.%.d4c.nintendo.net | [Title installation](NIM-Servers) |
| - dragons.hac.%.dragons.nintendo.net<br>- dragonst.hac.%.dragons.nintendo.net<br>- tigers.hac.%.dragons.nintendo.net | [eLicenses](Dragons-Servers) |
| - receive-%.dg.srv.nintendo.net<br>- receive-%.er.srv.nintendo.net | [Telemetry](Telemetry-Servers) |
| - bcat-topics-%.cdn.nintendo.net<br>- bcat-list-%.cdn.nintendo.net<br>- bcat-data-%.cdn.nintendo.net | [News](BCAT-Servers) |
| - Service-status-%.cdn.nintendo.net | [Game server availability](Service-Status-Server) |
| - api-%.pctl.srv.nintendo.net<br>- parentalcontrols-movie-%.cdn.nintendo.net | [Parental controls](Parental-Controls) |
| - web-%.share.srv.nintendo.net | |
| - bvc-hac-%.cdn.nintendo.net<br>- bvc-hac-%.cdn.n.nintendoswitch.cn | |
| - api.sect.srv.nintendo.net | |
| - capi.%.op2.nintendo.net | [NSO membership verification](NSO-Verification-Server) |
| - c-%.accounts.nintendo.com | |
| - app.%.five.nintendo.net | [Invitations](Invitation-Server) |
| - idbe-hac.cdn.nintendo.net | [Icon data](IDBE-Server) |
| - %.nso.nintendo.net | NSO applet |
| - mii-secure-%.cdn.nintendo.net | Mii images |
| - sprofile-%.cdn.nintendo.net | |
| - veer.hac.lp1.d4c.nintendo.net | |

## Wii U
| Server | Description |
| --- | --- |
| - account.nintendo.net<br>- game-dev.account.nintendo.net<br>- system-dev.account.nintendo.net<br>- library-dev.account.nintendo.net<br>- staging.account.nintendo.net | [[Account server]] |
| - mii-secure.account.nintendo.net<br>- mii-secure.cdn.nintendo.net<br>- mii-images.cdn.nintendo.net<br>- game-dev-mii-images.cdn.nintendo.net<br>- system-dev-mii-images.cdn.nintendo.net<br>- library-dev-mii-images.cdn.nintendo.net<br>- staging-mii-images.cdn.nintendo.net | Mii images |
| - nncs1.app.nintendowifi.net<br>- nncs2.app.nintendowifi.net | [NAT check server](NAT-Check-Server) |
| - hpp-&lt;game server id&gt;-&lt;environment&gt;.n.app.nintendo.net | [Hpp server](Hpp-Server) |
| - discovery.olv.nintendo.net | Miiverse |
| - tagaya.wup.shop.nintendo.net | [Title version list](Tagaya-Server) |
| - ninja.wup.shop.nintendo.net | [eShop api](Ninja-Server)
| - geisha-wup.cdn.nintendo.net | eShop website |
| - cas.wup.shop.nintendo.net<br>- ecs.wup.shop.nintendo.net<br>- ias.wup.shop.nintendo.net<br>- nus.wup.shop.nintendo.net | [eShop services](SOAP-Services) |
| - ccs.wup.shop.nintendo.net<br>- pls.wup.shop.nintendo.net<br>- pushmo.wup.shop.nintendo.net<br>- pushmore.wup.shop.nintendo.net<br>- samurai.wup.shop.nintendo.net<br>- samurai-wup.cdn.nintendo.net<br>- kanzashi-wup.cdn.nintendo.net<br>- kanzashi-movie-wup.cdn.nintendo.net<br>- samuraicdndev1-wup.cdn.nintendo.net<br>- geishacdndev1-wup.cdn.nintendo.net<br>- gw.sgks.shop.nintendo.net | eShop |
| - npvk.app.nintendo.net<br>- npvk-dev.app.nintendo.net<br>- npts.app.nintendo.net<br>- nppl.app.nintendo.net | BOSS |
| - idbe-wup.cdn.nintendo.net<br>- idbe-ctr.cdn.nintendo.net | [Icon data](IDBE-Server) |
| - m1.nintendo.net | [VC Manuals](VC-Manual-Server) |
| - nintendojp.d1.sc.omtrdc.net<br>- wiiu-ssl-static.ubi.com | |

## 3DS
| Server | Description |
| --- | --- |
| - conntest.nintendowifi.net | Connection test |
| - nasc.nintendowifi.net<br>- nasc.dev.nintendowifi.net<br>- nasc.test.nintendowifi.net | Account server |
| - hpp-&lt;game server id&gt;-&lt;environment&gt;.n.app.nintendo.net | [Hpp server](Hpp-Server) |
| - ccs.c.shop.nintendowifi.net<br>- nus.c.shop.nintendowifi.net<br>- pls.c.shop.nintendowifi.net | eShop |
| - l-npns.app.nintendowifi.net<br>- npns-dev.c.app.nintendowifi.net<br>- nppl.c.app.nintendowifi.net<br>- npul.c.app.nintendowifi.net<br>- npvk.app.nintendowifi.net | SpotPass |
| - ctr-o2fgs.cdn.nintendo.net |

## Other
| Server | Description |
| --- | --- |
| - nexred.nintendo.co.jp | Redmine issue tracker for [NEX](NEX-Overview-(Game-Servers)) |
| - devbts30.nintendo.co.jp<br>- devhipchat.boy.nintendo.co.jp | Internal dev servers |
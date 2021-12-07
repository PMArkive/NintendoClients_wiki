Based on system version 13.2.0.

| Name | Sysmodule | Interface |
| --- | --- | --- |
| `acc:aa` | `account` | nn::account::IBaasAccessTokenAccessor |
| `acc:e` | `account` | |
| `acc:e:u1` | `account` | |
| `acc:e:u2` | `account` | |
| `acc:u0` | `ns` | nn::account::IAccountServiceForAppliation |
| `acc:u1` | `ns` | nn::account::IAccountServiceForSystemService |
| `acc:su` | `ns` | nn::account::IAccountServiceForAdministrator |
| `dauth:0` | `account` | |
| `aoc:u` | `ns` | nn::aocsrv::detail::IAddOnContentManager |
| `apm` | `am` | nn::apm::IManager |
| `apm:am` | `ptm` | |
| `apm:sys` | `ptm` | nn::apm::ISystemManager |
| `appletAE` | `am` | nn::am::service::IAllSystemAppletProxiesService |
| `appletOE` | `am` | nn::am::service::IApplicationProxyService |
| `arp:r` | `glue` | |
| `arp:w` | `glue` | |
| `aud:a` | `audio` | nn::audio::detail::IAudioSystemManagerForApplet |
| `aud:d` | `audio` | nn::audio::detail::IAudioSystemManagerForDebugger |
| `audctl` | `audio` | |
| `auddebug` | | nn::audio::detail::IAudioSystemManagerForSystemDebug |
| `auddev` | `audio` | nn::audio::detail::IAudioSnoopManager |
| `audin:u` | `audio` | nn::audio::detail::IAudioInManager |
| `audout:u` | `audio` | nn::audio::detail::IAudioOutManager |
| `audrec:u` | `audio` | nn::audio::detail::IFinalOutputRecorderManager |
| `audren:u` | `audio` | nn::audio::detail::IAudioRendererManager |
| `avm` | `sdb` | |
| `banana` | | |
| `bcat:a` | `bcat` | nn::bcat::ipc::IServiceCreator |
| `bcat:m` | `bcat` | nn::bcat::ipc::IServiceCreator |
| `bcat:s` | `bcat` | nn::bcat::ipc::IServiceCreator |
| `bcat:u` | `bcat` | nn::bcat::ipc::IServiceCreator |
| `bgtc:sc` | `glue` | |
| `bgtc:t` | `glue` | |
| `bpc` | `pcv` | |
| `bsd:s` | `bsdsocket` | nn::socket::sf::IClient |
| `bsd:u` | `bsdsocket` | nn::socket::sf::IClient |
| `bsdcfg` | `bsdsocket` | |
| `bt` | `bluetooth` | nn::bluetooth::IBluetoothUser |
| `btdrv` | `bluetooth` | nn::bluetooth::IBluetoothDriver |
| `btm` | `btm` | |
| `btm:dbg` | `btm` | |
| `btm:sys` | `btm` | |
| `btm:u` | `btm` | nn::btm::IBtmUser |
| `capmtp` | `capmtp` | |
| `caps:a` | `capsrv` | |
| `caps:c` | `capsrv` | |
| `caps:dc` | `jpegdec` | |
| `caps:sc` | `vi` | |
| `caps:ss` | `vi` | |
| `caps:su` | `am` | nn::capsrv::sf::IScreenShotApplicationService |
| `caps:u` | `capsrv` | nn::capsrv::sf::IAlbumApplicationService |
| `cec-mgr` | `vi` | |
| `clkrst` | `pcv` | |
| `clkrst:a` | `pcv` | |
| `clkrst:i` | `pcv` | |
| `csrng` | `spl` | nn::spl::detail::IRandomInterface |
| `dispdrv` | `nvnflinger` | |
| `ectx:aw` | `glue` | nn::err::context::IWriterForApplication |
| `ectx:r` | `glue` | |
| `ectx:w` | `glue` | |
| `erpt:c` | `erpt` | |
| `erpt:r` | `erpt` | |
| `es` | `es` | |
| `ethc:c` | `bsdsocket` | |
| `ethc:i` | `bsdsocket` | |
| `eupld:c` | `eupld` | |
| `eupld:r` | `eupld` | |
| `fan` | `ptm` | |
| `fatal:p` | `fatal` | |
| `fatal:u` | `fatal` | |
| `fgm:9` | `ptm` | |
| `friend:a` | `friends` | nn::friends::detail::ipc::IServiceCreator |
| `friend:m` | `friends` | nn::friends::detail::ipc::IServiceCreator |
| `friend:s` | `friends` | nn::friends::detail::ipc::IServiceCreator |
| `friend:u` | `friends` | nn::friends::detail::ipc::IServiceCreator |
| `friend:v` | `friends` | nn::friends::detail::ipc::IServiceCreator |
| `fsp-ldr` | `FS` | nn::fssrv::sf::IFileSystemProxyForLoader |
| `fsp-pr` | `FS` | nn::fssrv::sf::IProgramRegistry |
| `fsp-srv` | `FS` | nn::fssrv::sf::IFileSystemProxy |
| `gpio` | `Bus` | |
| `grc:c` | `grc` | |
| `grc:d` | `grc` | |
| `hid` | `hid` | nn::hid::IHidServer |
| `hid:dbg` | `hid` | nn::hid::IHidDebugServer |
| `hid:sys` | `hid` | nn::hid::IHidSystemServer |
| `hid:tmp` | `hid` | |
| `hidbus` | `hid` | nn::hidbus::server::HidbusServer |
| `hshl:set` | `psc` | |
| `hshl:sys` | `psc` | |
| `htc` | | nn::tma::IHtcManager |
| `htc:tenv` | | nn::htc::tenv::IServiceManager |
| `htcs` | | nn::tma::IHtcsManager |
| `hwopus` | `audio` | nn::codec::detail::IHardwareOpusDecoderManager |
| `i2c` | `Bus` | |
| `i2c:pcv` | `Bus` | |
| `idle:sys` | `am` | |
| `ins:r` | `psc` | |
| `ins:s` | `psc` | |
| `irs` | `hid` | nn::irsensor::IIrSensorServer |
| `irs:sys` | `hid` | nn::irsensor::IIrSensorSystemServer |
| `jit:u` | `jit` | nn::jitsrv::IJitService |
| `lbl` | `vi` | |
| `ldn:m` | `ldn` | nn::ldn::detail::IMonitorServiceCreator |
| `ldn:s` | `ldn` | nn::ldn::detail::ISystemServiceCreator |
| `ldn:u` | `ldn` | nn::ldn::detail::IUserServiceCreator |
| `ldr:ro` | `ro` | nn::ro::detail::IRoInterface |
| `ldr:shel` | `Loader` | |
| `led` | `Bus` | |
| `lm` | `LogManager.Prod` | nn::lm::ILogService |
| `lm:get` | | nn::lm::ILogGetter |
| `lp2p:app` | `ldn` | |
| `lp2p:m` | `ldn` | |
| `lp2p:sys` | `ldn` | |
| `lr` | `NCM` | |
| `mig:usr` | `migration` | |
| `mii:e` | `sdb` | nn::mii::detail::IStaticService |
| `mii:u` | `sdb` | nn::mii::detail::IStaticService |
| `miiimg` | `sdb` | nn::mii::detail::IImageDatabaseService |
| `mm:u` | `vi` | |
| `mnpp:app` | `bcat` | |
| `mnpp:sys` | `bcat` | |
| `mnpp:web` | `bcat` | |
| `ncm` | `NCM` | |
| `nd:sys` | | |
| `ndrm:la` | `es` | |
| `ndrm:lu` | `es` | |
| `news:a` | `bcat` | |
| `news:c` | `bcat` | |
| `news:m` | `bcat` | |
| `news:p` | `bcat` | |
| `news:v` | `bcat` | |
| `nfc:am` | `nfc` | |
| `nfc:mf:u` | `nfc` | |
| `nfc:sys` | `nfc` | nn::nfc::detail::ISystemManager |
| `nfc:user` | `nfc` | nn::nfc::detail::IUserManager |
| `nfp:dbg` | `nfc` | nn::nfp::detail::IDebugManager |
| `nfp:sys` | `nfc` | nn::nfp::detail::ISystemManager |
| `nfp:user` | `nfc` | nn::nfp::detail::IUserManager |
| `ngct:s` | `ngct` | nn::ngc::t::detail::IServiceWithManagementApi |
| `ngct:u` | `ngct` | nn::ngc::t::detail::IService |
| `nifm:a` | `nifm` | nn::nifm::detail::IStaticService |
| `nifm:s` | `nifm` | nn::nifm::detail::IStaticService |
| `nifm:u` | `nifm` | nn::nifm::detail::IStaticService |
| `nim` | | |
| `nim:eca` | `nim` | nn::nim::detail::IShopServiceAccessServerInterface |
| `nim:ecas` | `nim` | nn::nim::detail::IShopServiceAccessSytemInterface |
| `nim:shp` | `nim` | |
| `notif:a` | `glue` | nn::notification::server::INotificationServicesForApplication |
| `notif:s` | `glue` | |
| `npns:s` | `npns` | nn::npns::INpnsSystem |
| `npns:u` | `npns` | nn::npns::INpnsUser |
| `ns:am2` | `ns` | |
| `ns:dev` | `ns` | |
| `ns:ec` | `ns` | |
| `ns:rid` | `ns` | |
| `ns:ro` | `ns` | |
| `ns:rt` | `ns` | |
| `ns:su` | `ns` | |
| `ns:vm` | `ns` | |
| `ns:web` | `ns` | |
| `nsd:a` | `bsdsocket` | nn::nsd::detail::IManager |
| `nsd:u` | `bsdsocket` | nn::nsd::detail::IManager |
| `ntc` | `nim` | nn::ntc::detail::service::IStaticService |
| `nvdbg:d` | `nvservices` | |
| `nvdrv` | `nvservices` | nns::nvdrv::INvDrvServices |
| `nvdrv:a` | `nvservices` | |
| `nvdrv:s` | `nvservices` | |
| `nvdrv:t` | `nvservices` | |
| `nvdrvdbg` | `nvservices` | |
| `nvgem:c` | `nvservices` | |
| `nvgem:cd` | `nvservices` | |
| `nvmemp` | | nv::MemoryProfiler::IMemoryProfiler |
| `olsc:s` | `olsc` | |
| `olsc:u` | `olsc` | nn::olsc::srv::IOlscServiceForApplication |
| `omm` | `am` | |
| `ovln:rcv` | `psc` | |
| `ovln:snd` | `psc` | |
| `pcie` | | |
| `pcie:log` | | |
| `pctl` | `pctl` | nn::pctl::detail::ipc::IParentalControlServiceFactory |
| `pctl:a` | `pctl` | nn::pctl::detail::ipc::IParentalControlServiceFactory |
| `pctl:r` | `pctl` | nn::pctl::detail::ipc::IParentalControlServiceFactory |
| `pctl:s` | `pctl` | nn::pctl::detail::ipc::IParentalControlServiceFactory |
| `pcv` | `pcv` | |
| `pdm:ntfy` | `sdb` | |
| `pdm:qry` | `sdb` | |
| `pgl` | `pgl` | |
| `pinmux` | `Bus` | |
| `pl:s` | `sdb` | nn::pl::detail::IPlatformServiceManagerForSystem |
| `pl:u` | `sdb` | nn::pl::detail::IPlatformServiceManager |
| `pm:bm` | `ProcessMana` | |
| `pm:info` | `ProcessMana` | |
| `pm:shell` | `ProcessMana` | |
| `prepo:m` | `bcat` | nn::prepo::detail::ipc::IPrepoService |
| `prepo:s` | `bcat` | nn::prepo::detail::ipc::IPrepoService |
| `prepo:u` | `bcat` | nn::prepo::detail::ipc::IPrepoService |
| `prepo:a2` | `bcat` | nn::prepo::detail::ipc::IPrepoService |
| `psc:c` | `psc` | |
| `psc:l` | `psc` | |
| `psc:m` | `psc` | |
| `psm` | `ptm` | |
| `pwm` | `Bus` | |
| `rgltr` | `pcv` | |
| `ro:1` | `ro` | |
| `ro:dmnt` | `ro` | |
| `rtc` | `pcv` | |
| `sasbus` | `Bus` | |
| `set` | `settings` | nn::settings::ISettingsServer |
| `set:cal` | `settings` | nn::settings::IFactorySettingsServer |
| `set:fd` | `settings` | nn::settings::IFirmwareDebugSettingsServer |
| `set:sys` | `settings` | nn::settings::ISystemSettingsServer |
| `sfdnsres` | `bsdsocket` | nn::socket::resolver::IResolver |
| `spbg:sp` | `olsc` | |
| `spl:` | `spl` | |
| `spl:es` | `spl` | |
| `spl:mig` | `spl` | |
| `sprof:bg` | `erpt` | |
| `sprof:sp` | `erpt` | |
| `spsm` | `am` | |
| `srepo:a` | `psc` | |
| `srepo:u` | `psc` | |
| `ssl` | `ssl` | nn::ssl::sf::ISslService |
| `tc` | `ptm` | |
| `ts` | `ptm` | |
| `time:a` | `glue` | nn::timesrv::detail::service::IStaticService |
| `time:al` | `psc` | |
| `time:m` | `psc` | |
| `time:p` | `psc` | |
| `time:r` | `glue` | nn::timesrv::detail::service::IStaticService |
| `time:s` | `psc` | nn::timesrv::detail::service::IStaticService |
| `time:su` | `psc` | nn::timesrv::detail::service::IStaticService |
| `time:u` | `glue` | nn::timesrv::detail::service::IStaticService |
| `tspm` | | |
| `uart` | `Bus` | |
| `usb:ds` | `usb` | |
| `usb:hs` | `usb` | |
| `usb:hs:a` | `usb` | |
| `usb:obsv` | `usb` | |
| `usb:pd` | `usb` | |
| `usb:pd:c` | `usb` | |
| `usb:pm` | `usb` | |
| `usb:qdb` | `usb` | |
| `vi:m` | `vi` | nn::visrv::sf::IManagerRootService |
| `vi:s` | `vi` | nn::visrv::sf::ISystemRootService |
| `vi:u` | `vi` | nn::visrv::sf::IApplicationRootService |
| `wlan:dtc` | `wlan` | |
| `wlan:inf` | `wlan` | |
| `wlan:lcl` | `wlan` | |
| `wlan:lg` | `wlan` | |
| `wlan:lga` | `wlan` | |
| `wlan:sg` | `wlan` | |
| `wlan:soc` | `wlan` | |
| `xcd:sys` | `hid` | |
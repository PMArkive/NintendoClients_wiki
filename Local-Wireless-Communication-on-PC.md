Because [LDN](LDN-Protocol) operates at the data link layer, it cannot be emulated with normal network sockets. Instead, one must put the network card into monitor mode and use a low-level networking library such as [libpcap](https://www.tcpdump.org/).

This page is intended to provide a simple guide to get started with local wireless communication.

This guide is written for Linux users and was tested on a system running Ubuntu. If you are using a different operating system, this guide is probably less useful for you.

1. [Entering monitor mode](#entering-monitor-mode)

### Entering monitor mode
By default, the network interface is in managed mode, which means that it only accepts packets that are intended for your PC:

![](https://www.dropbox.com/s/ef3rijbwos9hsos/iwconfig_managed.png?raw=1)

In monitor mode, the network interface receives all packets that are sent through the air.
This page describes the protocol that is used to communicate with nearby consoles in LDN mode, which is the default mode for local multiplayer.

Because LDN operates at the data link layer, it requires a good understanding of the [IEEE 802.11 specification](https://ieeexplore.ieee.org/document/9363693).

The host of the session broadcasts custom action frames. To find nearby consoles, the console scans for these action frames.
## Quick Start
### Sniffing Packets
A packet is a set of bytes sent to or from the server. Kingsisle sends these packets via TCP, and every packet containing Kingsisle's signature will hereby by refered to as a __magic packet__.

You can easily view these packets via [WireShark](https://www.wireshark.org/#download) (or any relevant tool) using a capture filter:
```
(src net 165.193.0.0/16 or dst net 165.193.0.0/16) and greater 61
```

Common PC softwares can interfere with our capture filter. You can further elaborate by adding additional ports:
```
tcp.port == 12000 || tcp.port == 12170 || tcp.port == 59384 || tcp.port == 57443 || tcp.port == 59359 || udp.port == 12171
```
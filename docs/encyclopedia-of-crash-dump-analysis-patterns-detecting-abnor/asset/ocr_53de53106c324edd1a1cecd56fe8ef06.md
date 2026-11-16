# Network Packet BuildUp

When looking at the network packet pools using NDIS WinDbg extension, we might see increased number of allocated blocks possibly correlated with network problems, for example:

```
```
0: kd> !ndiskd.pktpools * normal
Pool       Allocator  BlocksAllocated BlockSize  PktrsPerBlock PacketLength
8a467e20   b9909f96   0x1             0x1000     0x14          0xc8   tcpip!ARPRegister+119
8a491460   ba4eea56   0x1             0x1000     0x14          0xc8   wanarp!WanpInitializeNdis+a8
8a466508   b905d368   0x1             0x1000     0xd           0x138  tcpip!InitForwardingPools+53
8a373578   b905becb   0x3             0x1000     0x11          0xe8   tcpip!AllocIPPacketList+59
8a466580   b9095ac5   0x1             0x1000     0xe           0x118  tcpip!IPInit+e0
8a460958   bac40a97   0xb             0x1000     0x14          0xc8   vmxnet+a97
```
```

```
```
0: kd> !ndiskd.pktpools * no sent packets
Pool       Allocator  BlocksAllocated BlockSize  PktrsPerBlock PacketLength
8a467e20   b9909f96   0x1             0x1000     0x14          0xc8   tcpip!ARPRegister+119
8a491460   ba4eea56   0x1             0x1000     0x14          0xc8   wanarp!WanpInitializeNdis+a8
8a466508   b905d368   0x1             0x1000     0xd           0x138  tcpip!InitForwardingPools+53
8a373578   b905becb   0xa3            0x1000     0x11          0xe8   tcpip!AllocIPPacketList+59
8a466580   b9095ac5   0x1             0x1000     0xe           0x118  tcpip!IPInit+e0
8a460958   bac40a97   0x9b            0x1000     0x14          0xc8   vmxnet+a97
```
```
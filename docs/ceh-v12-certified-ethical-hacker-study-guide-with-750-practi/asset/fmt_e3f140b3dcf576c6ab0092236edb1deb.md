
We don't have to live with just the default level of detail. We can also ask for more detail about the packets that have been captured. There are multiple levels of verbosity that we can request of `tcpdump`. To get more verbose, we add `-v` to the command line. If we want even more detail than that, we use `-vv` and then `-vvv`. In the following listing, you can see a `tcpdump` capture with `-vv` as a command‑line parameter to get additional details. Additionally, there is a parameter setting the snapshot length to 0. In practice, this sets the number of bytes per packet to 262,144, which is the default setting. This wasn't always the case. It was once the case that the snapshot length was very short, so to get complete packets, you had to tell `tcpdump` not to limit the number of bytes captured.

**`tcpdump` Capturing with Additional Verbosity**

```
root@quiche:~# tcpdump -vv -s 0
tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 262144 bytes
10:40:27.047708 IP (tos 0x0, ttl 1, id 48781, offset 0, flags [DF], proto UDP (17), length 228)
    samsung.lan.8001> st-routers.mcast.net.8001: [udp sum ok] UDP, length 200
10:40:27.048568 IP (tos 0x0, ttl 64, id 64646, offset 0, flags [DF], proto UDP (17), length 68)
    quiche.lan.45867> testwifi.here.domain: [bad udp cksum 0x2dcd -> 0x690e!] 26697+ PTR? 7.0.0.224.in-addr.arpa. (40)
10:40:27.068536 IP (tos 0x0, ttl 64, id 16931, offset 0, flags [DF], proto UDP (17), length 102)
    testwifi.here.domain> quiche.lan.45867: [udp sum ok] 26697 q: PTR? 7.0.0.224.in-addr.arpa. 1/0/0 7.0.0.224.in-addr.arpa. PTR st-routers.mcast.net. (74)
10:40:27.068803 IP (tos 0x0, ttl 64, id 64650, offset 0, flags [DF], proto UDP (17), length 72)
    quiche.lan.46802> testwifi.here.domain: [bad udp cksum 0x2dd1 -> 0x7eb6!] 42424+ PTR? 22.86.168.192.in-addr.arpa. (44)
10:40:27.070769 IP (tos 0x0, ttl 64, id 16932, offset 0, flags [DF], proto UDP (17), length 123)
    testwifi.here.domain> quiche.lan.46802: [udp sum ok] 42424* q: PTR? 22.86.168.192.in-addr.arpa. 1/0/0 22.86.168.192.in-addr.arpa. PTR samsung.lan. (95)
10:40:27.070930 IP (tos 0x0, ttl 64, id 64651, offset 0, flags [DF], proto UDP (17), length 71)
    quiche.lan.49820> testwifi.here.domain: [bad udp cksum 0x2dd0 -> 0x05f9!] 46654+ PTR? 1.86.168.192.in-addr.arpa. (43)
10:40:27.072770 IP (tos 0x0, ttl 64, id 16933, offset 0, flags [DF], proto UDP (17), length 123)
    testwifi.here.domain> quiche.lan.49820: [udp sum ok] 46654* q: PTR? 1.86.168.192.in-addr.arpa. 1/0/0 1.86.168.192.in-addr.arpa. PTR testwifi.here. (95)
10:40:27.072857 IP (tos 0x0, ttl 64, id 64652, offset 0, flags [DF], proto UDP (17), length 72)
    quiche.lan.55520> testwifi.here.domain: [bad udp cksum 0x2dd1 -> 0x3ef4!] 48745+ PTR? 57.86.168.192.in-addr.arpa. (44)
10:40:27.170687 STP 802.1d, Config, Flags [none], bridge-id 7000.2c:08:8c:1c:3b:db.8001, length 43
    message-age 0.00s, max-age 20.00s, hello-time 1.00s, forwarding-delay 4.00s
    root-id 7000.2c:08:8c:1c:3b:db, root-pathcost 0
```

With default `tcpdump` settings, you get the IP header information where it's relevant to the packet—meaning fields of substance are set. When you add verbosity, you get details about the layer 4 headers. If you look at any of the UDP packets, you will see that there is a note saying the checksum is okay, meaning `tcpdump` performed the calculation of the checksum on the message and got the same value as the one in the packet. In the case of TCP segments, you would get details like the sequence and acknowledgment numbers as well as the flags set.

So far, all we have seen is the protocol headers. There hasn't been any payload data. We can take a look at the payload using the `-X` parameter. This performs a hex dump of the payload of the message. Hexadecimal (hex) dumps show each byte in its hexadecimal representation. It also provides an ASCII decode of each byte. This means if the ASCII value is a printable character, you will see that printable character on the right side. Even in cases where you see printable characters, the meaning of the byte to the protocol in use may not be that character. It may just be the numeric value of that byte.

**Hexadecimal Representation of Packet**

```
root@quiche:~# tcpdump -i eth0 -X
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 262144 bytes
10:49:35.174771 STP 802.1d, Config, Flags [none], bridge-id 7000.2c:08:8c:1c:3b:db.8001, length 43
    0x0000:  0000 0000 0070 002c 088c 1c3b db00 0000  …..p.,…;….
    0x0010:  0070 002c 088c 1c3b db80 0100 0014 0001  .p.,…;……..
    0x0020:  0004 0000 0000 0000 0000 00              ………..
10:49:35.578186 IP samsung.lan.8001> st-routers.mcast.net.8001: UDP, length 200
    0x0000:  4500 00e4 c563 4000 0111 bcdf c0a8 5616  E….c@…….V.
    0x0010:  e000 0007 1f41 00d0 9a56 7b22 6461  …..A.A…V{"da
    0x0020:  7461 223a 7b22 7631 223a 7b22 7572 6922  ta":{"v1":{"uri"
    0x0030:  3a22 6874 7470 3a2f 2f31 3932 2e31 3638  :"http://192.16
    0x0040:  2e38 362e 3232 3a38 3030 312f 6d73 2f31  .86.22:8001/ms/1
    0x0050:  2e30 2f22 7d2c 2276 3222 3a7b 2275 7269  .0/"},"v2":{"uri
    0x0060:  223a 2268 7474 703a 2f2f 3139 322e 3136  :"http://192.16
    0x0070:  382e 3836 2e32 323a 3830 3031 2f61 7069  8.86.22:8001/api
    0x0080:  2f76 322f 227d 7d2c 2272 656d 6f74 6522  /v2/"}},"remote
    0x0090:  3a22 312e 3022 2c22 7369 6422 3a22 7575  :"1.0","sid":"uu
    0x00a0:  6964 3a32 6239 3562 6466 652d 6138 3033  id:2b95bdfe-a803
    0x00b0:  2d34 3234 662d 3931 3530 2d34 3532 3434  -424f-915d-915244
    0x00c0:  6338 3162 3862 3022 2c22 7474 6c22 3a38  c81b8b0","ttl":8
    0x00d0:  3030 302c 2274 7970 6522 3a22 616c 6976  000,"type":"aliv
    0x00e0:  6522 7d0a                                e"}.
10:49:35.578979 IP quiche.lan.60408> testwifi.here.domain: 10006+ PTR? 7.0.0.224.in-addr.arpa. (40)
    0x0000:  4500 0044 163c 4000 4011 f6e1 c0a8 5639  E..D.<@.@…..V9
    0x0010:  c0a8 5601 ebf8 0035 0030 2dcd 2716 0100  ..V….5.0-.'…
    0x0020:  0001 0000 0000 0000 0137 0130 0130 0332  ………7.0.0.2
    0x0030:  3234 0769 6e2d 6164 6472 0461 7270 6100  24.in-addr.arpa.
    0x0040:  000c 0001                                ….
10:49:35.599038 IP testwifi.here.domain> quiche.lan.60408: 10006 1/0/0 PTR st-routers.mcast.net. (74)
    0x0000:  4500 0066 4230 4000 4011 cacb c0a8 5601  E..fB0@.@…..V.
    0x0010:  c0a8 5639 0035 ebf8 0052 c096 2716 8180  ..V9.5…R..'…
    0x0020:  0001 0001 0000 0000 0137 0130 0130 0332  ………7.0.0.2
    0x0030:  3234 0769 6e2d 6164 6472 0461 7270 6100  24.in-addr.arpa.
    0x0040:  000c 0001 c00c 000c 0001 0000 0bbc 0016  …………….
    0x0050:  0a73 742d 726f 7574 6572 7305 6d63 6173  .st-routers.mcas
    0x0060:  7403 6e65 7400                           t.net.
```

You will also see `-i eth0` on the command line. This tells `tcpdump` which interface to capture packets on. If you don't say, `tcpdump` will use the default interface. In most cases, that's the single interface in the system. Some systems have multiple interfaces, though. You may want to capture on an interface that isn't default. This means you need to tell `tcpdump` which interface to use. What you don't see here is any of the details from the layer 4 headers. This is because the `-v` parameter wasn't included, indicating we want more verbosity. You can add the verbosity parameters when you start `tcpdump`. You will get the layer 4 information along with the payload of the packet.

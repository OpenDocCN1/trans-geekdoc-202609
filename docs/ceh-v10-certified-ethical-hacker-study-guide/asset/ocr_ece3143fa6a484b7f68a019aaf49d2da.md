You can easily change this behavior, since the DNS requests can get very noisy and it’s hard to weed your way through to get to the traffic you really want to see. This is done by just adding -n to the command line. What you end up with is something like you see here.

# **tcpdump with no name resolution**

```
root@quiche:~# tcpdump -n
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 262144 bytes
20:42:16.326940 IP 192.168.86.210.40608 > 239.255.255.250.1900: UDP, length 558
20:42:16.587114 IP 192.168.86.210.40608 > 239.255.255.250.1900: UDP, length 546
20:42:16.703469 IP 192.168.86.24.5353 > 224.0.0.251.5353: 0 [5a] [5q] [lau] PTR (QM)? _homekit._tcp.local. PTR (QM)? _companion-link._tcp.local. TXT (QM)? 9EA05B22-BBCC-5F9C-9C4B-10A753BDAAD9._homekit._tcp.local. TXT (QU)? milobloom (2)._companion-link._tcp.local. PTR (QM)? _sleep-proxy._udp.local. (282)
20:42:16.704314 IP6 fe80::10ba:d862:9623:e420.5353 > ff02::fb.5353: 0 [5a] [5q] [lau] PTR (QM)? _homekit._tcp.local. PTR (QM)? _companion-link._tcp.local. TXT (QM)? 9EA05B22-BBCC-5F9C-9C4B-10A753BDAAD9._homekit._tcp.local. TXT (QU)? milobloom (2)._companion-link._tcp.local. PTR (QM)? _sleep-proxy._udp.local. (282)
20:42:16.832644 IP 192.168.86.210.40608 > 239.255.255.250.1900: UDP, length 536
20:42:16.845825 IP 192.168.86.46.5353 > 224.0.0.251.5353: 0*- [0q] 1/0/1 (Cache flush) TXT "si=AAB36E20-CDDB-4E60-EBEE-1BC0A3ABE82D" (141)
20:42:16.846030 IP6 fe80::1cbd:790c:b9f2:ae0b.5353 > ff02::fb.5353: 0*- [0q] 1/0/1 (Cache flush) TXT "si=AAB36E20-CDDB-4E60-EBEE-1BC0A3ABE82D" (141)
20:42:16.885944 IP 192.168.86.49.5353 > 224.0.0.251.5353: 0*- [0q] 1/0/1 (Cache flush) TXT "rpBA=AC:C5:14:0E:E0:35" "rpAD=c=77102094021" "rpHI=f27b7868fdf6f" "rpHN=ce75eb6a989e" "rpVr=164.16" "rpHA=ae260764c13d" (192)
20:42:16.885964 IP6 fe80::1882:675c:7bdd:2de3.5353 > ff02::fb.5353: 0*- [0q] 1/0/1 (Cache flush) TXT "rpBA=AC:C5:14:0E:E0:35" "rpAD=c=77102094021" "rpHI=f27b7868fdf6f" "rpHN=ce75eb6a989e" "rpVr=164.16" "rpHA=ae260764c13d" (192)
```

Much of what we see is fairly straightforward, though it may or may not be especially useful. As an example, the first captured packet is an IP packet. It tells us that right after the time stamp. Then we see the source address followed by >, showing the direction and then the destination address. This tells us that the packet is UDP and the length is 558. What we can also tell there is that the UDP datagram is the simple service discovery protocol (SSDP), part of universal plug and play (UPnP). We can tell this even without the assistance of tcpdump by just looking up the destination port number, if we don't happen to know that 1900 is a UPnP port. The source port for the datagram is just an ephemeral port, assigned by the operating system when the message is sent out on the network.

![](bbox=[0.137, 0.82, 0.23, 0.875])

You may have noticed that the user logged into the system is root. Because we have to set a parameter in the hardware, we have to run tcpdump as an administrative user. On Linux, this is root. On Windows, it would be anyone in the Administrators group or another group that had permissions to interface with the network hardware like that.
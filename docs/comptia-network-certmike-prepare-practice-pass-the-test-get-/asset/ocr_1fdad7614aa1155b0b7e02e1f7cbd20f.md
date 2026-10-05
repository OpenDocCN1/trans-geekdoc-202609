# Chapter 23 • Network Software Tools and Commands

Traceroute is an especially valuable tool on a large enterprise network because it can provide the troubleshooter with information about the routes packets taking through the network. For example, in the sample display, notice the jump in the round-trip times from the 100s to the 200s when the route takes packets from North America to servers in the United Kingdom.

# Arp

As described in Chapter 11, "Switching, the Address Resolution Protocol (ARP) is a data link protocol that systems use to resolve IP addresses into media access control (MAC) addresses. This then saves the routing pair of addresses to an ARP table, which saves memory for reuse.
In addition to the protocol itself, there is also an arp utility in both Windows and Unix/Linux that allows users to display and modify the contents of the ARP table. Running arp -a from the command line, produces a display like this:

```
Interface: 192.168.1.21 --- 0xe
Internet Address Physical Address Type
192.168.1.1 28-80-18-e7-e5 dynamic
192.168.1.11 84-b8-b8-2d-18-69 dynamic
192.168.1.14 20-ef-bd-33-bc-e8 dynamic
192.168.1.16 1c-1e-e3-b6-ae-42 dynamic
192.168.1.23 9e-d3-cf-bf-c3-2d dynamic
```

# Netstat

Netstat is a Windows and Linux command that can display a variety of network statistics about a system's TCP and UDP connections. Running the command netstat with no parameters displays a list of the computer's currently open sessions

Proto Local Address Foreign Address State
TCP 127.0.0.1:49994 M213:60757 ESTABLISHED
TCP 127.0.0.1:59423 CL73:59424 ESTABLISHED
TCP 192.168.1.21:57617 52.56.69:2 ESTABLISHED
TCP 192.168.1.21:57633 140:https TIME_WAIT
TCP 192.168.1.21:57638 40.96.190:18 TIME_WAIT
TCP 192.168.1.21:57662 40.97.186:226 ESTABLISHED
TCP 192.168.1.21:57674 a184-212-9:179 ESTABLISHED
TCP 192.168.1.21:57680 220:https ESTABLISHED
TCP 192.168.1.21:57681 219.21.13.15:http ESTABLISHED
TCP 192.168.1.21:57684 52.46.181.98:https ESTABLISHED
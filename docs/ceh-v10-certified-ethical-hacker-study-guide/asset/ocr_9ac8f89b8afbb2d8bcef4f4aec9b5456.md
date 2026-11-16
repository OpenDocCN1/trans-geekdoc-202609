```
ICMP Host Unreachable from 192.168.86.31 for ICMP Echo sent to 192.168.86.4
ICMP Host Unreachable from 192.168.86.31 for ICMP Echo sent to 192.168.86.4
ICMP Host Unreachable from 192.168.86.31 for ICMP Echo sent to 192.168.86.3
ICMP Host Unreachable from 192.168.86.31 for ICMP Echo sent to 192.168.86.3
ICMP Host Unreachable from 192.168.86.31 for ICMP Echo sent to 192.168.86.7
ICMP Host Unreachable from 192.168.86.31 for ICMP Echo sent to 192.168.86.7
ICMP Host Unreachable from 192.168.86.31 for ICMP Echo sent to 192.168.86.6
ICMP Host Unreachable from 192.168.86.31 for ICMP Echo sent to 192.168.86.6
```

Since the e parameter was passed to fping, it provides the elapsed time. This is the round-trip time between the message that was sent and the response that was received.
Some of these round-trip times are fairly high, considering it’s all on the local network,
even if fping is running on a virtual machine, where the host operating system is using
wireless.

While we have a lot of systems indicating responses, that doesn’t mean those are the
only systems that exist on the network. Since this is the local network, we can be reason-
ably sure that all of this information is correct. However, network- and host-based firewalls
may also block these ICMP echo requests. Just because you don’t get a response does not
mean that the hosts are not up. It may mean that there is something that’s blocking the
message. A firewall may respond with an ICMP host unreachable, just as you see in the
preceding code, or it may simply drop the message, meaning there would be no response.
There may be other reasons for lack of a response, though.

# Using MegaPing

Another tool that can perform a ping sweep, as well as several other functions, is
MegaPing. MegaPing is a GUI-based tool that runs under Windows. It incorporates several
functions into a single interface. The ping sweep can be accomplished using the IP Scanner
tool, which you would select from the list on the left-hand side. Figure 5.1 shows the full
interface after running the IP scan. By default, the MAC address and hostnames are not
included in the list. There are check boxes on the right-hand side, however, that can be
checked even after you have run a scan, and the information will be added.

Also along the left-hand side, you will see several other tools that you can make use of.
It becomes a bit of a Swiss Army knife for the purposes of network troubleshooting. In
addition to troubleshooting network issues, there is also a port scanning tool. I’ll cover port
scanning in more detail in the next section. There are other enumeration utilities you may
find useful as you are identifying systems and services on your target network.
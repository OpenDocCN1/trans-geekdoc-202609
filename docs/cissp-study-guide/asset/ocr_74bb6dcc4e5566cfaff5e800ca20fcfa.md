iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml. Most Linux and UNIX systems have a smaller list of well-known ports in /etc/services.

# Socket Pairs

A socket is a combination of an IP address and a TCP or UDP port on one node. A socket pair describes a unique connection between two nodes: source port, source IP, destination port, and destination IP. The netstat output in Fig. 5.6 shows a socket pair between source IP 192.168.80.144, TCP source port 51178, and destination IP 192.168.2.44, TCP destination port 22.

A socket may “listen” (wait for a connection); a listening socket is shown as 127.0.0.1:631 in Fig. 5.6. A socket pair is then “established” during a connection. You may have multiple connections from the same host (such as 192.168.80.144), to the same host (192.168.2.4), and even to the same port (22). The OS and intermediary devices such as routers are able to keep these connections unique due to the socket pairs. In the previous example, two connections from the same source IP and to the same IP/destination port would have different source ports, making the socket pairs (connections) unique.

# TCP Flags

The original six TCP flags are:

+   - URG: Packet contains urgent data
- ACK: Acknowledge received data
- PSH: Push data to application layer
- RST: Reset (tear down) a connection
- SYN: Synchronize a connection
- FIN: Finish a connection (gracefully)

Two new TCP flags were added in 2001: CWR (Congestion Window Reduced) and ECE (Explicit Congestion Notification Echo), using formerly reserved bits in the TCP header. A third new flag was added in 2003: NS (Nonce Sum). These flags are used to manage congestion (slowness) along a network path. All 9 TCP flags are shown in Fig. 5.7.

```
root@ubuntu:~# netstat -nat
Active Internet connections (servers and established)
Proto Recv-Q Send Local Address         Foreign Address         State
tcp     0       0 0.0.0.0:*               *:*                    LISTEN
tcp     0       0 192.168.80.144:51178  192.168.2.44:ESTABLISHED
```

FIG. 5.6

Socket pair.
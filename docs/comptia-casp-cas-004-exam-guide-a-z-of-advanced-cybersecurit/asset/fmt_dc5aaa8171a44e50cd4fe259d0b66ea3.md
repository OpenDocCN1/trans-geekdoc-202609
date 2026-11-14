
# Security Assessment Tools

## Password Crackers: John the Ripper

John the Ripper is another example of a password cracker. It identifies weak UNIX passwords, but it also supports hashes for a variety of other platforms. There are three versions of John the Ripper – a free official version, a community improved version (with numerous contributed patches but less quality assurance), and a cheap pro version. If you’re having trouble enforcing strong or complicated passwords and need to uncover weak passwords on your network, you may use a password cracker to determine which ones are weak and perhaps crack them. If assessing password security is time-sensitive, save the password file to one of your more powerful PCs (a cluster is even better) and execute the password cracker on that platform. This way, you’ll be able to use the extra resources to complete the audit more rapidly.

## Host Vulnerability Scanners

Like network vulnerability scanners, host scanners scan for vulnerabilities —but only on the host on which the tool is installed. Many scanners can do both. The Microsoft Baseline Security Analyzer is a host scanner that can also scan multiple hosts at once. It returns a clean list of all vulnerabilities and prioritizes them, as shown in [Figure 13.14](#c13.xhtml#fig13_14):

![](images/Image28199.jpg)

**Figure 13.14:** Microsoft Baseline Security Analyzer Output

## Command-Line Tools

Many local command-line utilities are available in both Windows and Linux/UNIX for making security assessments as well. While not as user-friendly as some of the more automated tools, they are preferred by many of the more experienced in the field for their flexibility, as they do require more knowledge and background. The following sections discuss several security-related command-line tools.

### Netstat

On a TCP/IP-based system, the `netstat` (network status) command is used to see what ports are listening. The `-a` option displays all ports, whereas `/?` displays what additional choices are available. (The possibilities vary depending on the operating system.) The current connections are displayed when the program is run without any switches, as shown in [Figure 13.15](#c13.xhtml#fig13_15). `netstat` can help you figure out which ports are open and which services/protocols are using them. These open ports might put the host’s security at risk. Refer to [Figure 13.15](#c13.xhtml#fig13_15) for the `netstat` output:

![](images/Image28207.jpg)

**Figure 13.15:** netstat Output

Each line of `netstat` output lists the source IP address and port number, the destination IP address or hostname, and the state of the connection. The following are the possible states:

*   `LISTEN`: Represents waiting for a connection request from any remote TCP connection and port.
*   `SYN-SENT`: Represents waiting for a matching connection request after having sent a connection request.
*   `SYN-RECEIVED`: Represents waiting for a confirming connection request acknowledgment after having both received and sent a connection request.
*   `ESTABLISHED`: Represents an open connection, and the data received can be delivered to the user. This is the normal state for the data transfer phase of the connection.
*   `FIN-WAIT-1`: Represents waiting for a connection termination request from the remote TCP connection or an acknowledgment of the connection termination request previously sent.
*   `FIN-WAIT-2`: Represents waiting for a connection termination request from the remote TCP connection.
*   `CLOSE-WAIT`: Represents waiting for a connection termination request from the local user.
*   `CLOSING`: Represents waiting for a connection termination request acknowledgment from the remote TCP connection.
*   `LAST-ACK`: Represents waiting for an acknowledgment of the connection termination request previously sent to the remote TCP connection (which includes an acknowledgment of its connection termination request).

### Ping

To verify the connection between two devices, the `ping` command uses the ICMP protocol. The TCP/IP protocol’s `ping` command is one of the most helpful. It transmits a sequence of packets to another system, which responds with a response of its own. When troubleshooting difficulties with distant hosts, the `ping` command may be incredibly beneficial. The `ping` command shows whether or not the host can be contacted and how long it takes for the host to respond. The time on a LAN is displayed as less than 10 milliseconds. However, on WAN networks, this figure can be significantly higher. `ping` also tries to resolve the hostname associated with the IP address when the `-a` parameter is used. A successful `ping` is shown in [Figure 13.16](#c13.xhtml#fig13_16):

![](images/Image28214.jpg)

**Figure 13.16:** Successful Ping

[Figure 13.17](#c13.xhtml#fig13_17) shows an unsuccessful `ping`. In this case, the request timed out, which typically means the host is off or disconnected from the network. When the destination cannot be reached, an error code is displayed. Refer to [Figure 13.7](#c13.xhtml#fig13_7) for failed `ping`:

![](images/Image28224.jpg)

**Figure 13.17:** Failed Ping

The most common of these codes are as follows:

*   `Destination unreachable`: This indicates that the IP datagram could not be forwarded. This also includes an error code (number) that indicates more detail—for example, that there is no routing table entry or the destination is reachable but did not respond to ARP.
*   `Request timed out`: This indicates that the TTL of the datagram was exceeded. This means you did not even get a response from a router. This can occur if the router is configured to not respond to ICMP, which is not uncommon. This is the situation in [Figure 13.17](#c13.xhtml#fig13_17).

Although there are easier ways to do this with other tools, such as `Nmap`, you can perform a ping sweep by creating a simple batch file, as follows:

```
for /l %i in(1,1,254) do ping -n 1 -w 100 <first three octets of host network>.%i
```

For example, to sweep the 192.168.1.0 network, you can use the following command:

```
for /l %i in(1,1,254) do ping -n 1 -w 100 192.168.1.%i
```

### Tracert/Traceroute

The `traceroute` command (in Linux and UNIX) is used to trace a packet’s journey via the network. Its most useful purpose is determining where a packet is lost in the network. It displays each hop (router) that the packet passes through, as well as the time it takes to do so. A traced route to [www.nascar.com](http://www.nascar.com) is shown in part in [Figure 13.18](#c13.xhtml#fig13_18). This command may also be used to record the route to a target and show it visually from within `Nmap` (`Zenmap`); graphical results are often simpler to interpret than command-line output. Each line indicates a hop, or a network that the communication passed through (that is, a router). Many times, these routes cannot be completely mapped because ICMP is blocked at the edge of the network in which the destination resides. Refer to [Figure 13.18](#c13.xhtml#fig13_18), which illustrates the `tracert` output:

![](images/Image28291.jpg)

**Figure 13.18:** Tracert Output

### Ipconfig/Ifconfig

The `ipconfig` command is used to view the IP configuration of a device and, when combined with certain switches or parameters, can be used to release and renew the lease of an IP address obtained from a DHCP server and to flush the DNS resolver cache. Its most common use is to view the current configuration. [Figure 13.19](#c13.xhtml#fig13_19) shows its execution with the `/all` switch, which results in a display of a wealth of information about the IP configuration:

![](images/Image28303.jpg)

**Figure 13.19:** Ipconfig Output

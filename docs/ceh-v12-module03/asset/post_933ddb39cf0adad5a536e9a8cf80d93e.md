
## Port Scanning Techniques

The port scanning techniques are categorized according to the type of protocol used for communication

![](img/198108450322f24970ade227cbf24f47_44_0.png)

## Port Scanning Techniques (Cont’d)

| Scanning Technique | Nmap Command | Request | Response | Advantages | Disadvantages |
|---|---|---|---|---|---|
| TCP Connect/Full-Open Scan | nmap -sT -v <Target IP Address> | SYN packets | ✓ SYN+ACK packet response - Port is open<br>✓ RST packet response - Port is closed | ✓ Does not require super-user privileges | ✓ Easily detectable and filterable<br>✓ The logs in the target system disclose the connection |
| Stealth Scan (Half-Open Scan) | nmap -sS -v <Target IP Address> | Single SYN packet | ✓ SYN+ACK packet response - Port is open<br>✓ RST packet response - Port is closed | ✓ Bypasses firewall rules and logging mechanisms |  |
| Inverse TCP Flag Scan | nmap -sF -sN -sX -v <Target IP Address> | Probe packet (FIN/URG/PSH/NULL) | ✓ No response - Port is open<br>✓ RST packet response - Port is closed | ✓ Avoids many IDS and logging systems; highly stealthy | ✓ Requires raw access to network sockets and super-user privileges<br>✓ Not effective against Microsoft Windows hosts, in particular |
| Xmas Scan | nmap -sX -v <Target IP Address> | Probe packet (FIN + URG + PSH) | ✓ No response - Port is open<br>✓ RST packet response - Port is closed | ✓ Avoids IDS and the TCP three-way handshake | ✓ Works only when systems are compliant with the RFC 793-based TCP/IP implementation<br>✓ Works on the Unix platform only<br>✓ Does not work against any current version of Microsoft Windows |
| FIN Scan | nmap -sF -v <Target IP Address> | Probe packet (FIN) | ✓ No response - Port is open<br>✓ RST packet response - Port is closed |  |  |
| NULL Scan | nmap -sN -v <Target IP Address> | Probe packet (NULL) | ✓ No response - Port is open<br>✓ RST packet response - Port is closed | ✓ Probe packets enabled with TCP flags can pass through filters undetected, depending on the security mechanisms installed<br>✓ Works only when systems are compliant with the RFC 793-based TCP/IP implementation | ✓ Effective only when used with Unix-based OSes<br>✓ Does not work against any current version of Microsoft Windows |
| TCP Maimon Scan | nmap -sM -v <Target IP Address> | Probe packet (FIN/ACK) | ✓ No response - Port is open<br>✓ ICMP unreachable error response - Port is filtered<br>✓ RST packet response - Port is closed |  |  |
| ACK Flag Probe Scan | nmap -sA -v <Target IP Address> | ACK probe packets | ✓ No response - Port is filtered (stateful firewall is present)<br>✓ RST packet response - Port is not filtered (no firewall is present) |  |  |
| TTL-Based ACK Flag Probe Scan | nmap -sA --ttl 100 -v <target IP address> | ACK probe packets (several thousands) to different TCP ports | ✓ RST packet response - Port is open (TTL value on a port < 64)<br>✓ RST packet response - Port is closed (TTL value on a port > 64) | ✓ Can evade IDS in most cases<br>✓ Helps in checking the filtering systems of target networks | ✓ Extremely slow and can exploit only older OSes with vulnerable BSD-derived TCP/IP stacks |
| Window-Based ACK Flag Probe Scan | nmap -sA -sW -v <target IP address> | ACK probe packets (several thousands) to different TCP ports | ✓ RST packet response - Port is open (WINDOW value on a port is non-zero)<br>✓ ICMP unreachable error response - Port is filtered<br>✓ RST packet response - Port is closed (WINDOW value on a port is zero) |  |  |
| IDLE/IPID Header Scan | nmap -sI <Zombie Hostname> <Target Hostname> | SYN packet | ✓ SYN+ACK packet response - Port is open<br>✓ RST packet response - Port is closed | ✓ Offers the complete blind scanning of a remote host | ✓ Requires the identification of sequence numbers of the zombie host |
| UDP Scan | nmap -sU -v <Target IP Address> | UDP packet | ✓ No response - Port is open<br>✓ ICMP unreachable error response - Port is closed | ✓ Less overhead with regard to an open port because there is no overhead of a TCP handshake<br>✓ Microsoft-based OSes do not usually implement any ICMP rate limiting; hence, this scan operates very efficiently on Windows-based devices | ✓ Slow because it limits the ICMP error message rate as a form of compensation to machines that apply RFC 1812 section 4.3.2.8<br>✓ A remote host will require access to the raw ICMP socket to distinguish closed ports from unreachable ports<br>✓ Requires privileged access |
| SCTP INIT Scan | nmap -sY -v <Target IP Address> | INIT chunk | ✓ INIT+ACK chunk - Port is open<br>✓ ICMP unreachable exception - Port is filtered<br>✓ ABORT chunk - Port is closed | ✓ An INIT scan is performed quickly by scanning thousands of ports per second on a fast network not obstructed by a firewall, offering a strong sense of security<br>✓ Can clearly differentiate between various ports such as open, closed, and filtered states |  |
| SCTP COOKIE ECHO Scan | nmap -sZ -v <Target IP Address> | COOKIE ECHO chunk | ✓ No response - Port is open<br>✓ ABORT chunk - Port is closed | ✓ The COOKIE ECHO chunk is not blocked by non-stateful firewall rule sets.<br>✓ Only an advanced IDS can detect an SCTP COOKIE ECHO scan | ✓ Cannot differentiate clearly between open and filtered ports, showing the output as open|filtered in both cases |

## Port Scanning Techniques

Port scanning techniques are further categorized as described below. This categorization is based on the type of protocol used for communication in the network.

### TCP Scanning:
- Open TCP Scanning Methods
  - TCP Connect/Full-open Scan
- Stealth TCP Scanning Methods
  - Half-open Scan
  - Inverse TCP Flag Scan
    - Xmas Scan
    - FIN Scan
    - NULL Scan
    - Maimon Scan
  - ACK Flag Probe Scan
    - TTL-Based Scan
    - Window-Based Scan
- Third Party and Spoofed TCP Scanning Methods
  - IDLE/IP ID Header Scan

### UDP Scanning:
- UDP Scanning

### SCTP Scanning:
- SCTP INIT Scanning
- SCTP COOKIE/ECHO Scanning

### SSDP Scanning:
- SSDP and List Scanning

### IPv6 Scanning:
- IPv6 Scanning

### TCP Connect/Full-Open Scan

Source: https://insecure.org

TCP Connect/Full Open Scan is one of the most reliable forms of TCP scanning. In TCP Connect scanning, the OS’s TCP connect() system call tries to open a connection to every port of interest on the target machine. If the port is listening, the connect() call will result in a successful connection with the host on that particular port; otherwise, it will return an error message stating that the port is not reachable.

TCP Connect scan completes a three-way handshake with the target machine. In the TCP three-way handshake, the client sends a SYN packet, which the recipient acknowledges with a SYN+ACK packet. Then, the client acknowledges the SYN+ACK packet with an ACK packet to complete the connection. Once the handshake is completed, the scanner sends an RST packet to end the connection.

![](img/198108450322f24970ade227cbf24f47_47_0.png)

Figure 3.33: Scan result when a port is open

![](img/198108450322f24970ade227cbf24f47_47_1.png)

Figure 3.34: Scan result when a port is closed

Making a separate connect() call for every targeted port in a linear manner would take a long time over a slow connection. The attacker can accelerate the scan using many sockets in parallel. Using non-blocking, I/O allows the attacker to set a short time-out period and watch all the sockets simultaneously. In Zenmap, the -sT option is used to perform TCP Connect/full open scan.

![](img/198108450322f24970ade227cbf24f47_48_0.png)

Figure 3.35: TCP Connect/Full Open scan using Zenmap

The drawback of this type of scan is that it is easily detectable and filterable. The logs in the target system will disclose the connection. Such scanning does not require superuser privileges.

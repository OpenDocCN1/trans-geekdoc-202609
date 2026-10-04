# Note

Some client operating systems may use registered port numbers instead of dynamic port numbers for assigning source ports.

Table 14-4 displays some common well-known port numbers and their associated applications.

# Table 14-4  Well-Known Port Numbers

| Port Number | Protocol | Application |
|---|---|---|
| 20 | TCP | File Transfer Protocol (FTP)—data |
| 21 | TCP | File Transfer Protocol (FTP)—control |
| 22 | TCP | Secure Shell (SSH) |
| 23 | TCP | Telnet |
| 25 | TCP | Simple Mail Transfer Protocol (SMTP) |
| 53 | UDP, TCP | Domain Name Service (DNS) |
| 67 | UDP | Dynamic Host Configuration Protocol (DHCP)—server |
| 68 | UDP | Dynamic Host Configuration Protocol (DHCP)—client |
| 69 | UDP | Trivial File Transfer Protocol (TFTP) |
| 80 | TCP | Hypertext Transfer Protocol (HTTP) |
| 110 | TCP | Post Office Protocol version 3 (POP3) |
| 143 | TCP | Internet Message Access Protocol (IMAP) |
| 161 | UDP | Simple Network Management Protocol (SNMP) |
| 443 | TCP | Hypertext Transfer Protocol Secure (HTTPS) |

Some applications can use both TCP and UDP. For example, DNS uses UDP when clients send requests to a DNS server. However, communication between two DNS servers always uses TCP.

Search the IANA website for *port registry* to view the full list of port numbers and associated applications.

# The netstat Command (14.4.4)

Unexplained TCP connections can pose major security threats. They can indicate that something or someone is connected to the local host. Sometimes it is necessary to know which active TCP connections are open and running on a networked host.
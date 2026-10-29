# SSDP and List Scan

# SSDP Scan

+   - The Simple Service Discovery Protocol (SSDP) is a network protocol that works in conjunction with the UPnP to detect plug and play devices
+   - Vulnerabilities in UPnP may allow attackers to launch Buffer overflow or DoS attacks
+   - Attacker may use the UPnP SSDP M-SEARCH information discovery tool to check if the machine is vulnerable to UPnP exploits or not

# List Scan

+   - This type of scan simply generates and prints a list of IPs/Names without actually pinging them
+   - A reverse DNS resolution is performed to identify the host names

![](bbox=[0.2, 0.24, 0.48, 0.41])

![](bbox=[0.58, 0.28, 0.87, 0.4])

# SSDP and List Scan

# SSDP Scan

Simple Service Discovery Protocol (SSDP) is a network protocol that generally communicates with machines when querying them with routable IPv4 or IPv6 multicast addresses. The SSDP service controls communication for the Universal Plug and Play (UPnP) feature. It generally works when the machine is not firewalled; however, it can sometimes work through a firewall. The SSDP service will respond to a query sent over IPv4 or IPv6 broadcast addresses. This response includes information about the UPnP feature associated with it. The attacker uses SSDP scanning to detect UPnP vulnerabilities that may allow him/her to launch buffer overflow or DoS attacks.
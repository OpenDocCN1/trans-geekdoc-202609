# Host Discovery Techniques

Host discovery techniques are used to identify the active/live systems in the network

![](bbox=[0.16, 0.175, 0.84, 0.405])

# Host Discovery Techniques (Cont’d)

![](bbox=[0.33, 0.485, 0.66, 0.545])

| Scanning Technique | Nmap Command | Request | Response | Advantages |
|---|---|---|---|---|
| ARP Ping Scan | nmap -sn -PR <Target IP Address> | ARP request probe | ✓ ARP response - Host is active
✓ No response - Host is inactive | ✓ More efficient and accurate than other host discovery techniques
✓ Useful for system discovery, where one may need to scan large address spaces |
| UDP Ping Scan | nmap -sn -PU <Target IP Address> | UDP request | ✓ UDP response - Host is active
✓ Error messages (host/network unreachable or TTL exceeded) - Host is inactive | ✓ Detects systems behind firewalls with strict TCP filtering |
| ICMP ECHO Ping Scan | nmap -sn -PE <Target IP Address> | ICMP ECHO request | ✓ ICMP ECHO reply - Host is active
✓ No response - Host is inactive | ✓ Useful for locating active devices or determining if the ICMP message passes through a firewall
**Disadvantage:**
✓ Does not work on Windows-based networks |
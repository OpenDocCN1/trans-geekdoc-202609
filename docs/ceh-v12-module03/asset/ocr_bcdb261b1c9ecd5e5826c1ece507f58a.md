# IPv6 Scan

+   - IPv6 increases the IP address size from 32 bits to 128 bits to support more levels of address hierarchy
+   - Attackers need to harvest IPv6 addresses from network traffic, recorded logs, or Received from: header lines in archived emails
+   - Attackers can use the -6 option in Zenmap to perform IPv6 scanning

![](bbox=[0.79, 0.1, 0.86, 0.13])

```
root@ :~# nmap -6 scanme.nmap.org
Starting Nmap ( http://nmap.org ) at 04:25 UTC
Nmap scan report for scanme.nmap.org (2600:3c01::f03c:91ff:fe18:bb2f)
Host is up (0.062s latency).
Not shown: 997 closed ports
PORT      STATE SERVICE
22/tcp    open  ssh
80/tcp    open  http
31337/tcp open  Elite

Nmap done: 1 IP address (1 host up) scanned in 3.94 seconds
```

![](bbox=[0.16, 0.3, 0.22, 0.35])

![](bbox=[0.78, 0.3, 0.84, 0.35])

# IPv6 Scan

IPv6 increases the size of the IP address space from 32 bits to 128 bits to support higher levels of the addressing hierarchy. Traditional network scanning techniques are computationally less feasible because of the larger search space (64 bits of host address space, or 2^64 addresses) provided by IPv6 in a subnet. Scanning the IPv6 network is more difficult and complex compared to IPv4. Additionally, a number of scanning tools do not support ping sweeps on IPv6 networks. Attackers need to harvest IPv6 addresses from network traffic, recorded logs, or "Received from" and other header lines in archived email or Usenet news messages to identify IPv6 addresses for subsequent port scanning. However, scanning an IPv6 network provides a large number of hosts in a subnet; if an attacker can compromise one subnet host, he/she can probe the "all hosts" link local multicast address if the hosts numbers are sequential or use any regular scheme. An attacker needs to analyze 2^64 addresses to verify if a particular open service is running on a host in that subnet. At a conservative rate of one probe per second, such a scan would take about 5 billion years to complete. Attackers can use Nmap to perform IPv6 scanning. In Zenmap, the -6 option is used to perform the IPv6 scan.

```
root@ :~# nmap -6 scanme.nmap.org
Starting Nmap ( http://nmap.org ) at 04:25 UTC
Nmap scan report for scanme.nmap.org (2600:3c01::f03c:91ff:fe18:bb2f)
Host is up (0.062s latency).
Not shown: 997 closed ports
PORT      STATE SERVICE
22/tcp    open  ssh
80/tcp    open  http
31337/tcp open  Elite

Nmap done: 1 IP address (1 host up) scanned in 3.94 seconds
```

Figure 3.74: IPv6 Scan using nmap
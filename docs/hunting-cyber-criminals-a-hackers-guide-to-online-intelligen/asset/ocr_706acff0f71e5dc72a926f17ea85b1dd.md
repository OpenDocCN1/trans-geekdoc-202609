# Change Data Length

Port scanners typically send the same size requests, so some firewalls/IDS are designed to detect port scans by looking at the size of the packet. We can try to avoid that type of detection by using the -data-length parameter and specifying additional data to the packets. If you are going to experiment with this, scanning a single port that you know is open (like 80 or 443) and play around with the packet size until you receive a response that you like:

```
root@OSINT: nmap -sS -data-length 300 scanneme.nmap.org
```

Starting Nmap 7.01 ( https://nmap.org ) at 2018-12-12 08:52 UTC
map scan report for scanneme.nmap.org (45.33.256)
Host is up (0.088s latency).
Other addresses for scanneme.nmap.org (not scanned):
2600:3c01:f0c3:diff:fe18:bb2f
Not shown: 98 closed ports
PORT STATE SERVICE
22/tcp open ssh
80/tcp open http
9929/tcp open nping-echo
31337/tcp open Elite

Nmap dose: 1 IP address (1 host up) scanned in 2.41 seconds

# IP/MAC Address Spoofing

Another method for to bypass firewall detection is to spoof the MAC address of your host. This technique can be very effective if the server has a MAC filtering rule that only allows traffic from certain MAC addresses. The downside is you will need to know the MAC address of a machine that is allowed to query your servers. This technique is more likely to be used on an internal network scan. If you know a target uses a specific vendor, you can try to gather MAC addresses from their products and use those in your scan.

Similarly, you can spoof the source port or an IP address so the target thinks you are coming from a host within the target's subnet. There are instances where firewalls will allow requests from certain ports or IPs, so this might be worth trying.

> NOTE Spoofing your IP address means you will never see the return packet you have access to IP address. Spoofing an IP address of a scan requires you to bind your request to a network interface using the -e switch. This will typically require you to set up a fake internal network card on your computer (like vnic1) and
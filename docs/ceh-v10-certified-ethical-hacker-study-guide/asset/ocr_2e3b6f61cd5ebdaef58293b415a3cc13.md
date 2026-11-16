# Ettercap DNS Spoof Log (continued)

```
SEND L3 ERROR: 83 byte packet (0800:06) destined to 192.168.86.26 was not forwarded (libnet_write_raw_ipv4(): -1 bytes written (Network is unreachable))
)
SEND L3 ERROR: 52 byte packet (0800:06) destined to 192.168.86.26 was not forwarded (libnet_write_raw_ipv4(): -1 bytes written (Network is unreachable))
)
SEND L3 ERROR: 52 byte packet (0800:06) destined to 192.168.86.26 was not forwarded (libnet_write_raw_ipv4(): -1 bytes written (Network is unreachable))
)
SEND L3 ERROR: 48 byte packet (0800:11) destined to 192.168.86.26 was not forwarded (libnet_write_raw_ipv4(): -1 bytes written (Network is unreachable))
)
SEND L3 ERROR: 48 byte packet (0800:11) destined to 192.168.86.26 was not forwarded (libnet_write_raw_ipv4(): -1 bytes written (Network is unreachable))
)
SEND L3 ERROR: 48 byte packet (0800:11) destined to 192.168.86.26 was not forwarded (libnet_write_raw_ipv4(): -1 bytes written (Network is unreachable))
)
SEND L3 ERROR: 52 byte packet (0800:06) destined to 192.168.86.26 was not forwarded (libnet_write_raw_ipv4(): -1 bytes written (Network is unreachable))
)
SEND L3 ERROR: 245 byte packet (0800:06) destined to 192.168.86.26 was not forwarded (libnet_write_raw_ipv4(): -1 bytes written (Network is unreachable))
)
DHCP: [192.168.86.1] ACK : 192.168.86.43 255.255.255.0 GW 192.168.86.1 DNS
192.168.86.1 "lan"
dns_spoof: A [browser.pipe.aria.microsoft.com] spoofed to [107.170.40.56]
```

The reason this works, even though the DNS request does go out to the legitimate DNS server and it responds, is because DNS is UDP, so there is no connection to be made. A UDP-based request goes out and a UDP-based response comes back. A system may send out multiple requests, since they are UDP and there is no guarantee the request will get to the DNS server. The first response that is received by the requesting system will be used. Since the Ettercap system is on the local network and there is a good chance the DNS server is not, the DNS response from the Ettercap system should be the first one back. Any subsequent responses to the requesting system will be ignored. By that point, the address configured in etter.dns has been sent back to the requesting system and populated the DNS cache on that system.

# sslstrip

Encrypted messages are problematic when it comes to capturing traffic. Encryption is intended to be end to end, meaning there is no way to sit in the middle. Any mechanism
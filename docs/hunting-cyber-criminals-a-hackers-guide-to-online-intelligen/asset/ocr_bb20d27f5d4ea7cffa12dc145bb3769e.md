# 138 Part II | Web Exploration

Finally, we can ensure that site usernames are enumerated by enumerate u. Typically this is included in a default scan but is skipped when scanning in stealthy mode.

> WARNING The ability to rotate IP addresses does not come with WPScan. Please do not expect this functionality out of the box with this (or any other) tool. I use a paid proxy service called Storm Proxies that automatically rotates my IPs on every request. The flow works like this:

+   - WPScan allows me to use an IP address →
- Storm Proxies provides me with an IP address that I use as my proxy address →
- For each request that we make to it, Storm Proxies relays it through a different address.

Putting it all together, our request looks like this:

```
root@OSINT:/opt/wscan: wscan --url http://www.nightlionsecurity.com \ --stealth --force proxy 'socks5:127.0.0.1:9050' --enumerate u
```

The new scan resulted in the following output:

```
[+] URL: https://www.nightlionsecurity.com/
[+] Started: Thu Jan 3 04:30:13 2019
```

```
Interesting Finding(s):
[+] https://www.nightlionsecurity.com/
| Interesting Entries:
| Server: nginx
| X-Powered-By: PHP/7.1.25, PleskLin
| Access-Control-Allow-Origin: cdn.nightlionsecurity.com
Found By: Headers (Passive Detection)
| Confidence: 100%
```

```
[i] User(s) Identified:
```

```
[+] Vinny
| Detected By: Rss Generator (Passive Detection)
| Confirmed By: Rss Generator (Aggressive Detection)
```

```
[+] BlogAdmin
```
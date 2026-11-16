# Nmap Full Connect Scan (continued)

```
MAC Address: 68:05:CA:46:70:88 (Intel Corporate)
Nmap scan report for 192.168.86.11
Host is up (0.022s latency).
PORT STATE SERVICE
80/tcp closed http
443/tcp closed https
```

```
MAC Address: C8:DB:26:02:EE:CC (Logitech)
```

```
Nmap scan report for harmonyhub.lan (192.168.86.12)
Host is up (0.014s latency).
PORT STATE SERVICE
80/tcp closed http
443/tcp closed https
```

```
MAC Address: C8:DB:26:02:89:62 (Logitech)
```

```
Nmap scan report for myq-d9f.lan (192.168.86.20)
Host is up (0.026s latency).
PORT STATE SERVICE
80/tcp open http
443/tcp closed https
```

```
MAC Address: 64:52:99:54:7F:C5 (The Chamberlain Group)
```

Two things you may note in the output: First, we don't know what the application is. All we know is the protocol that is being used. Of course, we assume it’s a web server, but what one? Even if we knew what the operating system is, we can’t assume which application is being used as the web server. The second thing to notice is that along with the MAC address, you get the vendor. There is nothing special here. Nmap looks up the organizationally unique identifier (OUI) part of the MAC address from a database and presents the result of the lookup.

There are additional TCP scans that nmap can run. The other scans make use of unexpected input as a way of potentially getting different responses. For example, the following code listing is something referred to as an Xmas scan. The reason for that is that the packets being sent have the FIN, PSH, and URG flags set, which makes the packet look lit up like a Christmas (or Xmas) tree. What you will likely notice quickly is that we don’t get an indication about open ports here, as we did in the preceding code. Instead, nmap is telling us that the port is either open or filtered. The reason for this is that with ports that are closed, the system responds with a RST. Ports that are open don’t respond at all because this is not a legal packet from the perspective of the protocol. If nmap doesn’t get any response, it’s not clear whether it’s because a network device dropped the message or if the system just didn’t respond to an illegal message.
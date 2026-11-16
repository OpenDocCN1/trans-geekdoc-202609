
## SYN Scan with Nmap

```
$ nmap -sS 192.168.86.32
Starting Nmap 7.70 ( https://nmap.org ) at 2018-07-14 19:01 MDT
Nmap scan report for billthecat.lan (192.168.86.32)
Host is up (0.022s latency).
Not shown: 500 closed ports, 495 filtered ports
PORT   STATE SERVICE
22/tcp open  ssh
88/tcp open  kerberos-sec
445/tcp open  microsoft-ds
548/tcp open  afp
5900/tcp open vnc
MAC Address: AC:87:A3:36:D6:AA (Apple)

Nmap done: 1 IP address (1 host up) scanned in 3.69 seconds
```

In order to demonstrate the use of a network block as a target, we can make use of a full connect scan. Rather than a RST as the response to the SYN/ACK, nmap will complete the connection and then tear it down once the connection is complete. What you will see in the following code listing is the use of a CIDR block as the target address. This means nmap will scan the entire subnet. You will also notice that the ports are specified. Rather than just defaulting to the 1,000 ports nmap will usually scan, we’re only going to get hosts that have port 80 and 443 open. There could be many hosts on the network that won’t respond to a scan like this.

## Nmap Full Connect Scan

```
$ nmap -sT -p 80,443 192.168.86.0/24
Starting Nmap 7.70 ( https://nmap.org ) at 2018-07-14 20:44 MDT
RTTVAR has grown to over 2.3 seconds, decreasing to 2.0
Nmap scan report for testwifi.here (192.168.86.1)
Host is up (0.011s latency).

PORT   STATE SERVICE
80/tcp open  http
443/tcp closed https
MAC Address: 18:D6:C7:7D:F4:8A (Tp-link Technologies)

Nmap scan report for 192.168.86.2
Host is up (0.011s latency).

PORT   STATE SERVICE
80/tcp closed http
443/tcp closed https
MAC Address: 68:05:CA:46:70:88 (Intel Corporate)
Nmap scan report for 192.168.86.11
Host is up (0.022s latency).
PORT STATE SERVICE
80/tcp closed http
443/tcp closed https
MAC Address: C8:DB:26:02:EE:CC (Logitech)
Nmap scan report for harmonyhub.lan (192.168.86.12)
Host is up (0.014s latency).
PORT STATE SERVICE
80/tcp closed http
443/tcp closed https
MAC Address: C8:DB:26:02:89:62 (Logitech)
Nmap scan report for myq-d9f.lan (192.168.86.20)
Host is up (0.026s latency).
PORT STATE SERVICE
80/tcp open http
443/tcp closed https
MAC Address: 64:52:99:54:7F:C5 (The Chamberlain Group)
```

Two things you may note in the output: First, we don't know what the application is. All we know is the protocol that is being used. Of course, we assume it’s a web server, but what one? Even if we knew what the operating system is, we can’t assume which application is being used as the web server. The second thing to notice is that along with the MAC address, you get the vendor. There is nothing special here. Nmap looks up the organizationally unique identifier (OUI) part of the MAC address from a database and presents the result of the lookup.

There are additional TCP scans that nmap can run. The other scans make use of unexpected input as a way of potentially getting different responses. For example, the following code listing is something referred to as an Xmas scan. The reason for that is that the packets being sent have the FIN, PSH, and URG flags set, which makes the packet look lit up like a Christmas (or Xmas) tree. What you will likely notice quickly is that we don’t get an indication about open ports here, as we did in the preceding code. Instead, nmap is telling us that the port is either open or filtered. The reason for this is that with ports that are closed, the system responds with a RST. Ports that are open don’t respond at all because this is not a legal packet from the perspective of the protocol. If nmap doesn’t get any response, it’s not clear whether it’s because a network device dropped the message or if the system just didn’t respond to an illegal message.

## Running an XMAS Scan with Nmap

```
$ nmap -sX 192.168.86.32
Starting Nmap 7.70 ( https://nmap.org ) at 2018-07-14 20:58 MDT
Nmap scan report for billthecat.lan (192.168.86.32)
Host is up (0.0076s latency).
Not shown: 995 closed ports
PORT STATE SERVICE
22/tcp open|filtered ssh
88/tcp open|filtered kerberos-sec
445/tcp open|filtered microsoft-ds
548/tcp open|filtered afp
5900/tcp open|filtered vnc
MAC Address: AC:87:A3:36:D6:AA (Apple)
Nmap done: 1 IP address (1 host up) scanned in 13.13 seconds
```

The same ports show up here as the SYN scan earlier. The only difference is that nmap can't specifically determine whether the port is open or filtered. Other scans, such as the Null scan where no flags are set, will also show results as being open or filtered for the same reason. The FIN scan also uses an unexpected set of flags since the FIN flag should only be sent in cases where there is an established connection. You will also get open or filtered from the FIN scan.

## UDP Scanning

UDP scanning is much more straightforward than TCP scanning. There are no options for UDP scanning. Nmap sends out UDP messages and then watches whatever responses may come back. The expectation is that if a port is closed, the system will respond with an ICMP port unreachable message. If a port is open, the service may respond with something or it may just not respond at all. In the following code, you can see a UDP scan run with nmap. You'll notice on the command line that a new parameter has been added, -T 4. This sets the throttle rate. By default, the throttle is set at 3, which is a common rate of message transmission. If you want it faster, you can go up to 5. If you want it to go slower, potentially to avoid detection, you can turn it down to 1. Since this is on my local network and I don't care how fast it transmits, I have the throttle rate set for 4.

```
$ nmap -sU -T 4 192.168.86.32
Starting Nmap 7.70 ( https://nmap.org ) at 2018-07-15 08:03 MDT
Nmap scan report for billthecat.lan (192.168.86.32)
Host is up (0.0053s latency).
Not shown: 750 closed ports, 247 open|filtered ports
PORT STATE SERVICE
123/udp open ntp
137/udp open netbios-ns
5353/udp open zeroconf
MAC Address: AC:87:A3:36:D6:AA (Apple)
Nmap done: 1 IP address (1 host up) scanned in 5.21 seconds
```

Figure 5.2 will show you what these requests look like after capturing them in Wireshark, a packet capturing program. At the top of the list of packets are the probe requests from the system running nmap. If you look at the packet decode in the bottom pane, you will see there is no data in the packet. The UDP header is the 8 bytes expected for a UDP header and then there is no payload. The bottom of the list of packets shows the ICMP port unreachable messages from the target host.

### FIGURE 5.2 UDP scan from Wireshark

![](img/421171b17a0c0dfae0aacde15d9831c1_178_0.png)

You can compare the time that it takes to perform the different scans. The SYN scan took a bit over 3 seconds, while the UDP scan took just over 5 seconds. You'll also notice that there are about 1,000 ports scanned for UDP as well. We still have the problem, though, of not knowing for sure what applications are running behind these ports. This is also something nmap can take care of for us.

## Detailed Information

We can use nmap to address the problem of not knowing the application. We can use version scanning. What nmap does when we run a version scan (-sV) is connect to the port and, as necessary, issue the correct protocol commands to get the application banner back. The banner is protocol-specific and may include such information as the software name and version. In the following code listing, you can see not only the protocol, as you've seen before, but also the software being used and the version number. For port 22, the system is running OpenSSH version 7.4. The 2.0 in parentheses indicates it is version 2.0 of the protocol. This is something that the service indicates in the banner.

## Nmap Version Scan

```
$ nmap -sV 192.168.86.32
Starting Nmap 7.70 ( https://nmap.org ) at 2018-07-14 20:51 MDT
Nmap scan report for billthecat.lan (192.168.86.32)
Host is up (0.00083s latency).
Not shown: 995 closed ports
PORT STATE SERVICE VERSION
22/tcp open ssh OpenSSH 7.4 (protocol 2.0)
88/tcp open kerberos-sec Heimdal Kerberos (server time: 2018-07-15 02:51:39Z)
445/tcp open microsoft-ds?
548/tcp open afp Apple AFP (name: billthecat; protocol 3.4; OS X
10.9 - 10.11; Macmini7,1)
5900/tcp open vnc Apple remote desktop vnc
MAC Address: AC:87:A3:36:D6:AA (Apple)
Service Info: OSs: OS X, Mac OS X; CPE: cpe:/o:apple:mac_os_x:10.9,
cpe:/o:apple:mac_os_x

Service detection performed. Please report any incorrect results at
https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 35.23 seconds
```

Nmap knows the details about the services because the application provides the information when nmap connects. Different applications and protocols will provide different sets of information, which means nmap has to understand how to speak these protocols to get this information in some cases. As an example, with web servers such as Apache, the system administrator is in charge of how much should be provided in the headers going back to the client. Apache can provide not only the name of the product, Apache, but also the version of the software and the modules that are loaded as well as the versions of the modules.

You may also want to know what operating system is running on the remote system. This is also something nmap can take care of, with an operating system scan. In order to make a determination about the operating system, nmap has a database of fingerprints. The fingerprints contain details about how each operating system behaves, including how the IP identification field is generated, the initial sequence number, the initial window size, and several other details. In order to identify the operating system, nmap has to find at least one open port and one closed port.

In the following code you can see an operating system scan. You will notice that even though I didn’t indicate a TCP scan, nmap performed one. The same ports that were found

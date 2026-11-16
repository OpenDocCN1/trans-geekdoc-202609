
**13.** What information would you not expect to find in the response to a whois query about an IP address?
- A. IP address block
- B. Domain association
- C. Address block owner
- D. Technical contact

**14.** What would you be looking for with the following Google query?
filetype:txt Administrator:500:
- A. Text files owned by Administrator
- B. Administrator login from file
- C. Text files including the text Administrator:500:
- D. 500 administrator files with text

**15.** What command would you use to get the list of mail servers for a domain?
- A. whois mx zone=domain.com
- B. netstat zone=domain.com mx
- C. dig domain.com @mx
- D. dig mx domain.com

**16.** What would you get from running the command dig ns domain.com?
- A. Mail exchanger records for domain.com
- B. Name server records for domain.com
- C. Caching name server for domain.com
- D. IP address for the hostname ns

**17.** If you wanted to locate detailed information about a person using either their name or a username you have, which website would you use?
- A. peekyou.com
- B. twitter.com
- C. intelius.com
- D. facebook.com

**18.** If you were looking for detailed financial information on a target company, with what resource would you have the most success?
- A. LinkedIn
- B. Facebook
- C. EDGAR
- D. MORTIMER

**19.** What financial filing is required for public companies and would provide you with the annual report?
- A. 10-Q
- B. 11-K
- C. 401(k)
- D. 14-A

**20.** If you were looking up information about a company in New Zealand, which RIR would you be looking in for data?
- A. AfriNIC
- B. RIPE
- C. APNIC
- D. LACNIC

## Chapter 5

## Scanning Networks

THE FOLLOWING CEH EXAM TOPICS ARE COVERED IN THIS CHAPTER:

- Communication on protocols
- Technical assessment methods
- Vulnerabilities
- Vulnerability scanners
- Network security
- Port scanning
- Security testing methodology

![](img/421171b17a0c0dfae0aacde15d9831c1_168_0.png)

With all the reconnaissance and information gathering behind us, we can start moving into interacting with the systems in the target and its networks. This stage requires the data gathered from the reconnaissance and footprinting steps. Without that, you will have no idea what to scan. Of course, if you are working hand in glove, as it were, with the customer, they may have provided you with a lot of the details you would normally have gotten with reconnaissance techniques. Either way is okay, as long as you are clear up front on what the scope and scale of the engagement is and, once you start directly interacting with systems, you don't move beyond what was agreed to with your target.

### Ethics Note

Just a reminder, especially as we start moving into touching systems, you must get permission. Even though we're just talking about scanning and not performing exploits, it's entirely possible for a scan to knock over a system. On really fragile systems, such as older embedded devices, a simple port scan can cause the device to fail. Ensure that you have permission from your target/client and that they have an understanding of what may happen once you get started. Expect the unexpected and inform your client/employer.

A common step to move to when first interacting with target systems is to perform a port scan. A port scan identifies open ports on systems connected to the target network. A port scan isn't done just for the purpose of doing a port scan. A port scan is a starting point for identifying services and applications that are listening on those ports. Keep in mind that the objective is always to identify issues on your target network so your client/employer can improve their security posture. Identifying applications can help us identify vulnerabilities that need to be addressed.

Just identifying services and applications may not provide you with a lot of information, and what information it does provide can create a lot of work for you. Knowing the application name and even the version means you need to start digging into potential vulnerabilities that may exist with that application and service. This is why we use vulnerability scanners. The vulnerability scanner can help save time during that process. You shouldn't assume, though, that the vulnerability scanner is infallible. Vulnerability scanners can make mistakes—on both ends of the spectrum, meaning it can miss vulnerabilities as well as report ones that really don't exist. The knowledge and skill of an ethical hacker is important here—knowing how to verify and knowing what is real and what isn't.

Firewalls can be a real nuisance, as can intrusion detection (or protection) systems for that matter, if you are doing a true red-team test where the operations team doesn't know what you are doing and you don't want them to know. This means that these technologies can inhibit or deter attempts to reach into the network to gather information that you can use later. Ports may be open on systems but closed in the firewall. This limits your ability to get to those applications. Your scan attempts may be detected, alerting security and operations staff about what you are doing, which may mean you just get barred altogether. Depending on the rules of the engagement, you may not want to be detected. This means there may be evasion techniques that need to be employed to make sure you can keep going and don't get blocked.

One way to achieve that, and also to poke at some functionality to identify possible vulnerabilities, is to use packet crafting. Packet crafting means you bypass the operating system and its mechanisms for creating all the data structures in the right way for transmission over the network. The reason for doing this is to create those messages incorrectly. If they don't look right, they may get ignored by firewalls or detection systems. This may allow the message to get to the endpoint.

### Ping Sweeps

Rather than blindly throwing attacks at address spaces you've identified, you may want to identify systems that are responsive within those address spaces. Responsive means that when network messages are sent to them, they provide an appropriate response to the messages. This means you can identify systems that are alive before you start aiming attacks or probes at them. One way of determining systems that are alive is to perform a ping sweep. A ping sweep is when you send ping messages to every system on the network, thus the “sweep” part. The ping is an ICMP echo request, which is a common message to be sent. As long as you aren't pounding targets with an unusual number or size of these messages, they may not be noticed. Ping sweeps aren't guaranteed to succeed because there may be firewall rules that block ICMP messages from outside the network.

### Using fping

While there are many tools that can perform a ping sweep, one of the common ones is fping. This is a tool designed to send ICMP echo requests to multiple systems. In the following code listing, you can see the use of fping to sweep my local network. The parameters used with fping are aeg, which means fping shows hosts that are alive, show elapsed time, and generate a list of targets from an address block. You'll see the list of hosts that respond at the front of the list. After that, you start to see host unreachable messages, indicating that the host is down. fping will send multiple messages to systems before giving up and determining it's down. This output is truncated due to length, but without the a, the end of the list would be all of the hosts that were flagged as down. As it is, all we get is the indication that the systems were up.

### fping Output

```
$ fping -aeg 192.168.86.0/24
192.168.86.1 (10.3 ms)
192.168.86.2 (16.4 ms)
192.168.86.12 (27.7 ms)
192.168.86.21 (17.4 ms)
192.168.86.11 (173 ms)
192.168.86.20 (82.7 ms)
192.168.86.31 (0.04 ms)
192.168.86.30 (14.3 ms)
192.168.86.32 (16.4 ms)
192.168.86.35 (16.9 ms)
192.168.86.37 (21.7 ms)
192.168.86.38 (20.4 ms)
192.168.86.39 (22.2 ms)
192.168.86.22 (216 ms)
192.168.86.43 (15.6 ms)
192.168.86.44 (14.7 ms)
192.168.86.49 (0.37 ms)
192.168.86.50 (14.3 ms)
192.168.86.51 (18.8 ms)
192.168.86.52 (15.3 ms)
192.168.86.28 (294 ms)
192.168.86.58 (19.9 ms)
192.168.86.47 (375 ms)
192.168.86.53 (508 ms)
192.168.86.63 (404 ms)
192.168.86.160 (15.6 ms)
192.168.86.162 (25.7 ms)
192.168.86.170 (14.6 ms)
192.168.86.189 (18.9 ms)
192.168.86.196 (25.6 ms)
192.168.86.200 (32.7 ms)
192.168.86.205 (72.2 ms)
192.168.86.210 (18.3 ms)
192.168.86.245 (15.6 ms)
192.168.86.247 (23.4 ms)
192.168.86.250 (25.9 ms)
```

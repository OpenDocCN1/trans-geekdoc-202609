
A `network analyzer` allows you to look into a network and analyze data going across the wire for network optimization, security, and/or troubleshooting purposes. Like a microscope for a lab scientist, a network analyzer is a must-have tool for any security professional.

![technicalstuff](images/technicalstuff.png)Network analyzers are often generically referred to as `sniffers`, though that term is actually the name and trademark of a specific product: Network Associates’ original Sniffer network analysis tool.

A network analyzer is handy for sniffing packets on the wire. A network analyzer is software that runs on a computer with a network card. It works by placing the network card in `promiscuous mode`, which enables the card to see all the traffic on the network, even traffic that isn’t destined for the network analyzer’s host. The network analyzer performs the following functions:

* Captures all network traffic.

* Interprets or decodes what it finds into human-readable format.

* Displays the content in chronological order (or however you choose to see it).

When assessing security and responding to security incidents, a network analyzer can help you do the following:

* View anomalous network traffic and even track down an intruder.

* Develop a baseline of network activity and performance (such as protocols in use, use trends, and MAC addresses) before a security incident occurs.

![remember](images/remember.png)When your network behaves erratically, a network analyzer can help you track and isolate malicious network use, detect malicious Trojan-horse applications, and monitor and track down DoS attacks.

#### Network analyzer programs

You can use one of the following programs for network analysis:

* **Omnipeek** (`https://www.savvius.com`) is one of my favorite network analyzers. It does everything I need and more, and it’s very simple to use. Omnipeek is available for Windows operating systems.

* **CommView** (`https://www.tamos.com/products/commview`) is a great, low-cost, Windows-based alternative.

* **Cain & Abel** (`www.oxid.it/cain.html`) is a free multifunctional password-recovery tool for performing ARP poisoning, capturing packets, cracking passwords, and more.

* **Wireshark** (`http://wireshark.org`), formerly known as Ethereal, is a free alternative. I download and use this tool if I need a quick fix and don’t have my laptop nearby. It’s not as user-friendly as most of the commercial products, but it’s very powerful if you’re willing to master its ins and outs. Wireshark is available for Windows and macOS X.

* **ettercap** (`http://ettercap.github.io/ettercap`) is another powerful (and free) utility for performing network analysis and much more on Windows, Linux, and other operating systems.

![technicalstuff](images/technicalstuff.png)Here are a few caveats for using a network analyzer:

* To capture all traffic, you must connect the analyzer to one of the following: 

    * A hub on the network.

    * A monitor/span/mirror port on a switch.

    * A switch that you’ve performed an ARP poisoning attack on.

* If you want to see traffic similar to what a network-based IPS sees, you should connect the network analyzer to a hub or switch monitor port — or even a network tap — outside of the firewall, as shown in [Figure 9-7](#c09.xhtml#c09-fig-0007). This way, your testing enables you to view: 

    * What’s entering your network *before* the firewall filters eliminate the junk traffic.

    * What’s leaving your network *after* the traffic passes through the firewall.

![© John Wiley & Sons, Inc. ¶  FIGURE 9-7:  Connecting a network analyzer outside the firewall.](images/9781119485476-fg0907.png)

© John Wiley & Sons, Inc. ¶  [FIGURE 9-7:](#c09.xhtml#rc09-fig-0007)  Connecting a network analyzer outside the firewall.

Whether you connect your network analyzer inside or outside your firewall, you see immediate results. The amount of information returned can be overwhelming, but you can look for these issues first:

* **Odd traffic,** such as: 

    * An unusual amount of ICMP packets.

    * Excessive amounts of multicast or broadcast traffic.

    * Protocols that aren’t permitted by policy or shouldn’t exist, given your current network configuration.

* **Internet use habits,** which can help point out malicious behavior of a rogue insider or system that has been compromised, such as: 

    * Web surfing and social media

    * Email

    * Use of Tor

    * Instant messaging and other P2P software

* **Questionable usage,** such as: 

    * Many lost or oversize packets, indicating that hacking tools or malware are present.

    * High-bandwidth consumption that might point to a web or FTP server that doesn’t belong.

* **Reconnaissance probes and system profiling from port scanners and vulnerability assessment tools,** such as a significant amount of inbound traffic from unknown hosts — especially over ports that aren’t used much, such as FTP or Telnet.

* **Hacking in progress,** such as tons of inbound UDP or ICMP echo requests, SYN floods, or excessive broadcasts.

* **Nonstandard host names on your network.** If your systems are named Computer1, Computer2, and so on, a computer named GEEKz4evUR should raise a red flag.

* **Hidden servers** (especially web, SMTP, FTP, DNS, and DHCP) that might be eating network bandwidth, serving illegal software, or accessing your network hosts.

* **Attacks on specific applications** that show such commands as `/bin/rm`, `/bin/ls`, `echo`, and `cmd.exe`, as well as SQL queries and JavaScript injection, which I cover in [Chapter 15](#c15.xhtml).

    ![remember](images/remember.png)You may need to let your network analyzer run for quite a while — several hours to several days, depending on what you’re looking for. Before getting started, configure your network analyzer to capture and store the most relevant data:

* **If your network analyzer permits you to do so, configure it to use a first-in, first-out buffer.** This configuration overwrites the oldest data when the buffer fills, but it may be your only option if memory and hard drive space are limited on your network analysis computer.

* **If your network analyzer permits you to do so, record all the traffic into a capture file and save it to the hard drive.** This scenario is ideal, especially if you have a large hard drive (4TB or larger).

    ![warning](images/warning.png)You can easily fill several hundred gigabytes’ worth of hard drive space in a short period. I highly recommend running your network analyzer in what Omnipeek calls `monitor mode`. This mode allows the analyzer to keep track of what’s happening, such as network use and protocols, but not to capture and store every single packet. If you analyzer supports monitor mode, this tool is beneficial and often all you need.

* **When network traffic doesn’t look right in a network analyzer, it probably isn’t.** It’s better to be safe than sorry. Run a baseline when your network is working normally. When you have a baseline, you can see any obvious abnormalities when an attack occurs.

One thing I like to check for is `top talkers` (network hosts sending/receiving the most traffic) on the network. If someone is doing something malicious on the network, such as hosting an FTP server or running Internet file-sharing software, using a network analyzer may be the only way you’ll find out. A network analyzer is another good tool for detecting systems that are infected with malware, such as a virus or Trojan horse. [Figure 9-8](#c09.xhtml#c09-fig-0008) shows what it looks like to have a suspect protocol or application running on your network.

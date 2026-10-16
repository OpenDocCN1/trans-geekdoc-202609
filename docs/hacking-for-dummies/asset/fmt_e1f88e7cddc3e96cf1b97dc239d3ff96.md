
![ FIGURE 9-8:  Omnipeek can help uncover someone running an illicit system, such as an FTP server.](images/9781119485476-fg0908.png)

[FIGURE 9-8:](#c09.xhtml#rc09-fig-0008)  Omnipeek can help uncover someone running an illicit system, such as an FTP server.

Looking at your network statistics (such as bytes per second, network utilization, and inbound/outbound packet counts) is another good way to determine whether something fishy is going on. [Figure 9-9](#c09.xhtml#c09-fig-0009) displays network statistics viewed through the powerful CommView network analyzer.

![ FIGURE 9-9:  CommView’s interface for viewing network statistics](images/9781119485476-fg0909.png)

[FIGURE 9-9:](#c09.xhtml#rc09-fig-0009)  CommView’s interface for viewing network statistics

TamoSoft (the maker of CommView) has another product called NetResident ([`https://www.tamos.com/products/commview`](https://www.tamos.com/products/commview)) that can track the use of well-known protocols, such as HTTP, email, FTP, and Voice over Internet Protocol (VoIP). As shown in [Figure 9-10](#c09.xhtml#c09-fig-0010), you can use NetResident to monitor web sessions and play them back.

![ FIGURE 9-10:  NetResident can track Internet use and ensure that security policies are enforced.](images/9781119485476-fg0910.png)

[FIGURE 9-10:](#c09.xhtml#rc09-fig-0010)  NetResident can track Internet use and ensure that security policies are enforced.

NetResident also has the capability to perform ARP poisoning via its PromiSwitch tool (available on the Tools menu), which allows NetResident to see everything on the local network segment. I cover ARP poisoning in “[The MAC-daddy attack](#c09.xhtml#c09-sec-0029)” later in this chapter.

#### Countermeasures against network protocol vulnerabilities

A network analyzer can be used for good or evil. The good ensures that your security policies are being followed. The evil helps someone work against you. A few countermeasures can help minimize the risk someone from using an unauthorized network analyzer. Just keep in mind that there’s no way to prevent it completely.

![warning](images/warning.png)If an external attacker or malicious user can connect to your network (physically or wirelessly), he can capture packets on the network, even if you’re using an Ethernet switch.

#### PHYSICAL SECURITY

Ensure that adequate physical security is in place to prevent someone from plugging into your network by doing the following things:

*   **Keep the bad guys out of your server room and wiring closet.** Ensure that the web, Telnet, and Secure Shell (SSH) management interfaces on your Ethernet switches are especially secure to keep someone from changing the switch port configuration and seeing everything that goes across the wire.

*   **Make sure that unsupervised areas, such as an unoccupied lobby or training room, don’t have live network connections.**

For details on physical security, see [Chapter 7](#c07.xhtml).

#### NETWORK ANALYZER DETECTION

You can use some older utilities to determine whether someone is running an unauthorized network analyzer on your network:

*   **Sniffdet** ([`http://sniffdet.sourceforge.net`](http://sniffdet.sourceforge.net)) for Unix-based systems.

*   **PromiscDetect** ([`http://ntsecurity.nu/toolbox/promiscdetect`](http://ntsecurity.nu/toolbox/promiscdetect)) for Windows.

Certain IPSes can also detect whether a network analyzer is running on your network. These tools enable you to monitor the network for Ethernet cards that are running in promiscuous mode. You simply load the programs on your computer, and the programs alert you if they see promiscuous behaviors on the network (Sniffdet) or local system (PromiscDetect).

### The MAC-daddy attack

Attackers can use ARP (Address Resolution Protocol) running on your network to make their systems appear to be your system or another authorized host on your network.

#### ARP spoofing

An excessive number of ARP requests can be a sign of an *ARP spoofing* attack (also called *ARP poisoning*) on your network.

A client running a program such as dsniff ([`https://www.monkey.org/~dugsong/dsniff`](https://www.monkey.org/~dugsong/dsniff)) or Cain & Abel can change the ARP tables — the tables that store IP addresses to media access control (MAC) address mappings on network hosts. Changing the ARP tables causes the victim computers to think that they need to send traffic to the attacker’s computer rather than to the true destination computer when communicating on the network. ARP spoofing is used during man-in-the-middle attacks.

Spoofed ARP replies can be sent to a switch, which reverts the switch to broadcast mode and essentially turns it into a hub. When this attack occurs, the attacker can sniff every packet going through the switch and capture anything and everything from the network.

![remember](images/remember.png)This security vulnerability is inherent in the way that TCP/IP communications are handled.

Here’s a typical ARP spoofing attack involving a hacker’s computer (Hacky) and two legitimate network users’ computers (Joe and Bob):

1.  Hacky poisons the ARP caches of victims Joe and Bob by using a tool such as dsniff, ettercap, or netcat.

2.  Joe associates Hacky’s MAC address with Bob’s IP address.

3.  Bob associates Hacky’s MAC address with Joe’s IP address.

4.  Joe’s traffic and Bob’s traffic are sent to Hacky’s IP address first.

5.  Hacky’s network analyzer captures Joe’s and Bob’s traffic.

    ![remember](images/remember.png)If Hacky is configured to act like a router and forward packets, it forwards the traffic to its original destination. The original sender and receiver never know the difference!

#### Using Cain & Abel for ARP poisoning

You can perform ARP poisoning on your switched Ethernet network to test your IPS or to see how easy it is to turn a switch into a hub and capture anything with a network analyzer.

![warning](images/warning.png)ARP poisoning can be hazardous to your network’s hardware and health, causing downtime and worse. Be careful!

Follow these steps to use Cain & Abel for ARP poisoning:

1.  **Load Cain & Abel and then click the Sniffer tab to enter network analyzer mode.**

    The Hosts page opens by default.

2.  **Click the Start/Stop APR icon (the yellow-and-black circle).**

    The ARP poison routing (how Cain & Abel refers to ARP poisoning) process starts and enables the built-in sniffer.

3.  **If you’re prompted to do so, select the network adapter in the window that appears and then click OK.**

4.  **Click the blue plus-sign (+) icon to add hosts on which to perform ARP poisoning.**

5.  **In the MAC Address Scanner window that appears, ensure that the All Hosts in My Subnet option is selected, and click OK.**

6.  **Click the APR tab (the one with the yellow-and-black circle icon) to load the APR page.**

7.  **Click the white space below the top Status column heading (below the Sniffer tab).**

    This step reenables the blue + icon.

8.  **Click the blue + icon.**

    The New ARP Poison Routing window shows the hosts discovered in Step 4.

9.  **Select your default route (in this example, 10.11.12.1).**

    The right column fills with all the remaining hosts, as shown in [Figure 9-11](#c09.xhtml#c09-fig-0011).

10.  **Ctrl+click all the hosts in the right column that you want to poison.**

11.  **Click OK to start the ARP poisoning process.**

     This process can take anywhere from a few seconds to a few minutes, depending on your network hardware and each hosts’ local TCP/IP stack. [Figure 9-12](#c09.xhtml#c09-fig-0012) shows the result of ARP poisoning on my test network.

12.  **To use the built-in passwords feature to capture passwords traversing the network to and from various hosts, click the Passwords tab.**

![ FIGURE 9-11:  Selecting your victim hosts for ARP poisoning in Cain & Abel](images/9781119485476-fg0911.png)

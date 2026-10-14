
## Figure 4-32 Centralized Wireless Intrusion Detection System

![](img/073342643701cc54eb7875c41ab92ef2_226_0.png)

## Test Your Understanding

- 21. a. What is the purpose of a wireless IDS?
- b. How do wireless IDSs get their data?
- c. What is a rogue access point?
- d. What are the two alternatives to using a centralized wireless IDS?
- e. Why are they not attractive?

## False 802.11 Security Measures

Many magazine articles about 802.11 security give advice that is now widely seen as offering only a false sense of security. They are what my grandfather called whiskey cures. He said that of all the things that fail to cure the common cold, whiskey is the most popular.

The actions deprecated in this section for corporate use may be enough to keep out nosy neighbors. However, drive-by hackers with good hacking software increasingly roam neighborhoods to get free Internet access and look through residential computers. In addition, these poor “protections” take as much effort or more to set up a full WPA or 802.11i security.

## SPREAD SPECTRUM OPERATION AND SECURITY

All 802.11 wireless LAN standards use spread spectrum transmission, which spreads the signal over a wide range of frequencies. Many people have heard that the military uses spread spectrum transmission for security. However, the types of spread spectrum transmission used in 802.11 offer no security; in fact, spread spectrum modes of operation for 802.11 WLANs specifically make it easy for stations to find and hear one another.14 Users should not dismiss hackers because “My system uses spread spectrum transmission, which can’t be intercepted.”

14 Spread spectrum transmission is mandated by law for the 2.4-GHz and 5-GHz unlicensed radio bands in which 802.11 operates in order to reduce propagation problems. Many propagation difficulties are frequency-dependent, and using a broad spectrum of frequencies reduces the damage of frequency-specific problems. Again, spread spectrum is not mandated for security.

## TURNING OFF SSID BROADCASTING

To work with an access point, a station must know the access point’s Service set identifier (SSID). To make it easy for stations to find access points, access points broadcast their SSIDs frequently. Turning off SSID broadcasting would seem to offer security.

However, even if SSID broadcasting is turned off, the SSID will still be transmitted in the clear in the header of each transmitted frame. Sniffer programs have no trouble reading SSIDs in frame headers. Quite simply, there is nothing a firm can do to hide SSIDs from an attacker who has even minimum hacking software.

## MAC ACCESS CONTROL LISTS

Each network interface card has a unique MAC address (e.g., 00-1C-23-0E-1D-41). It is possible to configure most access points to serve only stations on a preapproved list of MAC addresses. The wireless access point ignores other stations. However, MAC addresses must be transmitted in the clear in every frame, so drive-by hackers can easily learn them.

Attackers can easily change their MAC addresses and send frames that appear to come from one of the approved stations. Managing MAC access control lists is a good deal of work and provides no effective security.

## Implementing 802.11i or WPA Is Easier

Turning off SSID broadcasting and creating MAC access control lists are not just ineffective. They are time-consuming. Turning on 802.11i or WPA not only gives full security (aside from evil twin access points). It is also less work.

- **Spread Spectrum Operation and Security**
- - Signal is spread over a wide range of frequencies
- - Not done for security, as in military spread spectrum transmission

- **Turning off SSID Broadcasting**
- - Service set identifier (SSID) is an identifier for an access point
- - Users must know the SSID to use the access point
- - Drive-by hacker needs to know the SSID to break in
- - Access points frequently broadcast their SSIDs
- - Some writers favor turning off of this broadcasting
- - But turning off SSID broadcasting can make access more difficult for ordinary users
- - Will not deter the attacker because he or she can read the SSID, which is transmitted in the clear in each transmitted frame

- **MAC Access Control Lists**
- - Access points can be configured with MAC access control lists
- - Only permit access by stations with NICs having MAC addresses on the list
- - But MAC addresses are sent in the clear in frames, so attackers can learn them
- - Attacker can then spoof one of these addresses

- **Perspective**
- - These “false” methods, however, may be sufficient to keep out nosy neighbors
- - But drive-by hackers hit even residential users
- - Simply applying WPA or 802.11i provides much stronger security and is easier to do

## Test Your Understanding

- 22. a. Does the use of spread spectrum transmission in 802.11 create security?
- b. What are SSIDs?
- c. Does turning off SSID broadcasting offer real security? Explain.
- d. What are MAC access control lists?
- e. Do they offer real security? Explain.

## 4.7 Conclusion

This chapter began with a discussion about the four broad goals to consider when creating a secure networking environment. These goals include availability, confidentiality, functionality, and access control. We looked at some of the difficulties network administrators face when trying to secure networks.

The next section focused on denial-of-service (DoS) attacks. While companies may experience a loss of service, it may not be a DoS attack. It may be the result of faulty coding, or simply a dramatic increase in legitimate network traffic. Intentional DoS attacks are focused on stopping critical services or slowly degrading them over time.

The main DoS attack methods we looked at were (1) direct/indirect, (2) intermediary, (3) reflected, and (4) sending malformed packets. Defenses against DoS attacks include black holing, validating the TCP handshake, and limiting the rate of incoming packets.

The next type of network attack we looked at was ARP poisoning. More specifically, we looked at how ARP poisoning could be used to reroute traffic for a man-in-the-middle attack, or stop traffic altogether in an ARP DoS attack. It is important to remember that ARP poisoning required an attacker to have access to a computer on the local network. Rerouting traffic using ARP poisoning is an attack on both the functionality and confidentiality of a network.

We next looked at security for wired LANs, which almost always use Ethernet technology from the 802.3 Working Group. Another working group, 802.1, developed the 802.1X standard to prevent intruders from simply plugging laptops into wall jacks to get access to the network.

In 802.1X mode, there are three devices. The client or server PC connecting to the network is the supplicant. A central authentication server does credential checking. This central authentication server is usually governed by the RADIUS standard. The Ethernet workgroup switch to which the client or server PC connects is called the authenticator. Until the PC is authenticated, the port to which it connects is unauthorized and will only pass authentication information.

Authentication interactions are governed by the Extensible Authentication Protocol (EAP). We looked at the EAP interactions required for a computer connected to a workgroup switch port to authenticate itself. For most interactions, the workgroup switch authenticator merely passes EAP interactions between the connected computer and the central authentication server. Consequently, when new authentication methods are added, the authenticator does not have to be changed at all.

The next section focused on wireless attacks. The three types of wireless network attacks we looked at were (1) unauthorized network access, (2) a man-in-the-middle attack using an evil twin, and (3) wireless denial-of-service attacks.

Even if a firm implements a core security protocol, like WPA, security problems remain. The best way to handle the evil twin access point threat is to establish a VPN between the wireless client and the server it ultimately wishes to work with. This VPN

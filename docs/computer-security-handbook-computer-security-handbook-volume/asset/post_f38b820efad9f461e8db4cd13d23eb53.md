
The need for segmentation of wireless traffic is due to the inherent lack of physical controls for 802.11 traffic and range of accessibility. An external attack at a DMZ or other Internet-accessible device could lead to the compromise of DMZ assets, but controls typically exist in the form of multileg or sandwich-style firewall environments which limit the exposure from the DMZ network and prevent direct LAN connectivity. This type of segmentation should be applied to the wireless environment for similar reasons, albeit different attack vectors.

## 33.7.2.3 VPN over Wireless.

Depending on the purpose of the wireless network, users may require the same access on the wireless network that is afforded on the wired LAN. In favor of exposing the wireless network to the complete wired LAN a VPN solution may be used. This architecture would allow wireless network access to the Internet, just the VPN gateway, or other basic internal assets (such as an intranet site), which force the use of a VPN gateway for any other resources.

An additional strength provided by a VPN on top of wireless authentication is defense in depth. To gain internal LAN access from a wireless network, an attacker must compromise and gain access to the VPN in addition to any layer 2 wireless authentication/access control mechanisms. An attacker who gains access to the wireless medium would likely never suspect the use of a VPN and assume the state of limited internal access or mistake the current state for the complete LAN.

An assessment should be performed to understand the business case where wireless assets need complete access to the corporate LAN, and explicitly allow access on an IP/port basis. Fine-grained segmentation can be obtained by leveraging SSID-based VLAN assignments, explained in detail in the following sections, to assign restrictions on a per-VLAN basis with supporting ACLs at higher points within the network.

## 33.7.2.4 Inter-Wireless Network Segmentation.

Inter-wireless segmentation enables different user types to connect to different SSIDs provided by the same physical AP and be afforded different network-based access privileges. The process of segmenting each SSID into its own network usually involves VLAN tagging at the AP level to distinguish layer-2 traffic by forcing inter-VLAN communication to flow over a firewall or upstream router with VLAN/IP-based ACLs. Backend directory systems such as LDAP can be leveraged by modern APs to provide a decision on the VLAN assignment a particular user will receive—regardless of the SSID on which they currently reside. Dynamic backend directory-based systems are not completely secure due to the reliance on MAC addresses as a unique identifying agent.

This type of segmentation can be enforced at the network layer, through aforementioned VLAN firewalling, or through VPN access lists if employee wireless access is forced through a VPN tunnel to communicate with LAN assets.

## 33.7.2.5 Benefits and Drawbacks of SSID/VLAN-Based Segmentation.

Benefits of SSID/VLAN-based segmentation include:
- Differential treatment for wireless users by group or SSID; for example,
- An SSID of “corporate-sales” and “corporate-hr” may provide varying levels of access. It would be best practice to disguise and cloak the SSID names to obfuscate their purpose to an outsider.
- Ease of network administration by removing the need to assign VLANs on a per-port basis. SSID-based VLAN assignment only requires endpoint configuration to ensure the endpoint provides the credentials necessary to authenticate to a particular SSID.

A drawback of SSID-/VLAN-based segmentation is increased wireless-network overhead and reduced performance due to multiple SSID memory requirements.

## Summary of Wireless Segmentation Controls

- LAN segmentation: protects internal LAN in the event of wireless compromise through VLAN and wireless IP–based firewall ACLs.
- VPNs can be used over a wireless medium to allow users to access LAN assets.
- Intra-wireless network segmentation:
- SSID based: The use of separate SSIDs for different business cases can easily be mapped to a VLAN and provide varying levels of segmentation.
- Group based: RADIUS-based VLAN assignment for wireless user's current group privileges.

## 33.7.3 User Segmentation.

A RADIUS server can make advanced authorization decisions for a valid username/password match. Leveraging designated user groups in the authorization process can provide fine-grained control over which users are able to use a wireless network segmented in large sweeps. If it’s known that domain admins, power users, or general service accounts should never be able to authenticate over a wireless connection, they can be implicitly denied through nonmembership in a wireless-users group. Any user group that requires the ability to authenticate over wireless should be a member of this group.

A default RSN implementation that can and will authorize any user within the provided directory can become a victim of attacks on default, inactive, guest, or test accounts within the designated directory. Test accounts may be vulnerable to weak canonical passwords (e.g., “test” or “password”) due to their creation during early stages of software or directory development or through other means that bypass corporate password policy. When a username/password authentication mechanism is in play, an attacker may attempt basic brute-force attacks to gain access to the network through standard test or guest accounts. Many organizations don’t feel this is a serious problem, but when a directory contains thousands of accounts, and organizations don’t audit on a regular basis, it’s easy for things to slip through the cracks.

The use of a designated wireless group:
- Decreases the surface area of an attack, even if an adversary is able to obtain a list of user accounts and leverage them to brute force a wireless network through the use of basic passwords.
- Decreases the number of endpoints with saved or remembered network profiles that can be attacked and used to capture username/password challenge hashes in a hotspot or RADIUS impersonation-style attack.

## 33.8 SECURITY AUDITING TOOLS.41

This section looks at the open source and commercial tools available to help audit a wireless environment and to understand the tools that war drivers have to attack a network. Exhibit 33.11 lists the main programs available, including older software still mentioned in discussions, and the platforms they run (or ran) under.

## Exhibit 33.11 802.11 Security-Auditing Software

| Tool | Description and Home Page | Operating System |
|---|---|---|
| Aircrack | A program that breaks WEP encryption, injects packets (Aireplay), and performs a dictionary attack against WPA PSK. http://www.aircrack-ng.org | Linux Windows |
| Auditor | An obsolete security collection that had all the required drivers and security tools to audit or hack wireless networks. Replaced by BackTrack (see below). | Linux |
| AirMagnet | A commercial wireless LAN analyzer that runs on laptop PCs and pocket PCs. http://www.flukenetworks.com/enterprise-network/wlan-security-and-analysis | Windows Pocket PC |
| Airsnort | Outdated tool. Broke WEP encryption using the RC4 Key Scheduling Vulnerability and Korek optimizations. Last update was 2005. http://sourceforge.net/projects/airsnort/ | Linux |
| Airopeek NX | A commercial wireless LAN analyzer that ran on laptop and tablet PCs. Replaced by OmniPeek (see below). | Windows |
| BackTrack | A Linux security distribution and is the result of the merging of the Whax and Auditor security collections. http://www.backtrack-linux.org/ http://www.remote-exploit.org/articles/backtrack/index.html | Linux |
| CoWPAtty | A WPA PSK cracker last updated in 2008. http://www.willhackforsushi.com/Cowpatty.html | Linux |
| Ethereal | A program that understood the format of packets and dumps out their contents. Could capture packets as well as process a log file created by other programs. Replaced by Wireshark (see below) in 2006 when original programmer hired by a new company. | Linux Windows |
| Kismet | Wireless auditing tool still being actively developed and improved. Latest updates at time of writing were on 2012-12-06. http://www.kismetwireless.net/ | Linux, FreeBSD, NetBSD, OpenBSD, Mac OS X |
| Linux-wlan | The Linux drivers for Intersil Prism 2, 2.5, and 3-based cards used by open source software such as Kismet and Wellenreiter. Last updated 2004. http://www.linux-wlan.com/linux-wlan/ | GNU/Linux |
| Sniffer Global Analyzer | High-end software for use with portable (hardware) analyzer tools. http://www.netscout.com/products/enterprise/Pages/default.aspx | Hardware modules & client software |
| Netstumbler | Detects broadcasting 802.11 networks. Netstumbler is not suitable as a network auditing tool because access points can be configured to avoid detection. Last update (v0.4.0) was in 2004. http://stumbler.net/ | Windows |

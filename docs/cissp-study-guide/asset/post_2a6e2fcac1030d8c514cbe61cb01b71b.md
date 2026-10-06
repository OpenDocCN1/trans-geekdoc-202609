
# OSPF

Open Shortest First (OSPF) is an open link state routing protocol. OSPF routers learn the entire network topology for their “area” (the portion of the network maintain routes for, usually the entire network for small networks). OSPF routers send event-driven updates. If a network is converged for a week, the OSPF routers will send no updates. OSPF has far faster convergence than distance vector protocols as RIP. In Fig. 5.21, OSPF would choose the two-hop T3 route from Office A to B, over the single-hop T1 route.

> Note
> The example strongly prefers over proprietary standards, which is why proprietary routing protocols like Cisco’s EIGRP are not discussed here.

# BGP

BGP is the Border Gateway Protocol, the routing protocol used on the Internet. BGP routes between autonomous systems, which are networks with multiple Internet connections. BGP has some distance vector properties but is formally considered a path routing protocol.

# Modem

A Modem is a Modulator/Demodulator. It takes binary data and modulates it into analog sound that can be carried on phone networks designed to carry the human voice. The receiving modem demodulates the analog sound back into binary data. Modems are asynchronous devices: they do not operate with a clock signal.

# DTE/CEU and DSU

A DTE (Data Terminal Equipment) is a network “terminal,” meaning any type of network-connected user machine, such as a desktop, server, or actual terminal. A DCE (Data Circuit-Terminating Equipment, or called Data Communications Equipment) is a device that connects DTEs, such as a router. The most common use of these terms is DTE/DCE, and the meaning of each is more specific: the DCE marks the end of an ISP’s network. It connects to Terminal Equipment (DTE), which is the responsibility of the customer. The point where the DCE meets the DTE is called the demarc: the demarcation point, where the ISP’s responsibility ends and the customer’s begins.

The circuit carried via DCE/DTE is synchronous (it uses a clock signal). Both sides must synchronize to a clock signal, provided by the DCE. The DTE device is a modem or a CSU/DSU (Channel Service Unit/Data Service Unit).

# Operation of Hardware

Operation of hardware involves day-to-day operational issues such as redundant power, maintaining proper warranties, and support contracts.

# Secure Communications 279

# Redundant Power

Critical equipment such as routers and firewalls should be equipped with redundant power supplies. Each power supply should be connected to different electrical outlets that are also on different electrical circuits. Surge protectors and UPSs should be used, and generator backup should be available for critical devices. We will discuss surge protectors, UPSs, and generators in Chapter 8, Domain 7: Security Operations.

# Warranty and Support

All devices should be covered under active vendor warranty and have proper support contracts. Support contracts are often priced based on response time and other variables (faster response costs than slower). Cisco SmartNet offers levels of coverage:

- 24 × 7: 2-hour response, 24 hours a day, 7 days per week, including holidays
- 24 × 7: 4-hour response, 24 hours a day, 7 days per week, including holidays
- 8 × 5: 4-hour response, local business hours based on depot time, 5 days a week, no holidays
- 8 × 7 Next Calendar Day: Next-calendar-delivery, local business hours based on depot time, 7 days a week, including holidays
- 8 × 5 Next Business Day: Next-business-delivery, local business hours based on depot time, 5 days a week, no holidays [17]

Note that Cisco SmartNet itself is not testable; the example above was used because these types of tiered levels are common throughout the industry. There is no "right answer" for which level of support to choose: the desired response time may be determined after a risk assessment. Business Continuity Planning metrics such as Maximum Allowed Downtime (MAD, discussed in Chapter 8, Domain 7: Security Operations) can determine which level to purchase. Critical devices should be retired before reaching End-of-Support (EoS), as discussed in Chapter 3, Asset Security). Note that organizations may choose to self-ins for less critical devices including commodity PCs, but a thorough risk assessment must be conducted before self-insuring.

# Secure Communications

Protecting data in motion is one of the most complex challenges we face. The Internet provides global communication—with little or no built-in confidentiality, integrity, or availability. To secure our data, we must do it ourselves; secure communications describes ways to accomplish that goal.

# Authentication Protocols and Frameworks

An authentication protocol authenticates an identity claim over the network. Good security design ensures that a network eavesdropper may sniff all packets between the client and authentication server: the protocol should remain secure. As we see shortly, PAP fails this test, but CHAP and EAP pass.

# PAP and CHAP

PAP (Password Authentication Protocol) is a very weak authentication protocol. It sends the username and password in cleartext. An attacker who is able to sniff the authentication process can launch a simple replay attack, byplaying the username and password, using them to log in. PAP is insecure and should not be used.

CHAP (Challenge-Handshake Authentication Protocol) is a more secure authentication protocol that does not expose the cleartext password and is not susceptible to replay attacks. CHAP relies on a shared secret: the password is securely created (as during account enrollment) and stored on the CHAP server. Since both the user and the CHAP share a secret (the plaintext password), they can use that secret to securely communicate.

To authenticate, the client first creates an initial (unauthenticated) connection via LCP (Link Control Protocol). The server then begins the three-way CHAP authentication process:

- Server sends a challenge, which is a small random string (also called a nonce).
- The user takes the challenge string and the password, uses a hash cipher as MD5 to create a hash value, and sends that value back to the CHAP server as the response.
- The CHAP server hashes the password and challenge, creating the expected response. It compares the expected response with the response received from the user.

If the responses are identical, the user must have entered the appropriate password, and is authenticated. If they are different, the user entered the wrong password, and access is denied.

The CHAP server may re-authenticate by sending a new (and different) challenge. The challenges must be different each time; otherwise, an attacker could authenticate by replaying an older encrypted response.

A drawback of CHAP is that the server stores plaintext passwords of all client. An attacker who compromises a CHAP server may be able to steal the passwords stored on it.

# 802.1X and EAP

802.1X is "Port Based Network Access Control," and includes EAP (Extensible Authentication Protocol). EAP is an authentication framework that describes many specific authentication protocols. EAP is designed to provide authentication at Layer 2 (it is "port based", like ports on a switch), before a node receives an IP address. It is available for both wired and wireless, but is more commonly deployed on WLANs.

The 802.1X roles are:

- Supplicant: An 802.1X client
- Authentication Server (AS): a server that authenticates a supplicant
- Authenticator: a device such as an access point that allows a supplicant to authenticate and connect

# Exam Warning

Do not confuse 802.1X (EAP) with 802.11 (Wireless).

EAP addresses many issues, including the “roaming infected laptop” problem. A user with an infected laptop plugs into a typical office network and requests an IP address from a DHCP server. Once you get an IP, the malware installed on the laptop begins attacking other systems on the network.

By the time it is late to request an IP address, it is already in a position to cause harm on the network. This problem is most acute on WLANs (where an outside laptop 100 feet away from a building may be able to access the network). Ideally, authentication should be required before the laptop can join the network: EAP does exactly this.

Fig.3.2 shows Step 1 shows the Supplicant authenticating via EAPOL, Layer 2 EAP implementation. Step 2 shows the Authenticator receiving the EAPOL (EAP Over LAN) traffic and using RADIUS or Diameter to carry EAP traffic to the Authentication Server (AS). Step 3 shows the Authenticator allowing Supplicant access to the internal network after successful authentication.

There are many types of EAP, we will focus on EAP-MD5, EAP-FAST, EAP-TLS, EAP-TTLS, and PEAP:

- EAP-MD5 is one of the weakest forms of EAP. It offers client-server authentication (all other forms of EAP discussed in this section support mutual authentication of client and server); this makes it vulnerable to man-the-middle attacks. EAP-MD5 is also vulnerable to password cracking attacks.
- LEAP (Lightweight Extensible Authentication Protocol) is a Cisco-proprietary protocol released before 802.1X was finalized. LEAP has significant security flaws and should not be used.
- EAP-FAST (EAP-Flexible Authentication via Secure Tunneling) was designed by Cisco to replace LEAP. It uses a Protected Access Credential (PAC), which acts as a pre-shared key.

![](img/0bbd5f5bd171414c5e2c49247aab35d6_56_0.png)

FIG. 5.23 Successful 802.1X authentication.

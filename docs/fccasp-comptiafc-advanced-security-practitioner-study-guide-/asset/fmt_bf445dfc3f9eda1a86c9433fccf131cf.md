
# Network Authentication Methods

Network authentication is a key area of knowledge for the security professional, because it serves as the first line of defense. It consists of two pieces: identification and authentication. As an example, think of identification as me saying, “Hi, I am Michael.” It's great that I have provided you with that information, but how do you know that it is me? What you need is to determine the veracity of the claim. That's the role of authentication. Authentication types include `something you know`, `something you are`, and `something you have`. Three common network authentication methods are as follows:

*   **Password Authentication Protocol (PAP)** is an older authentication system designed to be used on phone lines and with dial-up systems. PAP uses a two-way handshake to authenticate but is considered weak because it transmits passwords in clear text. You should not use PAP. CHAP and EAP are seen as its replacements.
*   **Challenge Handshake Authentication Protocol (CHAP)** provides authentication by verifying through use of a three-way handshake. Once the client is authenticated, it is periodically requested to reauthenticate to the connected party through the use of a new challenge message. We will talk more about CHAP later in the chapter.
*   **Extensible Authentication Protocol (EAP)** is an authentication framework that is used in wireless networks. EAP defines message formats and then leaves it up to the protocol to define a way to encapsulate EAP messages within that protocol's message. There are many different EAP formats in use, including `EAP-TLS`, `EAP-PSK`, and `EAP-MD5`. Two common implementations of EAP are `PEAP` and `LEAP`.

# 802.1x

IEEE `802.1x` is an IEEE standard for port-based Network Access Control (NAC). `802.1x` is widely used in wireless environments and relies on EAP. `802.1x` acts as an application proxy. It's much like a middleman in the authentication process.

# Mesh Networks

There are many different network designs, such as bus, ring, star, and even mesh. An example of a mesh network is the Internet. It is a network of networks, one in which there are many paths the data can traverse to a given destination. The mesh network design is configured so that each node can forward data. One of the big advantages of a mesh network is its ability to self-heal. This simply means that if one node goes down, there are others to take its place. A mesh network is very reliable because there are multiple paths to the destination. Cellular networks are a good example of a mesh network.

Cellular networks are based on the mobile ad hoc network (MANET) design. With the proliferation of smartphones and tablets, MANETs have become one of the fastest-growing mesh network types. This is of particular concern to security professionals, since the lack of central points and the dynamic topology make the infrastructure prone to attack. Such attacks can include eavesdropping, jamming, interference, traffic analysis, data corruption, or even malware such as viruses and worms.

# Remote Access

Remote access is all about giving users outside the network access to company resources and data. Outside users are typically not physically connected to company resources and may be using their own hardware. A connection must be established by other means such as dial-in, wireless connection, through an Internet service provider (ISP), or over the Internet at a public hotspot. Remote access is an important topic in that potential attackers are constantly searching for ways to get access and in some cases have employed clever ways to do so.

In the world of Microsoft, the component designed for remote access is Remote Access Services (RAS). RAS is designed to facilitate the management of remote access connections through dial-up modems. Unix systems also have built-in methods to enable remote access. Historically, these systems worked well with Remote Authentication Dial-In User Service (RADIUS), a protocol developed to be a centralized sign-on solution that could support authentication, authorization, and accountability. This method of remote access has been around for a while, and there are some that are more modern.

Cisco has implemented a variety of remote access methods through its networking hardware and software. Originally, this was Terminal Access Controller Access Control System (TACACS). TACACS has been enhanced by Cisco and expanded twice. The original version of TACACS provided a combination process of authentication and authorization. This was extended to Extended Terminal Access Controller Access Control System (XTACACS). XTACACS is proprietary to Cisco and provides separate authentication, authorization, and accounting processes. The most current version is TACACS+. It has added functionality and has extended attribute control and accounting processes. TACACS+ also separates the authentication and authorization process into three separate areas.

Another standard is DIAMETER. The name is a pun in that the diameter is twice the radius. DIAMETER was designated by the Internet Engineering Task Force (IETF) to replace the RADIUS protocol. Although both operate in a similar manner, DIAMETER improves on RADIUS by resolving discovered weaknesses. DIAMETER improvements over RADIUS include improved failover. DIAMETER has the ability to support grouped attribute-value pairs (AVPs) and to forward requests to another agent should that designated agent fail.

One of the most common ways to authenticate across a point-to-point link using PPP is Challenge Handshake Authentication Protocol (CHAP). CHAP is designed to provide authentication periodically through the use of a challenge and response system. The CHAP process is shown in [Figure 2.1](#c02.xhtml#c02-fig-0001).

![FIGURE 2.1 CHAP authentication](images/c02f001.jpg)

**[FIGURE 2.1](#c02.xhtml#c02-fig-anc-0001)** CHAP authentication

One item that has really changed remote access is the increased number of ways that individuals can communicate with their company and clients. Hotels, airports, restaurants, coffee shops, and so forth now routinely offer Internet access. It's a low-cost way to get connectivity, yet it's a public network. This is why `virtual private networks` (VPNs) were created. A VPN is a mechanism for providing secure, reliable transport over the Internet. VPNs are secure virtual networks built on top of physical networks. The value of a VPN lies in the ability to encrypt data between the endpoints that define the VPN network. Because the data is encrypted, outside observers on a public network are limited in what they can see or access. From a security standpoint, it is important to understand that a VPN is not a protocol. It's a method of using protocols to facilitate secure communications. Since the 1990s, companies have been working to improve protocols designed for use with VPNs.

One example of this is Microsoft. In the mid-1990s, they led a consortium of networking companies to extend the Point-to-Point Protocol (PPP). The goal of the project was to build a set of protocols designed to work within the realm of VPNs. The result of this work was the Point-to-Point Tunneling Protocol (PPTP). The purpose of PPTP was to enable the secure transfer of data from a remote user to a server via a VPN. There are also many other variants such as CHAP, MS-CHAPv1, and MS-CHAPv2.

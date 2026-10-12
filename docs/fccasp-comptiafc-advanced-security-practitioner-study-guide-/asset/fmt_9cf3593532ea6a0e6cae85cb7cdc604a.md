
# VoIP Security and Implementation

## VoIP Security Risks

Before VoIP, voice was usually sent over the circuit-switched public switched telephone network (PSTN). These calls were then bundled by the phone carrier and sent over a dedicated communication path. As long as the conversation continued, no one else could use the same fixed path.

VoIP changes this because VoIP networks are basically packet-switched networks that utilize shared communication paths easily accessible by multiple users. Since this network is accessible by multiple users, an attacker can attempt to launch a man-in-the-middle (MITM) attack. MITM would allow an attacker to sit between the caller and the receiver and sniff the voice data, modify it, and record it for later review. Sniffing is the act of capturing VoIP traffic and replaying it to eavesdrop on a conversation. Sophisticated tools are not required for this activity. Easily available tools such as Cain & Abel (`www.oxid.it`) make this possible. Expensive, specialized equipment is not needed to intercept unsecured VoIP traffic. [Exercise 10.3](#c10.xhtml#c010-ex-03) will demonstrate how Cain & Abel can be used to sniff VoIP traffic. It's also worth mentioning that if network equipment is accessible an attacker can use Switched Port Analyzer (SPAN) to replicate a port on a switch and gain access to trunked VoIP traffic. It's important that the CASP understand the importance of placing physical controls so attackers cannot get access to network equipment.

Although VoIP uses TCP in some cases for caller setup and signaling, denial of service (DoS) is a risk. VoIP relies on some UDP ports for communication. UDP can be more susceptible to DoS than TCP-based services. An attacker might attempt to flood communication pathways with unnecessary data, thus preventing any data from moving on the network. Using a traditional PSTN voice communication model would mean that even if the data network is disabled, the company could still communicate via voice. With convergence, a DoS attack has the potential to disrupt both the IP phones and the computer network.

Yet another more recent inclusion into VoIP vulnerabilities was demonstrated at Defcon 2011 (`www.defcon.org/images/defcon-19/dc-19-presentations/Kotler-Amit/DEFCON-19-Kotler-Amit-Sounds-Like-Botnet.pdf`). The presenters demonstrated that VoIP could be used as a command and control mechanism for botnets. Basically, infected systems can host or dial into a conference call in order to perform a wide range of tasks, such as specifying what systems will participate in a distributed DoS (DDoS) attack, downloading new malware, or using the botnet for the exfiltration of data. This poses data loss prevention questions, to say the least. Here are some basic best practices that can be used for VoIP security:

*   Enforce strong authentication.
*   Implement restrictive access controls.
*   Disable any and all unnecessary services and ports.
*   Encrypt all VoIP traffic so attackers can't easily listen in on conversations.
*   Deploy firewalls and IDSs.
*   Keep systems and devices patched and updated.

You'll find a good list of free and paid VoIP security tools at `www.voipsa.org/Resources/tools.php`.

## VoIP Implementation

VoIP is a replacement for the PSTN of the past. The PSTN is composed of companies such as AT&T, the Baby Bells, and other public circuit-switched telephone networks. These traditional phone networks consist of telephone lines, fiber-optic cables, microwave transmission links, and so forth that are interconnected and allow any telephone in the world to communicate with any other. This equipment is highly specialized and may be proprietary to the telecommunication carrier. This makes it much harder to attack. After all, traditional telephones are only designed to make and receive calls. VoIP softphones can be a single application on a computer, laptop, iPad, or smartphone. A VoIP softphone resides on a system that has many different uses. A softphone opens another potential hole in the computer that an attacker can use as an entry point into the network or host. Hardware devices have advantages over software (softphones). Hardware-based phones are VoIP-based phones that look like typical phones but are connected to the data network instead of PSTN. These devices should be viewed as embedded computers that can be used for other purposes. To learn more, visit:

`www.blackhat.com/presentations/bh-usa-06/BH-US-06-Endler.pdf`

A well-designed VoIP implementation requires the CASP to consider the design of the network and to segregate services. Using technologies like a virtual local area network (VLAN), the CASP can segregate data traffic from voice traffic; however, convergence is making this task much harder. Implementing VLANs correctly can drastically reduce and often eliminate the potential for sniffing attacks that utilize automated tools such as those referenced earlier, as well as many other tools that focus on this type of attack exclusively regardless of hardware- or software-based phones. One such tool is Voice Over Misconfigured Internet Telephones (VOMIT), which deciphers any voice traffic on the same VLAN or any VLANs that it can access. You can learn more at `http://vomit.xtdnet.nl/`.

Another implementation concern is quality of service (QoS). Although no one may notice if email arrives a few seconds later, voice does not have that luxury. Fortunately, segmentation via VLANs can assist with remedying this kind of issue as well. Here are some QoS examples:

*   **Jitter** is the variation in transmission latency that can cause packet loss and degraded VoIP call quality.
*   **Latency** is a delay in the transmission of a data packet.

Before VoIP systems are implemented, a CASP must explore techniques to mitigate risk by limiting exposures of data networks from spreading to voice networks. VoIP equipment, gateways, and servers tend to use open standards based on RFCs and open protocols. This also allows an attacker to have a better understanding of the equipment and technology. If that is not enough, most of the vendors place large amounts of product information on their websites. This aids the attackers in ramping up their knowledge very quickly.

## Remote Access and Advanced Trust Models

**Remote access** is the ability to get access to a computer, laptop, iPad, or other device to a network or remote host. Years ago, dial-up systems were widely used for remote access; today, VPNs are much more common. Remote access can be defined as either centralized or decentralized. Centralized access control implies that all authorization verification is performed by a single entity within a system; two such systems are RADIUS and Diameter:

1.  **RADIUS Configurations** Remote Authentication Dial-In User Service (RADIUS) uses a modem pool for connecting users to an organization's network. The RADIUS server will contain usernames, passwords, and other information used to validate the user. Many systems formerly used a callback system for added security control. When used, the callback system calls the user back at a predefined phone number. RADIUS is a client-server protocol used to authenticate dial-in users and authorize access. RADIUS can also be used in more modern configurations when configured to be used with wireless networking and 802.1x port-based authentication.
2.  **Diameter** The Diameter protocol was designed to be an improvement over RADIUS and have better handling of mobile users (IP mobility). Diameter provides the functions of authentication, authorization, and accounting. However, RADIUS remains very popular.

**Decentralized access control** can be described as having various entities located throughout a system performing authorization verification. Two good examples of this type of technology are domains and trusts. Examples of access authentication protocols include the following:

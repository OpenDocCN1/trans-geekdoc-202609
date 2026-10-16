
If your server doesn’t need certain email services running (SMTP, POP3, and IMAP), disable them — immediately.

For web-based email, such as Microsoft’s Outlook Web Access (OWA), properly test and secure your web server application and operating system by using the testing techniques and hardening resources I mention throughout this book.

Require strong passwords. For stand-alone accounts as well as domain-level Exchange or similar accounts, any password weaknesses on the network will trickle over to email and be exploited by someone via Outlook Web Access or POP3. I cover password hacking in [Chapter 8](#c08.xhtml).

Be sure to include your email server(s) in your vulnerability scanning and penetration testing efforts.

If you’re running sendmail — especially an older version — don’t. Consider running a secure alternative, such as Postfix ([`www.postfix.org`](http://www.postfix.org)) or qmail ([`www.qmail.org`](http://www.qmail.org)).

## Understanding VoIP

A widely used technology in enterprises today is Voice over Internet Protocol. In-house VoIP systems and systems for remote users, VoIP servers, softphones, and related components have their own set of security vulnerabilities. As with most things security-related, many people haven’t thought about the security issues surrounding voice conversations traversing their networks or the Internet, but those issues certainly need to be on your radar. Don’t fret — it’s not too late to make things right. Just remember that even if protective measures are in place, VoIP systems need to be included in your overall security testing strategy on a continuous basis.

### VoIP vulnerabilities

As with any technology or set of network protocols, the bad guys are always going to figure out how to break in. VoIP is certainly no different. In fact, given what’s at stake (phone conversations and phone system availability), you have a lot to lose.

VoIP-related systems are no more (or less) secure than other common computer systems. Why? VoIP systems have their own operating system, they have IP addresses, and they’re accessible on the network. Compounding the issue is the fact that many VoIP systems house more *intelligence* (a fancy word for “more stuff that can go wrong”), which makes VoIP networks even more hackable.

![tip](images/tip.png)If you want to find out more about how VoIP operates, which will undoubtedly help you root out vulnerabilities, check out *VoIP For Dummies,* by Timothy V. Kelly (John Wiley & Sons, Inc.).

On one hand, VoIP systems have vulnerabilities very similar to other systems I cover in this book, including default settings, missing patpches, and weak passwords. For that reason, using the standard vulnerability scanning tools that I cover is important. [Figure 14-12](#c14.xhtml#c14-fig-0012) shows various vulnerabilities associated with the authentication mechanism in the web interface of a VoIP adapter.

![ FIGURE 14-12:  A WebInspect scan of a VoIP network adapter showing several weaknesses.](images/9781119485476-fg1412.png)

 [FIGURE 14-12:](#c14.xhtml#rc14-fig-0012)  A WebInspect scan of a VoIP network adapter showing several weaknesses.

Looking at these results, you might think that this device is a basic web server. That’s exactly my point: VoIP systems are nothing more than networked computer systems with vulnerabilities that can be exploited.

On the other hand, two major security weaknesses are tied specifically to VoIP:

*   **Phone-service disruption:** Yep, VoIP is susceptible to DoS attacks just like any other system or application. VoIP is as vulnerable as the most timing-sensitive applications out there, given the low tolerance that people have for choppy and dropped phone conversations (cellphones aside, of course).

*   **Lack of encryption:** The other big weakness of VoIP is that voice conversations usually aren’t encrypted; therefore, they can be intercepted and recorded. Imagine the fun that a bad guy could have recording conversations and blackmailing his victims. This attacks is very easy on unsecured wireless networks, but as I show in the upcoming section “[Capturing and recording voice traffic](#c14.xhtml#c14-sec-0034),” it’s also pretty simple to carry out on wired networks.

 ![warning](images/warning.png)If a VoIP network isn’t protected via network segmentation, such as a virtual local-area network (VLAN), the voice network is especially susceptible to eavesdropping, DoS, and other attacks. But the VLAN barrier can be overcome in many environments by a tool called VoIP Hopper ([`http://voiphopper.sourceforge.net`](http://voiphopper.sourceforge.net)). Just when you think that your voice systems are secure, a tool like VoIP Hopper comes along. It’s an older tool, but it can still work for this type of testing.

Unlike typical computer security vulnerabilities, these issues with VoIP aren’t easily fixed with simple software patches. These vulnerabilities are embedded in the Session Initiation Protocol (SIP) and Real-Time Transport Protocol (RTP) that VoIP uses for its communications. The following sections describe two VoIP-centric tests that you should use to assess the security of your voice systems.

![tip](images/tip.png)It’s important to note that although SIP is the most widely used VoIP protocol, H.323 also exists, so don’t spin your wheels testing for SIP flaws if H.323 is the protocol in use. Vist [`www.packetizer.comi/ipmc/h323_vs_sip`](http://www.packetizer.comi/ipmc/h323_vs_sip) for additional details on H.323 versus SIP.

#### Scanning for vulnerabilities

Outside the basic network, operating-system, and web-application vulnerabilities, you can uncover VoIP issues if you use the right tools. The good news is that you likely already have these tools at your disposal in the form of network vulnerability scanners such as Nexpose ([`https://www.rapid7.com/products/nexpose`](https://www.rapid7.com/products/nexpose)) and web vulnerability scanners such as Netsparker ([`https://www.netsparker.com`](https://www.netsparker.com)). Common flaws in VoIP call managers and phones include weak passwords, cross-site scripting, and missing patches that can be exploited with a tool such as Metasploit.

![tip](images/tip.png)Kali Linux has several VoIP tools built in via Applications/Vulnerability Analysis/VoIP Tools. Other free tools for analyzing SIP traffic are PROTOS ([`www.ee.oulu.fi/research/ouspg/protos/testing/c07/sip/index.html`](http://www.ee.oulu.fi/research/ouspg/protos/testing/c07/sip/index.html)) and sipsak ([`https://www.voip-info.org/wiki/view/Sipsak`](https://www.voip-info.org/wiki/view/Sipsak)). A good website that lists a variety of VoIP-related tools is [`www.voipsa.org/Resources/tools.php`](http://www.voipsa.org/Resources/tools.php).

#### Capturing and recording voice traffic

If you have access to the wired or wireless network, you can capture VoIP conversations easily, which is a great way to prove that the network and the VoIP installation are vulnerable.

![warning](images/warning.png)Many legal issues re associated with tapping into phone conversations, so make sure that you have permission and are careful not to abuse your test results.

You can use Cain & Abel (technically, just Cain for the features I demonstrate here) to tap into VoIP conversations. You can download Cain & Abel free at [`www.oxid.it/cain.html`](http://www.oxid.it/cain.html). Using Cain’s ARP poison routing feature, you can plug into the network and have it capture VoIP traffic by following these steps:

1.  **Load Cain & Abel, and click the Sniffer tab to enter network analyzer mode.**

    The Hosts page opens by default.

2.  **Click the Start/Stop APR icon (which looks like the nuclear-waste symbol).**

    The ARP poison routing process starts and enables the built-in sniffer.

3.  **Click the blue plus-sign (+) icon to add hosts on which to perform ARP poisoning.**

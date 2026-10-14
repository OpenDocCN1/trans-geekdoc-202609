
## Test Your Understanding

- 32. a. Why are dynamic routing protocols needed?
- b. What is the main TCP/IP interior dynamic routing protocol for large networks?
- c. What is the main TCP/IP exterior dynamic routing protocol?
- d. Why is Cisco’s EIGRP attractive?
- e. Is a company free to select its interior dynamic routing protocol, exterior dynamic routing protocol, or both?
- f. How could an attacker use dynamic routing protocols to attack a network?

Simple Network Management Protocol (SNMP). As Figure A-23 shows, the manager program can send SNMP GET messages to tell managed devices to send back certain information. The manager can even send SET messages that can change the configurations of remote devices. This allows the manager to fix many problems remotely.

> Many firms disable remote configuration because of the damage that attackers could do with it. For instance, SET can be used to get routers to misroute some or all packets or route all packets through an attacker’s sniffer.

## A.12 Application Standards

Most applications have their own application layer standards. In fact, given the large number of applications in the world, there is a multitude of application layer standards. This means a multitude of potential security issues at the application level.

## Test Your Understanding

- 33. a. What is the purpose of SNMP?
- b. Distinguish between the SNMP GET and SET commands.
- c. Why do many organizations disable the SET command?

Figure A-23 Simple Network Management Protocol (SNMP)

![](img/073342643701cc54eb7875c41ab92ef2_573_0.png)

As corporations get better at defending against attacks at lower layers, attackers have switched their focus to applications. If an attacker can take over an application running with high privileges, he or she usually obtains these privileges. Many applications run at the highest privileges, and attackers that compromise them “own the box.”

## HTTP AND HTML

Many applications have two types of standards. One is a transport standard to transfer application layer messages between applications on different machines. For the World Wide Web, this is the Hypertext Transfer Protocol (HTTP). The other is a standard for document structure. The main document structure standard for the WWW is the Hypertext Markup Language (HTML).

Netscape, which created the first widely used browser, also created a security standard to protect HTTP communication. This was Secure Sockets Layer (SSL). Later, the Internet Engineering Task Force took over SSL and changed the name of the standard to Transport Layer Security (TLS).

## E-MAIL

For e-mail, in turn, popular transfer standards are the Simple Mail Transfer Protocol (SMTP) for sending e-mail and POP and IMAP for downloading e-mail to a client from a mailbox on a server. Popular document body standards include RFC 2822 (for all-text messages), HTML, and MIME.

An obvious security issue in e-mail is content filtering. Viruses, spam, phishing messages, and other undesirable content should be filtered out before they reach users and can do damage.

Another security issue in e-mail is the securing of messages flowing from the sending client to the sender’s mail server, from the sender’s mail server to the receiver’s mail server, and from the receiving mail server to the receiving client. Fortunately, there are security standards to protect these message flows. The leading standards are SSL/TLS and S/MIME. Unfortunately, the IETF has been unable to agree upon a single security standard. This lack of standards clarity has hurt the adoption of e-mail security.

When web mail, which uses HTTP and HTML for e-mail communication, is used, SSL/TLS can work between the sender and the sender’s mail server and between the receiver’s mail server and the receiver. Transmission between the e-mail servers is another issue. Of course, senders can send encrypted message bodies directly to receivers. However, this prevents filtering at firewalls.

## TELNET, FTP, AND SSH

The two earliest applications on the Internet were the File Transfer Protocol (FTP) and Telnet. FTP provides bulk file transfers between hosts. Telnet allows a user to launch a command shell (user interface) on another computer. Neither of these standards has any security. Of particular concern is that both send passwords in the clear (without encryption) during login. The newer Secure Shell (SSH) standard can be used in place of both FTP and Telnet while providing high security.

## OTHER APPLICATION STANDARDS

There are many other applications and therefore application standards. These include voice over IP (VoIP), peer-to-peer applications, and service-oriented architecture (web service) applications, among many others. Most new applications have challenging security issues. Application security has become perhaps the most complex aspect of network security.

## Application Exploits

- By taking over applications, hackers gain the permissions of the exploited program
- A multitude of application standards
- Consequently, a multitude of security issues at the application level

## Many Applications Need Two Types of Standards

- One for the transmission of messages, one for the content of application documents
- For the World Wide Web, these are HTTP and HTML, respectively
- For transmission, e-mail uses SMTP, POP, and IMAP
- For message content, e-mail uses RFC 2822 (all-text), HTML, and MIME

## FTP and Telnet

- Have no security
- Passwords are transmitted in the clear so can be captured by sniffers
- Secure Shell (SSH) can replace both securely

## Many Other Application Standards Have Security Issues

- Voice over IP
- Service-oriented architecture (SOA); web services
- Peer-to-peer applications

Figure A-24 Application Standards (Study Figure)

## Test Your Understanding

- 34. a. Why are there usually two protocols for each application?
- b. In e-mail, distinguish between SMTP and POP.
- c. Why are Telnet and FTP dangerous?
- d. What secure protocol can be used instead of Telnet and FTP?
- e. What is the security standards situation in e-mail?

## A.13 Conclusion

When the Internet was created in the early 1980s, its standards almost completely ignored security. In the first idyllic years of the Internet, this benign neglect made sense. Attacks, while not absent, were merely a nuisance. During the 1990s, when the Internet grew explosively, attackers gravitated to the Internet rapidly. Since then, there has been an arms race between attackers and corporate defenders.

Most attacks take place over networks, including both the Internet and internal networks. The objective of this module has been to cover important networking concepts that security specialists need to understand to work effectively. Within the module text, the security implications of various networking concepts were noted briefly.

## Hands-on Projects

### Project 1

One of the most well-known packet sniffers is Wireshark® (formerly named Ethereal®). This is a flexible and powerful tool. Any network administrator worth his or her salt will know how to run Wireshark. Most professionals use it often. Wireshark has been getting better and better with every release. It will likely be around for a long time as the industry standard.

You will install Wireshark and do a few examples to give you a small taste of what Wireshark can do. In addition to loading Wireshark, you will also have to load WinPcap® in order to actually capture the packets being sent over your network.

- 1. Download Wireshark from www.wireshark.org/download.html.
- 2. Click Download Windows Installer. (Download the latest stable release.)
- 3. Click Save.
- 4. Save the file in your download folder.
- 5. If the program doesn’t automatically open, browse to your downloads folder.
- 6. Double-click Wireshark-setup-3.0.3.exe. (The software version numbers will be slightly different as newer versions are released.)
- 7. Install Wireshark and WinPCap.
- 8. Double-click the Wireshark icon on your desktop.
- 9. Click Interface List. (This will display a list of all available network interfaces on your computer. You will want to note the description and IP address of the interface with the most traffic. You will need to select this interface in the following steps.)
- 10. Note the interface with the most traffic. (You will select this interface in the following steps.)
- 11. Close the Capture Interfaces window.
- 12. Click Capture and Options.
- 13. Select your Network Interface Card if it is not already selected.
- 14. Close all other programs you currently have open except your word processing program.
- 15. Click Start.
- 16. Let it run for 10 seconds.
- 17. While you are waiting, open a web browser and go to www.google.com.
- 18. Return to your Wireshark window.
- 19. In the file menu, click Capture and Stop.
- 20. Scroll up until you see a green and blue area. (These are the packets you captured when you requested Google’s main page.)
- 21. Take a screenshot.
- 22. Scroll down until you see a line that has GET / HTTP/1.1. (You may have to try more than one until you get to the packet that shows “www.google.com” in the bottom pane.)
- 23. Select that row.
- 24. In the bottom pane, you will see a bunch of numbers to the left. (It’s the packet’s contents in hexadecimal.) Just to the right you will see the content of the packet in a column.
- 25. Select the text: www.google.com.
- 26. Take a screenshot.

*Note:* You just picked packets off your network and looked at their contents. There may have been a lot of traffic that you couldn’t interpret. Don’t worry about the information on your screen that is difficult to understand. In the next project, you will use a filter to capture only web traffic going over Port 80.

### Project 2

In this project, you are going to filter out all the “extra” packets you captured and just look at web traffic. Too often, you will capture much more information than you will ever want or need. Being able to filter out the traffic you don’t want is an important skill.

Wireshark can filter packets by IP address or by port number. A thorough understanding of TCP/IP will greatly aid your understanding of how packet filtering works. There are several great online tutorials available that will teach you the basics of TCP/IP.

Below are instructions on how to filter out all packets *except* web traffic by creating a filter for just Port 80. This will capture all the web traffic going to *all* the computers on your local network. Reread the last sentence. Yes, you read that correctly, it may even capture web traffic intended for other computers on your network. This is one of the reasons why packet sniffers are important to learn.

- 1. With Wireshark open, click Capture and Options.
- 2. If you haven’t already done so, select your network interface card (NIC).
- 3. Double-click the interface you have selected. (This will allow you to enter a capture filter.)
- 4. Click Capture Filter.

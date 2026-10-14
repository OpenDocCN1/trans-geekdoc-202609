is normally very difficult to do. However, if the attacker sends an RST message, which terminates a connection, this protection is greatly reduced. In fact, it is fairly easy to send RST messages that close legitimate open connections. Security that results from the inherent operation of a standard is called incidental security.

# Security Explicitly Designed into the Standard

A second issue is security explicitly designed into the standard. Most standards were initially created without any security. If security was added in later versions, it was often done in an awkward way. For instance, IP, which is the main protocol for delivering packets over the Internet, originally had no security. The IPsec standards were created to address this weakness, but IPsec is burdensome and not widely used.

# Security in Older Versions of the Standard

Third, even when security is added to a standard, it usually is added only to later versions of the standard. If a company uses an older version of the standard, it is limited in terms of the security it can implement.

# Defective Implementation

A fourth issue is the security of defective standards implementations in vendor products. These defective implementations may create vulnerabilities that attackers can exploit even if the standard itself is highly secure.

# Test Your Understanding

+   7. List the four security problems with protocols. Write one sentence describing each.

# A.4 Core Layers in Layered Standards
Architectures

Standards are complex. A common way to deal with complex problems is to break them down into smaller parts. Figure A-8 shows that standards are divided into three **core layers**. Collectively, these layers have the functionality needed to allow any application program on one host on one network of an internet to interoperate with another program on another host on any other network of the internet.

The highest core layer governs the interactions of *applications*. For instance, World Wide Web access is governed by the Hypertext Transfer Protocol (HTTP). In World Wide Web access, the two application programs—the browser on the client PC and the webserver program on the webserver—have to send messages governed by the HTTP standard.

The middle core layer is the *internet core layer*. Standards at this layer govern how packets are delivered across an internet, including the global Internet. One of the main standards at the internet core layer is the Internet Protocol (IP).

The lowest core layer is the *single-network core layer*. Standards at this layer govern the transmission of frames across the switches and transmission lines in a single network (a LAN or WAN).
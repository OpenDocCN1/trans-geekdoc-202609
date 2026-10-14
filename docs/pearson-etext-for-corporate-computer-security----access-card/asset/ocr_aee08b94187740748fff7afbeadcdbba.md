# **Figure A-13** IP Version 6 Packet

![](bbox=[0.11, 0.114, 0.699, 0.298])

# ## Test Your Understanding

+   18.  
+      a. How long are traditional IP addresses?  
+      b. What are the three parts of an IP address?  
+      c. Why are masks needed?  
+      d. What is the main advantage of IPv6?

# ## IPsec

IP, which was created in the early 1980s, initially had no security at all. In the 1990s, the Internet Engineering Task Force developed a general way to secure IP transmission. This was IP security, which normally is just called IPsec (eye-pea-SEK). IPsec is a general security solution because everything within the data field of the protected packet is secure. This includes the transport message and the application message contained in the transport message. The IP packet, entirely or in part, is also secured, depending on the IPsec operating mode. Originally developed for IPv6, IPsec was extended to IPv4 as well, becoming a completely general security solution. IPsec provides transparent protection to all transport and application layer protocols, meaning that these higher-layer protocols are protected without their even knowing that IPsec is working.

> IPsec operates in two modes. In transport mode, there is protection all the way from the source host to the destination host. In tunnel mode, there is only protection between sites and none within sites. Transport mode gives stronger protection but is much more expensive to implement. In addition, firewalls cannot easily filter transport mode traffic, which is unreadable unless the firewall has the decryption key for the communication.

# ## Test Your Understanding

+   19.  
+      a. In what sense is IPsec a general protection strategy for all internet, transport, and application protocols?  
+      b. Does IPsec work with IPv4, IPv6, or both?  
+      c. Compare IPsec transport mode and tunnel mode.
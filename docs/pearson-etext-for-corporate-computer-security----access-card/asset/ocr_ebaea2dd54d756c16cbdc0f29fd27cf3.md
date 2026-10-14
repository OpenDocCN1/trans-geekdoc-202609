# A.9 The Transmission Control Protocol

As noted earlier, the Transmission Control Protocol (TCP) is one of the two possible TCP/IP protocols at the transport layer. Figure A-14 shows a TCP message, which is called a TCP segment.

# Test Your Understanding

+   20. a. How many TCP/IP transport layer protocols are there?
+      b. What is a TCP message called?

# TCP: A Connection-Oriented and Reliable Protocol

# CONNECTIONLESS AND CONNECTION-ORIENTED PROTOCOLS

Protocols are either connectionless or connection oriented.

+   - Connection-oriented protocols are like telephone conversations. When you call someone, there is at least tacit agreement at the beginning of a conversation that you are both willing to speak. For example, such expressions as “Hold, please” and “Can I call you back?” indicate an unwillingness to talk at the moment. Similarly, there is at least tacit agreement that you are done talking at the end of the conversation. (Simply hanging up is considered rude.)
+   - Connectionless protocols, in turn, are like e-mail. You do not need to get someone’s permission to send them an e-mail. You just send it.

TCP is a connection-oriented protocol. Figure A-15 shows a sample TCP connection. In TCP, three messages are sent to open a connection. The originator of the connection transmits a TCP SYN segment to indicate that it wishes to open a TCP session. The other transport process sends back a TCP SYN/ACK segment that acknowledges

Figure A-14 Transmission Control Protocol (TCP) Segment

![](bbox=[0.3, 0.65, 0.89, 0.93])

Flag fields are 1-bit fields. They include SYN, ACK, FIN, RST, PSH, and URG
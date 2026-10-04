# Summary (14.8)

The following is a summary of the topics in the chapter and their corresponding online modules.

# Transportation of Data

The transport layer is the link between the application layer and the lower layers that are responsible for network transmission. The transport layer is responsible for logical communications between applications running on different hosts. The transport layer includes TCP and UDP. Transport layer protocols specify how to transfer messages between hosts and is responsible for managing the reliability requirements of a conversation. The transport layer is responsible for tracking conversations (sessions), segmenting data and reassembling segments, adding header information, identifying applications, and handling conversation multiplexing. TCP is stateful and reliable, it acknowledges data, it re-sends lost data, and it delivers data in sequenced order. Use TCP for email and the web. UDP is stateless, fast, has low overhead, does not require acknowledgments, does not re-send lost data, and delivers data in the order in which it arrives. Use UDP for VoIP and DNS.

# TCP Overview

TCP establishes sessions, ensures reliability, provides same-order delivery, and supports flow control. A TCP segment adds 20 bytes of overhead as header information when encapsulating the application layer data. The TCP header fields are Source Port, Destination Port, Sequence Number, Acknowledgment Number, Header Length, Reserved, Control Bits, Window Size, Checksum, and Urgent. Applications such as HTTP, FTP, SMTP, and Telnet use TCP.

# UDP Overview

UDP reconstructs data in the order in which it is received, it does not re-send lost segments, it does not establish sessions, and does not inform the sender of resource availability. The UDP header fields are Source Port, Destination Port, Length, and Checksum. Applications such as DHCP, DNS, SNMP, TFTP, VoIP, and video conferencing use UDP.

# Port Numbers

The TCP and UDP transport layer protocols use port numbers to manage multiple simultaneous conversations. This is why the TCP and UDP header fields identify source and destination application port numbers. The source and destination ports
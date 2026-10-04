As the layer's name implies, functions at the session layer create and maintain dialogues between source and destination applications. The session layer handles the exchange of information to initiate dialogues, keep them active, and restart sessions that are disrupted or idle for a long period of time.

# TCP/IP Application Layer Protocols (15.1.3)

The TCP/IP application layer protocols specify the format and control information necessary for many common internet communication functions. Application layer protocols are used by both the source and destination devices during a communication session. For communications to be successful, the application layer protocols that are implemented on the source and destination hosts must be compatible.

Table 15-1 describes the most popular application layer protocols.

Table 15-1 TCP/IP Application Layer Protocols

| Application | Protocol(s) | Port Number | Characteristics |
|---|---|---|---|
| Name system | Domain Name System (DNS) | TCP, UDP client 53 | Translates domain names, such as cisco.com, into IP addresses |
| Host config | *Bootstrap Protocol (BOOTP)* | UDP client 68, server 67 | Enables a diskless workstation to discover its own IP address, the IP address of a BOOTP server on the network, and a file to be loaded into memory to boot the machine

BOOTP is being superseded by DHCP |
|  | Dynamic Host Configuration Protocol (DHCP) | UDP client 68, server 67 | Dynamically assigns IP addresses to be reused when no longer needed |
| Email | *Simple Mail Transfer Protocol (SMTP)* | TCP 25 | Enables clients to send email to a mail server

Enables servers to send email to other servers |
|  | *Post Office Protocol (POP3)* | TCP 110 | Enables clients to retrieve email from a mail server

Downloads the email to the local mail application of the client |
|  | *Internet Message Access Protocol (IMAP)* | TCP 143 | Enables clients to access email stored on a mail server

Maintains email on the server |
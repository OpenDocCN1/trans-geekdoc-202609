based on UDP, and version 3 introduced TCP support. Both are implemented on top of RPC (see Remote Procedure Calls). NFS versions 2 and 3 are stateless protocols, mainly due to performance considerations. As a consequence, the server must manage file locking separately.

| Ports | See RPC (Section "Directory services") |
|-------|------------------------------------------|
| Definition | RFC 1094 |
|  | RFC 1813 |
|  | RFC 3010 |

Table 4.6 — NFS Quick Reference

Secure NFS (SNFS) offers secure authentication and encryption using Data Encryption Standard (DES) encryption. In contrast to standard NFS, secure NFS (or rather secure RPC) will authenticate each RPC request. This will increase latency for each request as the authentication is performed and introduces a light performance premium, mainly paid for in terms of computing capacity. Secure NFS uses DES encrypted time stamps as authentication tokens. If server and client do not have access to the same time server, this can lead to short-term interruptions until server and client have resynchronized themselves.

NFS version 4 is a stateful protocol that uses TCP port 2049. UDP support (and dependency) has been discontinued. NFS version 4 implements its own encryption protocols on the basis of Kerberos and has discontinued use of RPC. Foregoing RPC also means that additional ports are no longer dynamically assigned, which enables use of NFS through firewalls. Another approach that the security architect could consider as part of his or her design is to plan for the securing of NFS where it must be deployed, by tunneling NFS through Secure Shell (SSH), which can be integrated with operating system authentication schemes.

# Simple Mail Transfer Protocol (SMTP) & Enhanced Simple Mail Transfer Protocol (ESMTP)

Using port 25/TCP, SMTP is a client/server protocol utilized to route email on the Internet. Information on mail servers for Internet domains is managed through DNS, using mail exchange (MX) records.ww Although SMTP takes a simple approach to authentication, it is robust in the way it deals with unavailability; an SMTP server will try to deliver email over a configurable period.
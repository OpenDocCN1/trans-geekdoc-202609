is encrypted using a shared key. The resulting block is encrypted using symmetric metric encryption.

# 12.7.6 Some Terms Related to SSL

# SSL Session:

An SSL Session is an association between a client and a server. The sessions are created by Handshake Protocol by defining a set of cryptographic security parameters, which can be shared among many connections under the session. Sessions are used to avoid expensive negotiations of new security parameters for each connection.

# SSL Connection:

A connection is a transport for providing service. The connections are transient, and each connection is associated with one session.

# Session State:

A session state is defined by the following parameters:

+   i. Session Identifier: An arbitrary byte sequence chosen by the server.

+   ii. Peer Certificate: An X.509.V3 Certificate of the peer.

+   iii. Compression Method: The algorithm used to compress data prior to encryption.

+   iv. Cipher Spe: A Symmetric Encryption Algorithm like AES for providing confidentiality and a MAC algorithm using a secret key and an embedded Hash algorithm (like MD5 or SHA-1) used for MAC calculation.

+   v. Master Secret: A 48-byte secret, shared between the client and the server.

+   vi. Resumable: It indicates whether the session can be used to initiate new connections.

Connection State: A connection state is defined by the following parameters:

+   i. Server and Client Random: Byte sequences chosen by the server and the client for each connection.
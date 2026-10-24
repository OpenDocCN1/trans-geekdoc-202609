hash function, if any bit in the message is altered during transmission, the transmitted MAC would differ from the one recomputed at the receiver. Hence, the MAC is also used as a form of checksum with much stronger protection than traditional checksum method such as CRC16.

In conventional systems, communication between a client and server is done over a session. Hence, security mechanisms were designed around this need. At the beginning of the session, the client and the server would mutually authenticate each other. Once the authentication step is done, a session key would be created and used to encrypt all messages exchanged within the session. For a prolonged session, the session key might be refreshed. For sessions conducted over the Web, the secure socket layer (SSL) (or transport layer security) protocol is typically used. The server authentication is done via a digital signature and public-key certificate protected by a public-key infrastructure. Client authentication is typically done via user-name and password. Some enterprise systems, such as directory services, adopt much more sophisticated authentication algorithms based on the challenge-response approach.

# REFERENCES

+   1. A. Avizienis and L. Chen. On the implementation of n-version programming for software fault tolerance during execution. In Proceedings of the IEEE International Computer Software and Applications Conference, pages 149–155, 1977.
+   
+   2. A. Avizienis, J. C. Laprie, B. Randell, and C. Landwehr. Basic concepts and taxonomy of dependable and secure computing. IEEE Transactions on Dependable and Secure Computing, 1(1):11–33, 2004.
+   
+   3. M. Y. Chen, E. Kiciman, E. Fratkin, A. Fox, and E. Brewer. Pinpoint: Problem determination in large, dynamic internet services. In Proceedings of the 2002 International Conference on Dependable Systems and Networks, DSN ’02, pages 595–604, Washington, DC, USA, 2002. IEEE Computer Society.
+   
+   4. M. Franz. Understanding and countering insider threats in software development. In Proceedings of the International MCETECH Conference on e-Technologies, pages 81–90, January 2008.
+   
+   5. L. Lamport, R. Shostak, and M. Pease. The byzantine generals problem. ACM Transactions on Programming Languages and Systems, 4:382–401, 1982.
+   
+   6. P. M. Melliar-Smith and B. Randell. Software reliability: The role of programmed exception handling. In Proceedings of an ACM conference on
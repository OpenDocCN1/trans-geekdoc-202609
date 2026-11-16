# # Security Model

The security model specifies how the contents of the directory can be protected from unauthorized access. It also specifies the scope of access for the clients, that is, it specifies which clients can access which parts of the directory tree and whether they can perform update or interrogation operations or both on that part of the tree.

In LDAPv2, LDAP clients provide a DN and a clear-text password to the server. The password is the authentication credential and the DN defines the scope of authentication. However, this method is susceptible to a malicious user who steals passwords by eavesdropping on the network. This has been prevented lately by using the Kerberos authentication protocol.

Since LDAPv3, SASL handles authentication and security. SASL is merely a standard way for plugging in different authentication protocols that do the actual work of authentication and enforcement of security. As we have seen, SSL is one such protocol that plugs into the SASL model and is almost the de facto standard for secure communications over TCP/IP networks.

The successor to SSL is **TLS** (Transport Layer Security), which is also a pluggable authentication scheme that is supported by several LDAP vendors. In future, LDAP implementations are expected to use the `startTLS` mechanism to encrypt a communication channel and TLS for the clients to authenticate themselves and to verify identity of servers. Please see RFC 2487 http://www.ietf.org/rfc/rfc2487.txt?number=2487 for more information on `startTLS`.

Currently LDAP does not have an inherent standard means to enforce access control. However, most LDAP vendors have some access control model built into their implementations. Access control is of significance because it allows the owners of information to modify it. For example, the access control policy of a directory can be set up such that a user can change his telephone number and address but cannot modify any other entries, a manager can modify his entry and all the entries belonging to his subordinates, or a facilities administrator can modify the room number and telephone number of all employees and nothing else.

# # Advanced Features of LDAP

Let's discuss some features which LDAP supports but are seldom used except by administrators or advanced users.

# # Asynchronous Operations

LDAP supports asynchronous operations on the directory. Asynchronous operations are operations that do not block. Consider an application (LDAP-enabled or otherwise) that needs to frequently access external devices such as hard disks or networks apart from doing some other processing. An operation on an external device is quite slow to respond and the application is forced to wait in the subroutine that accessed the device until the device responds. This prevents the application from doing any other useful work. This is a typical application that is synchronous in nature.

In the case of asynchronous operation, the call to the device-specific function would not block in the subroutine, thereby allowing the application to continue and do other useful stuff. The application will subsequently be notified when the device responds. In the case of LDAP, the operations from the client to the server may block, as the transaction is happening over a network (most of the time). To allow the LDAP application to circumvent this, asynchronous operations are allowed.
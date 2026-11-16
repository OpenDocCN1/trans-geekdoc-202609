# # Networking and TCP/IP

With the proliferation of TCP/IP-based networks and services accessible over these networks, the ways and means to access these services by other applications is of significant interest. PHP scripts are no exception to this trend. In this chapter we shall look at the functions that PHP provides for such access by building illustrative applications that utilize these functions.

PHP scripts inherently use some level of networking, since most often they are invoked over a network and send their result over a network. From a protocol standpoint this is purely a transaction-free interaction, since the protocol itself, HTTP, does not provide for a direct mechanism to maintain the state of the application. However, applications make use of PHP sessions in the form of cookies or URL session parameters to achieve application-level session semantics.

In this chapter, we shall not be looking at this interaction; rather the functionality available to PHP scripts to connect and interact with other services that adhere to various TCP/IP based protocols is in focus. In particular we shall be looking at the following aspects of TCP/IP programming:

+   - A short introduction to the TCP/IP protocol suite
+   - Name resolution and network directory services such as Domain Name System (DNS) and Yellow Pages/Network Information Services (YP/NIS)
+   - The Sockets API provided by PHP
+   - Simple Network Management Protocol (SNMP) client functions
+   - Applications that deal with some of the protocols directly and the functional interfaces to other protocols
![](bbox=[0.22, 0.1, 0.82, 0.2])

Figure 15-19 Step 4: DNS Server Responding to the DNS Query

Step 5. The client computer uses the IP address to make requests of the server, as shown in Figure 15-20.

![](bbox=[0.21, 0.31, 0.8, 0.57])

Figure 15-20 Step 5: Client Sending Web Request Using IP Address

# DNS Message Format (15.4.2)

The DNS server stores different types of resource records that are used to resolve names. Each record contains the name, address, and type of record. Some of these record types are as follows:

+   - A: An end-user device IPv4 address
- NS: An authoritative name server
- AAAA: An end-user device IPv6 address; pronounced “quad-A”
- MX: A mail exchange record

When a client makes a query, the DNS process on the server first looks at the server's own records to resolve the name. If it is unable to resolve the name by using its
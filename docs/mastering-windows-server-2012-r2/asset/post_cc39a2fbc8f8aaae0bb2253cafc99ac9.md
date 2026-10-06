
You might be wondering to yourself, “Why would this be necessary?” Well, the primary reasons are security related. Consider a hacker who has set up a malicious service to listen for DNS queries for FDNs starting with www. on a network. The rogue service gets a query, it automatically sends a bogus response to the client with the IP address of the hacker's server. The website loads worms, viruses, Trojans, and other unsafe code before the user knows what's happening. Now, if the browser could perform a reverse lookup on the provided IP address, it could compare the result with the queried name. If it didn't match, it wouldn't have to connect to the web server.

An example of how this type of reverse name resolution lookup works in the real world is with the SMTP service on Windows. This service has to perform reverse lookups on connections to the server. The SMTP servers provide their domain names in the communication, and the TCP/IP address is provided in the connection. The reverse lookup can then be performed to verify that things match as they should do.

The `nslookup` command initiates the use of the reverse lookup. In the following code, the reverse lookup started in interactive mode on a server that does not have a pointer (PTR) record in the reverse lookup zone. The default server is listed as Unknown. DNS queries are flaky when this is the case.

```
C:\Users\Administrator.BFI>nslookup
Default Server: Unknown
Address: 192.168.0.10
```

If the pointer record is created in the reverse lookup zone, the command looks better. You can see here it lists the name of the server:

```
C:\Users\Administrator.BFI>nslookup
Default Server: bigfirm.com
Address: 192.168.0.10
```

To correctly configure reverse lookup zones within your network, you need to understand how reverse resolution works. For IPv4, the IP address is in decimal notation rather than octets, as in x.y.w.z. For IPv6, it uses hex numbers and a lot more. Either way, the process is the same. The DNS server that receives the query changes the order of the IP address. So, a query for the FDN for the IP address of x.y.w.z becomes z.w.y.x, with in-addr.arp appended to the end of it. Now the DNS server attempts to resolve the FDN of z.w.y.z.in-addr.arp like a normal FDN. It starts at the top-level domain of arp and works its way down to.

In small enrollments that include only one subnet, the subnet can be represented by a single zone. In our example, the 192.168.0.10 subnet is one, as shown in Figure 6.20. When the reverse lookup zone is created, the New DNS Wizard requests the name of the subnet to create the zone.

In larger enrollments where multiple subnets are in place, the zone, for the higher-precedence octets needs to be created, and lower octets should be represented as subdomains or delegated domains. For example, if a large organization is using the 10.0.0.0 private IP addressing scheme, it would create a reverse lookup zone for the 10.in-addr.arp domain name.

With dynamic updates occurring, subdomains would be automatically created for the next octet 1 to 254, and pointer records would populate the subfolders of the structure. At some point, the subdomains could be delegated to another set of DNS servers, as as domain controllers located in a site that contains these subnets. Then pointer records would be registered in the respective zone that represents the subnet.

# CHAPTER 6 DNS AND NAME RESOLUTION IN WINDOWS SERVER 2012 R2

# FIGURE 6.20
Reverse lookup zone example

![](img/41a83208e6906a3732620203b836cea7_263_0.png)

In Figure 6.21, the 10.in-addr.arp zone was created on BF1. If you wanted the 10.11.0.0 subnets controlled by another server, you would delegate the 11 subdomain. This is delegated to EC1, where the actual subnet of 10.11.12.0 is also represented as a delegated subdomain.

# FIGURE 6.21
Reverse lookup zone for the 10.0.0.0 network

![](img/41a83208e6906a3732620203b836cea7_263_1.png)

# Understanding Record Types

Now that the databases are set up for clients retrieval, you need to add records to the databases. As previously mentioned, Dynamic DNS (DDNS) is a process that allows DNS clients to register their hostnames in an assigned namespace, as DHCP, and this adds the records for the Windows computers within an environment. However, it will be necessary

# INSTALLING DNS

to add some records manually and verify that the correct records were created dynamically. More than 25 record types are available for a DNS zone. In this section, we'll review the most common record types found in a Windows DNS implementation.

# ROUND-ROBIN AND NETMASK ORDERING

On the Advanced tab in the properties of the DNS server, you will find a number of server options enabled, two of which are:

- "Enable round robin"
- "Enable netmask ordering"

**Round-robin** This is a "round-robin" technique to distribute load among multiple servers. The DNS server responds with the IP addresses in a different order for each query, ensuring that the load is distributed.

**Netmask ordering** This is a method to ensure that clients connect to the closest server based on the subnet mask. The DNS server sorts the IP addresses based on the subnet mask, providing the most relevant server to the client first.

# HOST AND POINTER RECORDS

Host (A) and pointer (PTR) records are the most common records you will find in the forward zones and the reverse zones, respectively. The A records list the hostname of the computer and return the IP address. The PTR records list the IP address and return the FDN. You may have to create these for computers that do not have DDNS update.

# ALIAS RECORDS

CNAME records are created to list a secondary name for a computer. This record will list the name and return the assigned computer's FDN. These are useful in the event of replacing the service of a published name that the clients use to access applications or services. Without reconfiguration, clients will still be able to access the alias after replacement.

+   1. In the network adapter TCP/IPv4 properties, change the primary DNS server to the IP address of the primary network connection. For example, if the primary IP address for your server is 192.168.0.1, then this is what you need to change your primary DNS server property to.

When troubleshooting DNS with the nslookup utility, the loopback address (127.0.0.1) causes tests to be "unauthorized". Although this may be cosmetic, we have found results to be a little fickle using the loopback address, so it's best to stick with your primary IP address instead.

+   2. Create the reverse lookup zones in the ForestDNSZones.domain.name application partition.

The reverse lookup zone for subnets may be shared between domain controllers of different domains.

+   3. Create a stub zone for new domain trees on the root DNS server.

A domain tree has a different name than the root DNS server. Since the original DNS server entry is listed as a forwarder like the other domain controller promotions, the DNS server can communicate with the rest of the Active Directory DNS structure. However, there are no automatic configurations on the rest of the Active Directory DNS structure to resolve names in your new namespace. For example, we need to set up a conditional forwarder or a stub zone to point the DNS servers to the new domain controller for Apex.com. In Figure 6.19, you can see a stub zone to assist resolving Apex.com FDNs.

# Understanding SRV Records and Clients

Looking at a brand-spanning-new domain's DNS zone, you will notice that it has a lot of folders or subdomains. Drilling through these folders, you will find service location records by the bootload, as shown earlier in Figure 6.22. As we mentioned, Microsoft served SRV records and Dynamic DNS updates to make Active Directory work. This is the result of the two technologies working together.

The netlogon service needs to create the SRV records within the Active Directory DNS namespace. The sole reason is to ensure computers can find domain controllers in the domain.

Within the Windows operating system processes, the specific services are sought out with the use of the DNS. In Figure 6.22, you will notice a few different services:

+   * _gc, or global catalog: The LDAP service to look up data within the global catalog

+   * _kerberos: The authentication process

+   * _ldap: The LDAP service to look up data within the domain

Each of these services is performed by domain controllers within the domain or forest. In Figure 6.22, you will see DC01.Bigform. perform all of these roles and what TCP port it is listening on.
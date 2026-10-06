
# Chapter 5

# IP Address Management and DHCP Failover

As network environments get more complex and additional networking protocols such as IPv6 start to become commonplace, the ability to centrally manage and deliver high availability of your IP address configurations is essential. Windows Server 2012 has some additional features to address these requirements delivered through IP Address Management (IPAM) and DHCP Failover. These features work with your existing DNS and DHCP deployments to help you track and reduce outages (ultimately headaches) related to IP addressing problems.

In this chapter you will learn to:

- Implement IPAM
- Use IPAM components effectively
- Integrate IPAM with System Center 2012
- Manage IPAM delegation
- Understand DHCP Failover

# IPAM

IP Address Management isn't just a buzz phrase that dictates how you should manage your IP addresses; it's actually a pretty cool (and definitely needed) new feature of Windows Server 2012 that will simplify network complexity through its integration with your existing corporate DNS and DHCP deployments. Microsoft's own words describing IPAM are as follows:

> IPAM is an integrated suite of tools to enable end-to-end planning, deploying, managing and monitoring of your IP address infrastructure, with a rich user experience. IPAM automatically discovers IP infrastructure servers on your network and enables you to manage them from a central interface.

So, if you're reading that description and thinking, “This sounds like a pretty neat feature, but what kind of problems can I expect it to solve for me?” then there are some typical examples of IP address management issues that you might be able to relate to:

- You're trying your best to manually maintain a number of different spreadsheets and custom databases (what you hope is) all of the IP addresses for your network environments.
- You need to uniquely identify a free IP address for a new network computer or device and ensure it gets registered in DNS.
- One of your scopes has reached its maximum limit, and you need to identify and expand it as quickly as possible.
- You have a requirement to track which addresses are in use across multiple locations and subunits, including virtual addresses.
- You want to make a change to a DHCP option that's spread across all of your DHCP scopes, removing old DNS server references or changing the web proxy.
- You're tired of having to open a myriad of DNS and DHCP consoles each time you want to make a change that is applicable across the entire networking environment.

With IPAM, you can reduce the amount of time spent maintaining your existing IPv4 and IPv6 addresses ranges. The more complex your IP address environment is, the more it makes sense to utilize this feature. Furthermore, organizations that have a mixture of physical and virtual networks can now have a unified address-management solution across them.

A nice feature of IPAM is that it will automatically search your network to locate all of your DNS, Domain Controller, and DHCP servers and give you the option to bring them under centralized control or not. If you've deployed the Network Policy Server (NPS) role to any servers in your network, IPAM will not automatically find these, but you can easily add them in manually to bring them under IPAM control. Figure 5.1 shows an example of how IPAM works with your servers to help you customize your address-management designs.

# FIGURE 5.1
IPAM

![](img/41a83208e6906a3732620203b836cea7_211_0.png)

# IPAM Requirements

# WINDOWS SERVER SUPPORT

Because IPAM was introduced with Windows Server 2012, you will need to install it onto a Windows Server 2012 (higher) computer running either Standard or Datacenter edition. Once installed, IPAM will be able to manage only DHCP, DNS, and Domain Controller servers running Windows Server 2008 or higher. This means that if you still have some legacy Windows Server 2003 or Windows Server 2000 computers on your network, you'll have to manage them the old "decentralized"

# ACTIVE DIRECTORY SUPPORT

An IPAM server must be a member of an Active Directory domain; non-domain-joined IPAM server deployments are not supported. The IPAM server can operate only within the confines of a single Active Directory forest, but inside that forest you can have a mix of trusted and untrusted domains that all can be managed by the IPAM server. Also, you can manage only domain-joined servers; any servers that are not members of an Active Directory domain will not be supported with IPAM.

> CAN INSTALL IPAM ONTO A DOMAIN CONTROLLER OR DHCP SERVER?

In short, the answer is no. Even though you will get an error when initializing the IPAM feature, deploying it onto a server with the Active Directory Services Domain Controller role already in place is not supported. When you later attempt to provision the IPAM server after the initial feature deployment, it will cause you no end of problems and ultimately won't work. Similarly, if you deploy IPAM onto a computer with the DHCP server role installed, IPAM discovery of DHCP servers on the network will be disabled.

# DHCP AND DNS SUPPORT

The following support limits are applicable for DHCP and DNS environments managed by IPAM:

- DHCP and DNS servers must be members of an Active Directory domain.
- A single IPAM server can support up to 150 DHCP servers and up to 6,000 DHCP scopes.
- A single IPAM server can support up to 500 DNS servers and up to 150 DNS zones.

# DATABASE SUPPORT

IPAM needs to store all of its configuration and data inside a database. Here's what you need to know about IPAM database support:

- What Microsoft calls "forensics data" is stored in the IPAM database for auditing and tracking purposes up to three years.
- This data is made up of a combination of IP address, MAC addresses, and login/logoff information for up to 100,000 users. That's a lot of data to store, yet strangely enough Microsoft hasn't provided a database purge policy; You, as the IPAM administrator, must purge the database manually as required.
- IPAM in Windows Server 2012 (non-R2) supports only the default Windows Internal Database. No external database is supported.
- IPAM in Windows Server 2012 R2, however, gives you the option to use either the Windows Internal Database or a SQL 2008 R2/SQL 2012 database. The SQL database can be co-located on the same server where IPAM is running, or it can be located externally on a remote computer.

# NETWORKING SUPPORT

It's no-brainer to presume that a healthy IPAM deployment is dependent on a fully functional (IPv4/IPv6) networking environment, but here are a few additional things to be aware of on the networking side:

- There is no support for non-Microsoft network elements (such as NetBIOS Name Service, DHCP relays, or proxies).
- WINS is a legacy Microsoft NetBIOS name-resolution solution and is also not supported by IPAM.
- If you want to use IP utilization trend data from IPAM, then you'll have to make do with IPv4 reporting because IPv6 address utilization trend data is not supported.
- IPv6 address reclaiming is not available; only IPv4 support is available.
- IPAM does not cross-reference its IP address consistency with routers and switches, so be aware of any DHCP services running on these devices.

# IPAM Components

IPAM is made up of three feature components that integrate to deliver holistic management of your IP address infrastructure. These three components deliver functionality around Multi-Server Management and Monitoring, Address Space Management, and Network Auditing. This section will discuss each of these three features in detail to ensure you have a full understanding of the IPAM suite and knowledge of where each piece can fit into your network-management designs.

# Multi-Server Management and Monitoring

The Multi-Server Management and Monitoring feature of IPAM delivers the automated discovery of manageable DHCP and DNS servers and provides centralization of the resources they serve. If you don't want to use the automatic discovery method, you can still choose to

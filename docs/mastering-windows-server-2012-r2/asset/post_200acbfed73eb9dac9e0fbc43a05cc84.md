
# APPENDIX THE BOTTOM LINE

Solution Create a new website, and add the ASP.NET module to the new site. Use a custom TCP/IP port number or header to differentiate the new site from existing sites. Consider configuring a unique application identity for the site to isolate ASP.NET activity during troubleshooting.

Manage IIS 8 with advanced administration techniques. Day-to-day site maintenance and content posting may be the bulk of your IIS 8 administration. But additional higher-level management is what assures consistent and uninterrupted service of your web pages. Important configuring tasks, including recovery from disasters, monitoring performance, setting access or code security, and defining encryption, can be accomplished either locally or remotely.

Master IT Because of limited storage space, you are revising your disaster-recovery plan. You are considering delaying backups of the IIS host.config file to monthly. However, you are concerned that minor global configuration changes throughout the month may get lost if a failure occurs before the monthly backup. How would you recover a mid-month edit?

IIS 8 maintains a configuration of application.config according to the default schedule in the ii_schema.xml file. Previous versions of the file can be restored with the Restore-WebConfiguration PowerShell command. By default, the automatically generated functions of application.config are stored in the history subdirectory under %systemdrive%\netpub.

# Chapter 20: Advanced IP: Routing with Windows

Document the life of an IP packet routed through your network. Understanding how the routing components work inside your hosts and routers will allow you to predict where network traffic will travel through your network. With this understanding comes the ability to troubleshoot issues that are appearing perplex.

Master IT In the New York/London network from Figure 20.1, you will understand the route taken by an IP packet from host A in the New York site to host C in the London site to determine which addresses you should ping in to discover routing issues that are preventing packets from traveling between A and C.

When using the ping tool to track traffic from one host to another, it is important to realize that you are tracking return traffic. If a route is broken, it may be well in the return journey. Having said that, when debugging route issues from system A (New York) to system C (London), you should ping, in the following IP addresses:

- 192.168.0.1—To ensure that IP is configured on host A (New York)
- 192.168.0.100—To ensure that the router is on the network
- 192.169.0.100—To ensure that the router is routing traffic
- 192.169.0.3—To ensure that host B (London) is receiving, and responding to,

# CHAPTER 20: ADVANCED IP: ROUTING WITH WINDOWS

Explain the class-based and classless views of IP routing. When routing with networking professionals, it is important to understand the old class-based terminology to allow for conversations and documentation that may still linger on these terms. Understanding how classless IP routing works is key to avoiding inefficiencies brought by strict adherence to class boundaries in network addressing.

Master It The address 172.24.255.255 lies inside class B, whose default netmask is 255.255.0.0. It also lies in the 172.16/20 RFC 1918 private network range, whose default netmask is 255.255.255.240. Given this information, is the address 172.24.255.255 a host address or a subnet broadcast address?

Solution The information given is insufficient to determine whether 172.24.255.255 is a host or a subnet broadcast address. The default netmask is not relevant; only the netmask that is in use is relevant. If this is a network built by a network designer who was not thinking about subnetting or CIDR, this may very well be treated as a subnet broadcast address. It is more likely, given that RFC 1918 about subnetting this address, that this is a simple host address.

Use NAT devices route TCP traffic. Until we start using IPv6, NAT devices route TCP traffic from our many networked hosts to the outside world, using only a few of increasingly rare IP addresses. Understanding how NAT change the source and destination addresses of packets will allow you to read packet traces and interpret which systems are recipients of data.

Master It A user complains that he tries to connect to an FTP site, the connection succeeds, the first time that listing, his connection is severed, and the server states that it cannot connect to 172.168.0.10. What are likely causes of this problem, and how could this be addressed?

Solution FTP, like other protocols, often includes the IP address of the host in its communication. Whenever an RFC 1918 address such as 192.168.0.1 is seen as part of an error, your first thought should be that there may be a problem with NAT between the two hosts. With FTP, there are a number of possible causes and effects:

- NAT changes the IP address and port in the control channel—the usual cause for it not doing so is the server is running on a port other than 21. If possible, moving the server back to port 21 will allow the NAT to work correctly.
- If the server is on port 21, it is possible that encryption is used on the control channel, using SSL or TLS. In this case NAT cannot see or modify the traffic.
- Many FTP clients allow the user to select "passive mode" for data transfers, in which case the server's IP address needs to pass through NAT, and this may allow for data travel between client and server.
- If this is not possible, the use of a proxy service may be necessary to ensure that connections can flow correctly.

# Chapter 21: Getting from the Office to the Road: VPNs

Add the Network Policy and Services role. The first step to create a VPN server is to add the Network Policy and Services role. Once the role is added, you can take additional steps to configure the VPN server.

Master It You need to add the Network Policy and Services role to create a VPN server. How can you accomplish this?

Solution Launch Server Manager ➤ Local Server Manage menu, choose Roles and Features, and then add the Network Policy and Services role.

Understand the Remote Access role. The Remote Access role includes more than just the ability to create a VPN server.

Master It Name the services within this role (choose three):

- Remote Access Service
- VPN Service
- Routing
- DirectAccess

Solution Remote Access Service, Routing, and DirectAccess are the three that make up the Remote Access role.

Configure a VPN server. You have added the Remote Access role and now want to configure your VPN server to accept connections from clients.

Master It What do you need to configure your VPN server?

Solution Launch Routing and Remote Access by selecting Server Manager ➤ Routing and Remote Access. Right-click the server, and select Configure and Enable Routing. Use the wizard to complete the configuration.

Explore DirectAccess. DirectAccess enables remote users to securely connect back into the corporate environment without the need to use a VPN client.

Master It What client operating systems are supported for Windows Server 2012 R2 DirectAccess?

Solution Only Windows 7 Enterprise and Ultimate and Windows 8 Enterprise are supported operating systems for DirectAccess.

# Chapter 22: Adding More Locations: Sites in Active Directory

Create a site. Site objects are added to Active Directory to represent well-connected physical locations that will host domain controllers. Once a decision has been made to place a DC in a physical location, you need to add a site.

Master It Create a site to represent a new business location in Virginia Beach.

Solution Launch Active Directory Sites and Services. Right-click Sites, and select New Site. Name the site VB, select a site link, and click OK.

Add subnets to sites. Active Directory uses users' subnets to determine which site they are. For this work, subnet objects need to be created and associated with subnets.

Master It Create a subnet to represent the 10.15.0/16 subnet that exists in the Virginia Beach location. Associate the subnet object with the VB site.

Solution Launch Active Directory Sites and Services. Right-click Subnets, and select New Sub. Enter 10.15.0/16 as the prefix, and select the VB site. Click OK.

Configure a site to replicate during certain times. It's often desirable to restrict when replication occurs between sites. If the defaults are used, replication will occur every 180 minutes. If the WAN link is heavily used during certain periods, you can configure the site so it replicates only during certain times.

Master It Configure the Default-First-Site-Name (or other site) to replicate between midnight and 5 a.m.

Solution Launch Active Directory Sites and Services. Right-click the DefaultIPSite link, and select Properties. Click the Change Schedule button. Click Replication Not Available to change the schedule so that replication isn't scheduled. Use your mouse to highlight the 5 a.m. to midnight for all seven days of the week. Click Replication Update, and click OK.

Configure Group Policy for the next nearest site. If a domain controller cannot be reached in a client's site, the client will look for any domain controller without regard how close it is. This can negatively impact logins for enterprises with several locations connected with different WAN links. You can configure Windows Vista (and newer clients) to locate and log on a DC in the next nearest site if a DC can't be located in their site. This can be done using Group Policy or the Registry Editor.

Master It Which of the following Group Policy settings can be manipulated to enable the next nearest site?

- 1. Computer Configuration > Policies > Administrative Templates > System > Logon DC Locator DNS Records
- 2. Computer Configuration > Policies > Administrative Templates > System > Net Logon > DC Locator DNS Records
- 3. User Configuration > Policies > Administrative Templates > System > Logon > DC Locator DNS Records
- 4. User Configuration > Policies > Administrative Templates > System > Net Logon > DC Locator DNS Records

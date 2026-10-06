
# Chapter 6

# DNS and Name Resolution in Windows Server 2012 R2

Computers communicate with each other using IP addresses, whether IPv4 or IPv6. However, it's difficult for most people to remember the IP address for their favorite website or file server. They like using friendly, text-based names. Thus, naming systems are implemented to resolve the friendly names of computers with their assigned IP addresses. The Domain Name System (DNS) is the naming system that Windows Server 2012 R2 servers use. Not only does DNS help users easily identify devices, but many other services such as Active Directory require DNS so that clients and servers can locate and communicate with domain controllers.

In this chapter, you will learn to:

- Explain the fundamental components and processes of DNS
- Configure DNS to support an Active Directory environment
- Manage and troubleshoot DNS resolution for both internal and external networks

## Understanding the DNS Server Role

DNS has been around for decades prior to Microsoft developing its first edition of DNS in Windows NT 4.0. There are many different varieties of DNS implementations that support the required features and define DNS. In this section, we'll cover the concepts of Microsoft's Domain Name System and how it's applied in Windows operating systems.

DNS is implemented within Windows Server 2012 R2 to manage IP address resolution. Once installed on a server, the DNS service will need to communicate with other DNS servers, which is accomplished by using different methods, such as forwarding, root hints, and delegation. The DNS service will also maintain databases, zones, for the internal Active Directory domain or other namespaces. The computers will need to query this DNS service, which you must configure individual computers in order to provide efficient and rapid name resolution.

Windows Server 2012 and previous releases of the Windows operating system offer a built-in DNS Server role. Windows Server 2012 R2 is compatible with older versions of DNS going back to Windows Server 2003, however, versions earlier than Windows Server 2008 do not support IPv6 and are functional only with IPv4 addresses.

# CHAPTER 6 DNS AND NAME RESOLUTION IN WINDOWS SERVER 2012 R2

The following is a short summary of the DNS fundamental concepts referred to in this chapter:

**Hostname** This is the (friendly) name of a computer. According to DNS standards, it can be up to 255 characters in length. It is equivalent to a computer's first name, for example, EC01.

**Namespace** This is the name of domain, not specifically an Active Directory domain though. It's a logical set of hosts signified by a name controlled by a set of name servers. This is equivalent to a computer's last name; they're all part of the same family. For example, Bigform.com is the namespace for hosts in the Bigform domain.

**Fully Qualified Domain** The FQDN is the hostname appended to the domain's namespace, such as EC01.Bigform.com.

**HOSTS File** This is a file that statically maps hostnames to IP addresses. This file is located in c:\windows\system32\drivers\etc for standard Windows Server 2012 R2 installations and can be used as an entry-level alternative to a DNS server for name resolution in small environments. Don't try to manage a large enterprise environment with static HOSTS file entries, though it will quickly turn into an administrative nightmare!

**Name Server** This is a DNS server that will resolve FQDNs to IP addresses. Name servers also control namespaces for specified domains. They will resolve requests for namespace from DNS clients throughout the network.

**Hierarchical Naming Structure** The namespace is created so that the left part of a name is start at the right side of the name as shown in the FQDN. With this, the naming servers can direct to the correct naming server for a given namespace. For example, as shown in Figure 6.1, Ec01.Bigform.com is the FQDN for a server in the East.Bigform.com domain. This domain is actually a subset, a subdomain, under the control of the Bigform.com domain. You can say the same about Bigform for the .com top-level domain name. The strength is that you can ask for the .com name server where the Bigform.com name server is. You can do that for the East.Bigform.com server, the FQDN name directs the query to the right name server through a process named recursion.

# **FIGURE 6.1** Hierarchical DNS naming

![](img/41a83208e6906a3732620203b836cea7_247_0.png)

Recursion This is a server-directed process to resolve a FQDN. If the server cannot resolve the FQDN with its own information, it will send the query to other name servers. The recursion processes root servers and domain name servers. Root servers are the top of the hierarchcial structure. The root servers list the name servers that control the top-level domain names such as .com, .gov, and edu. The top-level domain servers control the registry of subdomains are registered beneath the .com domain servers. For example, name servers for the Sybex subdomain are registered on the .com domain servers. When a query occurs, the following occurs (as shown in Figure 6.2):

1. The DNS client requests a name, like www.Sybex.com, from its DNS server.
2. Through the recursive process, the DNS server queries the root servers for the .com domain servers.
3. The root servers give a list of name servers for the .com domain.
4. Then the DNS server queries the .com name servers for Sybex.com.
5. It receives another list of name servers for the Sybex.com domain.
6. It queries the provided name servers for the www.Sybex.com FQDN.
7. The Sybex.com DNS server cough up the IP address of the www server to the DNS.
8. The DNS server passes the IP address to the client.
9. Armed with the IP address, the client connects with the web server www.Sybex.com.

# FIGURE 6.2
DNS recursion process

![](img/41a83208e6906a3732620203b836cea7_248_0.png)

# CHAPTER 6 DNS AND NAME RESOLUTION IN WINDOWS SERVER 2012 R2

Delegation This allowing another name server to control a subdomain of a namespace. For example, the Bigfirm.com name servers can delegate control of the East.Bigfirm.com namespace to another server.

Forwarding This is an alternative to the recursion process. Forwarding is a lateral request to another server. The forwarding server obtains a response and relays it to the originating server.

Iteration This is a client-directed request to resolve an FQDN. If the client receives a negative request from a name server, it will query another server.

NetBIOS Naming System This legacy naming system was used primarily within Microsoft NT 4.0 networks. Its processes are part of modern-day Windows operating systems, particularly when using non-domain (workgroup)-computers.

Service records (SRV) are records that map a service to a hostname. This is an essential part of DNS supporting Active Directory.

Dynamic Update Dynamic DNS (DDNS) is a process that allows DNS clients to register their hosts in an assigned namespace such as DHCP. This reduces the need of admins to manually enter records in the name server databases. This is another essential part of DNS supporting Active Directory.

## Installing DNS

DNS for Windows Server 2012 R2 can be deployed into several configurations depending on your scenario. You can choose to install a stand-alone DNS server onto a nondomain-joined computer, or deploy it onto your domain-joined member servers or Active Directory domain controllers. Whatever the scenario, the Installing role is simple. This section will first explain what you need to do to manually deploy DNS onto a nondomain-joined computer. Later, we will explain how to automatically configure DNS to integrate with Active Directory as to ensure name resolution smoothly within your environment.

## Configuring a Stand-Alone DNS Server

First things you will need to allocate a static IP address to the server that you want to install the DNS role onto, since making a moving target is tough for clients! From the desktop, if you press Ctrl+R and type ncpa.cpl and hit Enter, you will be brought to the Network Connections window. Here, you can click-right your adapter and then Properties to open the configuration. If you double-click Internet Protocol Version 4 (TCP/IPv4), you will be presented with the TCP/IPv4 dialog box. Once there, you then assign a static IP address, as shown in Figure 6.3.

When you have assigned a static IP address, you should also add the primary suffix, such as Bigfirm.com, in the Advanced TCP/IPv4 Settings box, as shown in Figure 6.4.

We use the word here because it isn't always necessary to add a primary DNS suffix. The primary suffix is modified automatically when the computer joins a domain. If the server is going to operate as part of a workgroup (as is the case in our example here), you will need to add it so that other DNS servers can locate it in the DNS structure.

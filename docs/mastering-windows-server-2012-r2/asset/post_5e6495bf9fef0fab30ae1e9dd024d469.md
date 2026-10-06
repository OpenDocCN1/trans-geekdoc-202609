
## CHAPTER 6 DNS AND NAME RESOLUTION IN WINDOWS SERVER 2012 R2

- * Broadcast only: “b-node,” 1
- * Contact WINS only: “p-node,” 2
- * Broadcast first and then contact WINS: “m-node,” 4
- * Contact WINS and then broadcast: “h-node,” 8

FIGURE 6.25 The WINS tab

![](img/41a83208e6906a3732620203b836cea7_271_0.png)

H-node is best for a network relying on NetBIOS because NetBIOS reduces the chatter in a WINS-supported environment. If no DNS server is enabled, the computer can get at least some answer in a subnet, such as at home or in a workgroup. If DHCP is not configured with this, the operating system's default configuration takes you to h-node, or hybrid mode.

It would be best for Active Directories to disable NetBIOS because it reduces the extra traffic and processes. It also reduces security threats such as bots searching networks for computers to attack your naming server. Before doing this, you'd need to ensure that DNS name resolution is accurate.

You can find client configurations on the DNS tab of the network properties, which is displayed in Figure 6.26. The obvious need is the DNS server's IP address. It should be connecting to the nearest server, your primary domain controller in its local site. A secondary DNS server is recommended.

The middle portion of the tab deals with unqualified names. A hostname is without a “last name,” (such as BFS listed in the ping example). The DNS server needs a FQDN, so the DNS client appends suffixes, the “last name,” before sending the request. The primary DNS suffix is listed in the System control panel (My Properties) under the Computer Name tab. This is managed automatically by the operating system when the computer joins the domain; you shouldn't need to mess with it. Additional suffixes may be necessary in larger environments, but in single-domain environments, the default settings work. In only rare occasions would you consider adding a DNS suffix.

## FIGURE 6.26
DNS tab

![](img/41a83208e6906a3732620203b836cea7_272_0.png)

The following three settings are applied to all connections with TCP/IP enabled. For resolution of unqualified addresses:
- Append primary and connection specific DNS suffixes
- Append parent suffixes of the primary DNS suffix (in order).

All of this is most important if FQDNs are used regularly. When applications are configured, use FQDNs. When connecting home or folder redirection, use FQDNs. When writing scripts to map network drives, use DNS. Get the point? On top of this, DNS bypasses the NetBIOS protocols. Applications can tell the difference between NetBIOS and DNS and will resort to DNS when they recognize a FQDN.

## Updating DNS DYNAMICALLY

To make the DNS name-resolution process airtight, you will need to have all of the computers listed in DNS zones. In the past, DNS became a full-time job for system admins because they had to manually enter the ever-growing number of records for their network. To reduce the work for system admins, Microsoft sought a dynamic solution through developing NT and then switched to DNS when the Dynamic DNS (DDNS) update protocol was available. The process is pretty simple:

1. The client queries the SOA record for its DNS suffix namespace. This will tell it that the server can accept DDNS. It also does for the reverse lookup zone that its IP address is associated with.
2. The client makes the DDNS request to the server.

On standard zones' Start of Authority records, the primary server is listed. On Active Directory integrated zones, the domain controller receiving the request modifies the SOA response with its name. Since it can change the Active Directory database, there's no need to hunt down a domain controller located elsewhere. If the update process fails, it can attempt to find other name servers to perform the update.

## CHAPTER 6 DNS AND NAME RESOLUTION IN WINDOWS SERVER 2022 B2

The only configuration on the DNS tab for DDNS that you can make is to check two boxes on the bottom, as shown in Figure 6.2c. You can register the name with the primary DNS suffix or with the connection suffix. The latter check box is deselected by default.

The silly part is that this DNS client service doesn't perform the DDNS process. The DHCP client service does. This reminds us of an eventful day when one of us disabled the DHCP client service on a domain controller. This doesn't need the service running; it has a static IP address... As already mentioned, the DDNS process is used by the domain controllers to list the SRV records for Active Directory. Eventually, the clients couldn't find the domain controller there were no SRV records for it. Oh, joy! Fortunately, this was in a lab.

There are two locations that manage the DDNS process: the zone for a namespace and the DHCP server.

The DNS zone can be enabled for DDNS updates in the New Zone Wizard or be modified in the properties of the zone. Figure 6.27 shows the options for DDNS. The options are secure only, both and secure, and disabled. Secure dynamic updates means the DNS client has authenticated with the domain controller prior to the update. Nonsecure means the update is accepted without authentication. Given the name, you can safely assume that hackers exploit this option. Disabled prevents any DDNS updates from occurring.

## FIGURE 6.27 Dynamic DNS update options

![](img/41a83208e6906a3732620203b836cea7_273_0.png)

The DHCP server can also participate in the DDNS process. In earlier versions of Windows Server, there were plenty of clients that didn't have DDNS capabilities. To resolve this, the DHCP server would identify these OSs and perform the updates for them. Figure 6.28 shows the DNS tab of IPv4 properties within the DHCP server.

The default settings are displayed, and these will be rarely modified. Essentially, DHCP is not performing any updates because clients are doing it themselves. It performs a cleanup when lease expires, which is just a check box reached by clicking the Configuration button, basically prevents DHCP from updating an existing record.

## FIGURE 6.28
DDNS options on DHCP

![](img/41a83208e6906a3732620203b836cea7_274_0.png)

## UNDERSTANDING Active Directory’s DNS

Microsoft has integrated DNS and Active Directory so tightly together that it's difficult to discuss the two separately. When an Active Directory environment is created with Windows Server 2012 R2, the Active Directory installation process automatically configures DNS while adding the role. This provides a hands-off capability for the IT generalist setting up DNS.

In the following sections, we'll cover how the Active Directory configures DNS and uses it to support clients. For a more detailed discussion of the Active Directory terms and concepts, refer to Chapter 7.

### Configuring DNS Automatically

Windows Server 2012 R2 offers two ways of installing the DNS server: on its own (as you've seen in the stand-alone non-domain configuration) or adding the Active Directory Domain Services role. When you opt for the latter, you must run the Active Directory Installation Wizard, which performs a number of configurations for the Active Directory Domain Services role, including automatically configuring and integrating the DNS. In Chapter 7, we will walk you through the Active Directory installation process in detail, but here we take a look at what happens regarding the DNS.

First, you must understand the prerequisite for the Active Directory installation process. The prospective domain controller needs to have connectivity to the existing Active Directory DNS structure. Otherwise, it won't be able to connect to the domain controllers and obtain the necessary information. The IP configurations must list a DNS server within the Active Directory environment, preferably the root's DNS server or a DNS server in the same domain you are about to join. The only exception to this is when you create the first

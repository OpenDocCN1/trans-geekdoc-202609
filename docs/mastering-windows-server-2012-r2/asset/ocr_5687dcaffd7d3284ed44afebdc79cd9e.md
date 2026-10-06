# FIGURE 6.26
DNS tab

![](bbox=[0.316, 0.107, 0.638, 0.412])

The following three settings are applied to all connections with TCP/IP enabled. For resolution of unqualified addresses
* Append primary and connection specific DNS suffixes
* Append parent suffixes of the primary DNS suffix (in order).

All of this is most if FQDNs are used regularly. When applications are configured, use FQDNs. When connecting home or folder redirection, use FQDNs. When writing scripts to map network drives, use DNS. Get the point? On top of this, DNS bypasses the NetBIOS protocols. Applications can tell the difference between NetBIOS DNS and will resort to DNS when they recognize a FQDN.

# Updating DNS DYNAMICALLY

To make the DNS name-resolution process airtight, you will need to have all of the computers listed in DNS zones. In the past, DNS became a full-time job for system admins because they had to manually enter the ever-growing number of records for their network. To reduce the work for system admins, Microsoft sought a dynamic solution through developing NT and then switched to DNS when the Dynamic DNS (DDNS) update protocol was available. The process is pretty simple:

+   1. The client queries the SOA record for its DNS suffix namespace. This will tell it that server can accept DDNS. It also does for the reverse lookup zone that its IP address is associated with.
2. The client makes the DDNS request to server.

On standard zones' Start of Authority records, the primary server is listed. On Active Directory integrated zones, the domain controller receiving the request modifies the SOA response with its name. Since it can change the Active Directory database, there's no need to hunt down a domain controller located elsewhere. If the update process fails, it can attempt to find other name servers to perform the update.
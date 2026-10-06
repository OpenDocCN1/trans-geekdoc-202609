# CHAPTER 5 IP ADDRESS MANAGEMENT AND DHCP FAILOVER

# TABLE 5.2: Common IPAM Issues

| ISSUE | SUGGESTED RESOLUTIONS |
| Can't connect to the IPAM server | - Confirm that the account you're using has the relevant permissions to access the IPAM console.<br>- Ensure that the Windows Internal Database service is running on your IPAM server.<br>- Ensure that the Windows Process Activation service is running on your IPAM server. |
| Unable to fetch data from a managed server | - Ensure that the access status for your server is Unlocked or Not Applicable for DHCP RPC and Audit Share Access Status, DNS RPC Access Status, and Event Log Status.<br>- Confirm that your firewall is not blocking IPAM for any servers listed with a status of Blocked.<br>- Follow the instructions in the Configure IPAM Provisioning section earlier to ensure you have provided the server correctly. |
| Cannot discover DNS or DHCP servers | - If DNS server is not co-located with a domain controller, make sure that you have registered your DNS server as a name for the domain zone and that you have also registered your DNS suffix for the domain. Also ensure that the DNS server is running on the server.<br>- If your DHCP server can't be discovered, check if that particular DHCP server has been authorized to operate in the domain and ensure that the DHCP server is up and running on it. |
| Not Reachable state shown for a managed server | - Confirm that you can communicate with the particular server and that no firewall or other variable is blocking access to it.<br>- Confirm that the DNS or DHCP server is up and running on the server.<br>- Confirm that the server has been properly corrected, and if required, repeat the steps in the Configure IPAM Provisioning section earlier. |

# DHCP Failover

The Dynamic Host Configuration Protocol (DHCP) is responsible for automatically assigning IP addresses from specified address pools (scopes) to any network-connected devices that need to be identified. It has been an integral part of networking environments for years, and without it, you would need to maintain your own manual list of IP addresses. In any kind of reasonably sized environment, this would be an administrative nightmare.

A Caveat of traditional Windows Server DHCP implementations, though, was the fact that providing redundancy or high availability (HA) for this critical service wasn't always straightforward as it should be.
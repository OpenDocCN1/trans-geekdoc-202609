# Create virtual network

+   Basics Security IP addresses Tags Review + create

Define the address space of your virtual network with one or more IPv4 or IPv6 address ranges. Create subnets to segment the virtual network address space into smaller ranges for use by your applications. When you deploy resources into a subnet, Azure assigns the resource an IP address from the subnet. Learn more >

| Subnets | IP address range | Size | NAT gateway |
| :--- | :--- | :--- | :--- |
| edgateway | 10.10.8.0 - 10.10.8.255 | /24 (256 addresses) | - |
| AzureFirewallSubnet | 10.10.10.0 - 10.10.10.63 | /26 (64 addresses) | - |
| AzureFirewallManagement! | 10.10.10.64 - 10.10.10.127 | /26 (64 addresses) | - |

# Figure 10.8: Azure Create Virtual Network IP Address Form

# Tags:
perform simultaneous updates to all of your DHCP and DNS servers, this is where that functionality stems from.

**Integrate IPAM with System Center 2012.** With all the focus on datacenter and cloud management, it’s that Microsoft has invested the most in enhancing IPAM for Windows Server 2012 R2. The Virtualized IP Address Space of the IPAM console streamlines the management of your physical and virtual addresses through a new integration with VMM. This integration opens up IP address-management capabilities between your on-premise and cloud-based IP address schemes.

**Master It** What version of Windows Server 2012 R2 do you need to be running IPAM integration?

**Solution** You need to be running Windows Server 2012 R2 with System Center 2012 R2 Virtual Machine Manager if you want to use the IPAM feature to manage your physical and virtual addresses seamlessly.

**Manage IPAM delegation.** When you install the IPAM server, the installation process automatically creates a number of local security groups that can be used to deliver Role-Based Access Control of your IPAM environment to designated users and administrators. Depending on the type of administrative privileges you want your users to have, all do you need to do to add their accounts to the appropriate security group.

**Master It** There are five local security groups that IPAM creates to deliver RBAC. Which group from the following list is not one of them? (Choose one)

+   a. IPAM Administrators

+   b. IPAM IP Audit Administrators

+   c. IPAM ISM Administrators

+   d. IPAM Advanced Users

+   e. IPAM MSM Administrators

+   f. IPAM Users

e) The IPAM Advanced Users group is not one of the five local security groups created by IPAM for RBAC and access delegation.

**Understand DHCP Failover.** The beauty of DHCP Failover is that there is no need for any shared storage, such as a Storage Area Network device, between your DHCP servers. The IP address lease data is replicated between each server continuously. With both DHCP Failover servers containing a copy of the latest IP address assignment and scope information, you will always be able to sustain a failure of one DHCP server without losing any functionality.

**Master It** The new DHCP Failover functionality allows you to configure two types of failover relationships. What are these relationships called? (Choose two.)

+   a. Failover clustering (active/active)

+   b. Hot standby (active/passive)
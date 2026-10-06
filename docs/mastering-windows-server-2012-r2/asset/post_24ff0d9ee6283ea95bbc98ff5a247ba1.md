
# IPAM 179

add or remove your DHCP and DNS servers manually. The ability to perform simultaneous updates to all of your DHCP and DNS servers at once stems from this feature.

This feature also provides monitoring functionality that can check the availability of your DHCP scopes and DNS zones.

# ADDRESS SPACE MANAGEMENT

The Address Space Management (ASM) feature of IPAM delivers full transparency of your IP address infrastructure from a single centralized console. It includes a neat reporting function that allows you to track IPv4 address utilization trends and provide the data in easy-consume reports. Using ASM to ensure better planning, accountability, and control on your network can be the real difference between being proactive (fixing the problem before it happens) or reactive (learning about the problem after it happens) to IP addressing problems.

You can use IPAM to detect overlapping IP ranges or scopes that have been configured differently across DHCP servers, as well as DNS and DHCP entries and locate any free IP addresses within a range. Figure 5.2 shows an IP address utilization trend over one-month period.

![](img/41a83208e6906a3732620203b836cea7_214_0.png)

# NETWORK AUDITING

The Network Auditing feature of IPAM dives into the Windows event logs for your DHCP servers and provides you a full view of all DHCP configuration changes that have occurred in the environment. It correlates data from the IPAM database, DHCP server lease-logs, and your DC and NPS security logs to surface tracking information on users, devices, and IP addresses. With this type of data readily available and fully searchable, you can then run reports on the fly to help identify any configuration issues.

# Topology Deployment Options

You have three topology design options to choose when deploying IPAM to manage an IP address state that spreads across multiple physical and logical environments. These types of configurations are categorized and defined in Table 5.1.

# CHAPTER 5 IP ADDRESS MANAGEMENT AND DHCP FAILOVER

# TABLE 5-1: IPAM Topologies

| TOPOLOGY | DEFINITION |
| --- | --- |
| Centralized | One IPAM server in a central location to manage everything. |
| Distributed | An IPAM server deployed to each site in the enterprise. The information on each IPAM server will be isolated to each site with out-of-box replication or syncing of data between the different IPAM servers in the enterprise. |
| Hybrid | This design utilizes a mixture of both the centralized and distributed models and has a central IPAM server deployed along a number of distributed IPAM servers on different sites. |

# IPAM Installation

Now that you have an understanding of what IPAM is, we can walk through the installation steps. In this section presume that you have either an existing IP address infrastructure (DC, DNS, DHCP, and the like) to manage or that you have at least followed the steps outlined in this book to build and configure a lab or test network (we are using the Bigfirm.com domain for our sample environment here) that you can deploy IPAM into. Here are the high-level steps required to get it deployed:

- 1. Install the IPAM Server feature with the Add Roles and Features Wizard.
- 2. Configure IPAM provisioning either manually or by using Group Policy.
- 3. Configure DHCP and DNS server discoveries across your domain(s).
- 4. Run discovery of your DHCP and DNS servers.
- 5. Choose discovered servers to be managed.
- 6. Retrieve data from your managed DHCP and DNS servers.
- 7. Install the IPAM client on additional computers.

# Installing the IPAM Server Feature

In this section, we will walk through the installation of the IPAM feature:

- 1. To begin, log on your domain-joined Windows Server 2012 R2 with an account that has domain administrative permissions, and from the Server Manager > Local Server > Manage menu, choose Add Roles and Features option.
- 2. In the Before You Begin dialog box, click Next.
- 3. Ensure that Role-based or Feature-based Installation is selected in the Select Installation dialog box; click Next.
- 4. Under Select Destination Server, leave the default option of “Select a Server from the Server Pool” checked, confirm that your server is highlighted in the Server Pool, and then click Next to continue.
- 5. Don't choose any of the options from the Select Server Roles dialog box; just click Next here to move on.
- 6. When you reach the Select Features dialog box, scroll down until you find the IP Address Management (IPAM) Server option from the Features list and check the box beside it, as shown in Figure 5.3. You'll be prompted to add some required features here, such as the Group Policy Management console and the Windows Internal Database, so just click the Add Features button in the window that pops up. Click Next to continue.

# FIGURE 5-3
Choosing the feature

![](img/41a83208e6906a3732620203b836cea7_216_0.png)

- 7. When you see the Confirm Installation Selections dialog box, review your selection and then click the Install button to start the installation of IPAM.
- 8. When the installation is complete, click the Close button to finish off the wizard.

# INSTALLING IPAM with PowerShellShell

You can install the IPAM server feature using PowerShell by following these simple steps:

- 1. Opens a Windows PowerShell prompt with elevated permissions by right-clicking the shortcut and choosing the Run As Administrator option. Then enter your admin credentials as required.
- 2. Type the following command into PowerShell and then press Enter:

```
Install-WindowsFeature IPAM -IncludeManagementTools
```

# Installing the IPAM Client Feature

The IPAM client is essentially the same IPAM console that you get when you install the IPAM server feature, but it's installed on a computer that is not your IPAM server. To deploy the IPAM client to another server than your primary IPAM server, you need to deploy the Remote Server Administration Tools (RSAT). Follow these steps on a Windows Server 2012 or higher computer to deploy the client:

- 1. To begin, log on your domain-joined Windows Server 2012 installation with an account that has domain administrative permissions, and from the Server Manager > Manage menu, choose the Add Roles and Features option.
- 2. In the Before You begin dialog, click Next.
- 3. Ensure that Role-based or Feature-based Installation is selected at the Select Installation dialog box, click Next.
- 4. Under Select Destination Server, leave the default option of “Select a Server from the Server Pool”, confirm, that your server is highlighted in the Server Pool section, and then click Next.
- 5. Don't choose any of the options from the Select Roles dialog box; click Next to move on.
- 6. When you reach the Select Features dialog box, expand Server Administration Tools and expand Feature Administration Tools.
- 7. Check the IP Address Management (IPAM) Client box, click Next.
- 8. If you're prompted to add some required features here, such as the Group Policy console and the Windows Internal Database, click the Add Features button from the window that pops up Click Next to continue.
- 9. When you see the Confirm Installations dialog box, review your selection choices, and click the Install button to start the installation of the IPAM client.
- 10. After the client installation is complete, click the Close button to exit the wizard.

# Configure IPAM Provisioning

Once you have the IPAM feature deployed, you'll need to provide your IP address infrastructure for management. As mentioned earlier, there are two methods of provisioning IPAM: manually or through use of Active Directory Group Policy. To make things easy (and for the sake of your sanity), we'll focus on the Group Policy provisioning method. For obvious reasons, if you want to work through this process, you will need to have an Active Directory environment deployed. If you haven't configured your lab with Active Directory yet, then work through the tasks in Chapter 7 and come back to this later.

- 1. To begin, on the server where you deployed the IPAM server feature, open Server Manager and notice that you have an option for IPAM in the navigation bar on the left, as shown in Figure 5.4.

Clicking the IPAM link from inside Server Manager opens the IPAM Overview console, which will be your main focal point for managing IPAM. Here you can choose from three options: Quick Start, Actions, or Learn More.

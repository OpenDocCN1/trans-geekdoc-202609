Health Registration Authority Health Registration Authority (HRA) is part of NAP and is used to issue health certificates for the IPSec enforcement. If the client passes the health policy verification performed by NPS, the HRA will issue a bill of health in the form of a health certificate.

Host Credential Authorization Protocol Host Credential Authorization Protocol (HCAP) is used to integrate Microsoft's NAP solution with Cisco's Network Access Server.

# ### Is This A REQUIREMENT IF WE JUST WANT VPN?


Although it's not a prerequisite to deploy the Network Policy and Access Services role to create your VPNs, there's definitive advantage to having this role installed alone the Remote Access to deliver the service and general network access that most organizations require with their VPNs. It's worth noting that by default, all user accounts in Active Directory have been configured to control their dial-in through the use of NPS Network Policy regardless of whether the role has been deployed or not.

# ## Installing the Network Policy and Access Services Role

Before starting, we'll presume that you have an environment with at least one Windows Server 2012 R2 domain controller, a member server, and a Windows 8 client. Check out the earlier chapters in this book if you need assistance in setting up these servers before you attempt to deploy your remote access.

+   1. To begin, log on to your domain-joined Windows Server 2012 R2 installation with an account that has domain administrative permissions, and from the Server Manager manage menu, choose the Add Roles and Features options.
2. In the “Before you begin” dialog box, click Next.
3. Ensure that “Role-based or Feature-Based Installation” is selected in the Selection Installation type dialog box; then click Next.
4. In the Select Server dialog box, leave the default option of “Select a Server from the Server Pool” confirmed, that your server is highlighted in the Server Pool section, and then click Next to continue.
5. When you reach the Select Server dialog box, scroll down until you find the Network Policy and Access Services options in the Roles list, and check the box beside it.
6. You'll be prompted to add some required features here, such as the Remote Server Administration Tools (RSAT), just click the Add Features button in the window that pops up.
7. Click Next again to continue.
8. Leave the features as they are in the Select Features dialog box; then click Next twice.

When you reach the Select Role Services dialog box, you will be presented with three options to choose from the Role Services pane, as shown in Figure 21.3.
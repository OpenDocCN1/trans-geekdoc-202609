# WINDOWS RT AND ACCESSING RESOURCES

Windows RT is a different type of operating system than Windows 8, but it carries many of the same feature sets and access capabilities. While you cannot join an Active Directory domain, as stated earlier, you can access resources on the network.

Microsoft's System Center Configuration Manager 2012 SP1 supports the management and configuration of Windows devices through its advanced mobile device management (MDM) configurations.

The more common way of accessing resources is via Windows File Explorer, you can use this tool to manage files and folders as you can on the non-RT OSs. Through File Explorer you can map your network devices, access shares, and ever storage devices. To access the network, Windows RT fully supports many connection types the same way as Windows 8 does. Following are a few examples of accessing resources:

+   Wireless Networks You must manually set the connection and configurations on networks, having the appropriate SSID, connection accounts, and security details for that connection is imperative. Depending on your organization's security practices, you may have only limited access to resources in your environment.

+   Wired Networks Many manufacturers provide an Ethernet port. Most organizations use DHCP, so you will not need to configure your network. If you need to configure an IP address and subnet, you can do so following the same steps you did for Windows 8 via Control Panel.

+   Proxy Servers Since no policies are applied because of the lack of domain joining, you have to manually configure your proxy settings. If you need to detect of an internal proxy server you must use the Web Autodiscovery Protocol on your network. This involves configuring specific DHCP options as well as a web server, but as people move to bring-own-device (BYOD) scenarios, you might consider this as an option.

+   VPN Connectivity Windows RT devices can utilize VPN connections to establish a more-connected feel to your organization's network. Many IT pros like to utilize this option because it helps with security and access control. Since many VPN options are available for Windows RT, you should review the RT VPN overview provided by Microsoft at http://tinyurl.com/c18tVPN

# JOINING THE OFFLINE DOMAIN WITH DJJOIN

Domain joining offline: what if you can't get to the domain controller to create the computer account or you can't write to it? You may not be able to contact a domain controller if you are joining a group of client computers before deploying or installing a client while offline.

Introduced in Windows 7 and available still in Windows 8 and Windows Server 2012 is the djoin utility, which joins you computer to a domain when the client computer can't communicate with the domain controller.

This section will show you how to use djoin.exe to join a new Windows 8 client computer (WIN8CLIENT)

In a nutshell, djoin.exe provides a computer account in AD and then exports the data (called a blob, which is needed for the computer with computer name to join the domain) to a text file. The offline computer imports the blob and joins the domain.
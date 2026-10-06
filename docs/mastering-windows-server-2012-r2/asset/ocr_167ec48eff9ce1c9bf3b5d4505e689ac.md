# AN INTRODUCTION AND ACTIVE DIRECTORY BASICS

+   1. Log onto the server using an account with local administrator privileges.

+   2. If you have not already done so, install the Active Directory Services role. Open Server Manager and choose Manage/Add Roles and Features. Then follow the wizard as you did for the first domain controller.

Alternatively, you could open a PowerShell command prompt and run the following cmdlet; this will install the same features as running the wizard:

```
Add-WindowsFeature AD-Domain-Services,RSAT-AD-AdminCenter,RSAT-ADS-Tools,GPMC
```

+   3. In Server Manager click the exclamation mark and click "Promote this server to a domain controller."

If the yellow exclamation mark did not appear after running the PowerShell command, click the refresh in Server Manager.

+   4. On the first Deployment Configuration page, select "Add a domain controller to an existing domain." Specify the domain name and provide domain administrator credentials for bigfirm.com. If the account you used to log onto the server isn't a member of the Domain Administrators group in the target domain, you will also need to enter alternate credentials. Next.

# AD PROBLEMS? CHECK DNS!

If you receive an error indicating that a domain controller for the domain can't be contacted, double-check the spelling of the domain name and then check DNS is running on the DNS server. Ensure your system is configured to use this DNS server. A simple check is to ping the domain name. For example, if your domain name is bigfirm.com, you typing bigfirm.com and should receive four replies. If you don't receive any, it is a clear indication that you are not reaching DNS (check your TCP/IP and firewall settings) or DNS is not functioning.

+   5. On the Domain Controller Options page, select both "Domain Name System (DNS server)\ and Global Catalog (GC), as shown in Figure 7.15. Make sure Default-First-Site is selected. You also need to enter a DSRM password. A good practice would be to choose the same password for your second DC as you did for your first DC. Click Next.

+   6. If a DNS delegation warning appears, click Next.

+   7. On the Additional Options page, you could specify to install Active Directory from media.

You could use NTDSUtil to create installation media from a current Active Directory database. NTDSUtil will create a kind of point-in-time snapshot that then provides you as input for this wizard. The advantage is that you only need to replicate the differences for the time after the snapshot. This feature is very useful if you have a slow WAN link and you don't want to replicate the entire Active Directory database over this slow net.
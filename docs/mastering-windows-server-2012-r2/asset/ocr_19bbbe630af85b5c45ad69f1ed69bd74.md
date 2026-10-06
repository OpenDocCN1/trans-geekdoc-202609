# CHAPTER 5 IP ADDRESS MANAGEMENT AND DHCP FAILOVER

Microsoft has released the Windows Server Migration Tools to help you with this process, and
You can get more information on here: http://tinyurl.com/ws2012migtools.
Also, you cannot create a DHCP Failover configuration with more than two computers
as the replication process can occur only between two points.

# DOMAIN MEMBERSHIP SUPPORT
As is the case with stand-alone DHCP, you can deploy DHCP Failover onto either domain-joined
or workgroup computers. In a domain-joined environment, DHCP Failover can be installed onto
DHCP servers that are running on either Domain Controller or Domain Member servers.

# Installing DHCP Failover
Once you've got the prerequisites, you're ready to start with the DHCP Failover
installation. In this section, we presume you've already deployed the DHCP server role to
two Windows Server 2012 R2 computers and have configured and activated an address scope
one of the two DHCP servers.
Ensure you don't have the same scope configured on both servers if you do,
You will get an error during setup stating that the scope on the server failover needs to be
deleted before continuing.

# SYNCHRONIZE YOUR SERVER CLOCKS
A gotcha that you might come across when installing DHCP Failover is that the time between the
servers must be kept within one minute of each other. If it creeps out just one
minute during the installation process, you will be greeted with a critical error telling you to go
back and get your servers in sync before going any further. You can use something like Active
Directory or the Network Time Protocol (NTP) to ensure all is in order.

+   1. Log on to your first Windows Server 2012 R2 computer (we'll use BF1.Bigfirm.com for our
example) with an account that has administrative permissions, and launch the DHCP
 console MMC snap-in from the Server Manager > DHCP menu or from\within the IPAM console, as discussed earlier.
2. Right-click the scope you want to create a DHCP Failover relationship for, and then
Choose Failover, as shown in Figure 5.29.
3. In the Introduction to the DHCP Failover dialog box, ensure your server is selected in
the Available Scopes section, and click Next.
4. In the Specify Partner Server To For Failover box, click the Add Server
button and choose your second server (we've use BF2.Bigfirm.com as an example here)
from the list of authorized DHCP servers, click OK, and then click Next.
5. As shown in Figure 5.30, configure your options for the new failover relationship and
then click Next. These options are as follows:
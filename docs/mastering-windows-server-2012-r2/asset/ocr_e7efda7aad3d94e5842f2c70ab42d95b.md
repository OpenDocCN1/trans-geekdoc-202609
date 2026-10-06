Subnet Mask This is the subnetwork to which the node belongs.

Default Gateway This is the router that will route traffic between your assigned subnet and other subnets and networks.

DNS Servers DNS resolve IP addresses to computer names. You need to have a DNS server assigned, or you will not be able to join a domain. In most cases, the DNS server address is supplied by the DHCP server.

If the ifconfig results come empty, then you may not have a DHCP server to allocate addresses, in which case you will need to configure your local area connection settings manually. To do this, you will need to open the local area connection associated with the NIC and enter the information by hand. For now, assume that the ifconfig results show that the NIC has the address assignment handled.

# Testing Network Connectivity with the ping Command

To absolutely ensure that your network and TCP/IP are working properly and the IP information is correct, open a command prompt, and use the ping command to test basic network connectivity.

If you are unfamiliar with ping, you can review the command and all the switches here: http://tinyurl.com/c18pingCommand.

Here are typical ping commands that you can use to test network connectivity:

+   - ping 127.0.0.1 This pings your computer (this address specifies the node you are pinging from and is called the loopback address).
- ping localhost -4 This pings another node (it tells you that the local area connection is able to send and receive information). The -4 option to receive results in IPv4 format.
- ping x.x.x.x This pings another node (replace x.x.x.x with an IP address).
- ping DNSNAME.DOMAIN.SUFFIX This pings a node using its fully qualified domain name (the name stored in DNS that is mapped to an IP address). An example is bf1.bigfirm.com.

# Verifying and Setting Local Area Connection Information Using the GUI

How to get to the client local area connection is important for these reasons:

+   - You can verify the local area connection configuration using the GUI.

+   - You can set the local area connection information manually if you do not have a DHCP server from to obtain these settings automatically.

# LOCAL AREA CONNECTIONS IN WINDOWS 8

To locate the local area connections on a Windows 8 client, select Start, type Control Panel, click Control Panel, and select Network and Sharing Center (shown in Figure 18.3).

The local area connection information will be the same on your Windows RT devices. The Windows networking interfaces are common across the Windows 8, RT, and Windows Server 2012 operating systems.
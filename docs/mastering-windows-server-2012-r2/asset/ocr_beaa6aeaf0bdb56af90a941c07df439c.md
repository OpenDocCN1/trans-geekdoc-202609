# TWO NICs REQUIRED FOR VPN

As a reminder, two NICs are required to fully configure RRAS as a VPN server. However, if you have only one NIC, you can still configure RRAS so that you can explore both RRAS and NPS. Instead of choosing "Virtual private network (VPN) access and NAT" on the Configuration page, choose "Custom configuration," and select the VPN access and NAT options from the Custom Configuration page. Once this is complete, you'll also need to access the properties page of the server and add a static address pool from the IPv4 tab.

+   7. From the options presented in the Configuration dialog box, "Virtual private network (VPN) access and NAT"; then click Next.
8. On the VPN Connection page, select the NIC that's connected to the Internet.
On this example system we renamed our Internet Facing NIC, selected it, and simulated a public IP address by assigning it 74.1.2.3.
9. Once you're happy with your selections here, click Next.
10. On the IP Assignment page, select "From a specified range of addresses," and click Next.
11. Click Next. Enter a starting IP address and an ending IP address.

These will be assigned to VPN clients and should be chosen to allow access to the network. Here we've chosen the range of 192.168.20.200 through 192.168.20.250 to be used as an example.

+   12. Click OK, and then click Next.
13. On the Managing Remote Access Servers page, accept the default of "No, use Routing and Remote Access to authenticate connection requests," and click Next.
14. Review the information and click OK to dismiss the dialog box.
15. If prompted, click the notification about the NPS connection request policy by clicking OK, and then click the Start button from the pop-up dialog to start the RRAS service.

A dialog box will appear indicating that the DHCP agent must be added if DHCP is being used to give out IP addresses. This is not relevant with a static IP range used in these steps.

At this point, you have a VPN server joined to a domain with Routing and Remote Access Service installed and configured. However, clients will not be able to connect until the network policy is configured.

# Configuring Policies

Network access policies are an integral component in delivering secure and controlled VPN access. If a client doesn't meet the conditions of any policy, the client will not be able to connect access. If the VPN server doesn't have any policies, clients can't meet the conditions of a policy and

connected with Multilink connections but was using only a small fraction of the bandwidth, BAP can disconnect the unused line so that it is available for another user. Figure 21.14 shows the Settings page for Multilink and BAP with the default selections.

## FIGURE 21.14
Configuring multilink settings for a network access policy

![](img/41a83208e6906a3732620203b836cea7_1120_0.png)

## IP Filters

You can use IPv4 and IPv6 input and output filters to control traffic across the connection. The settings that can be configured are the same type of settings that can be configured on a basic packet-filtering router.

Packets can be filtered based on IP addresses, subnets, protocols, and ports. For example, if the VPN clients are supposed to have access only to a single subnet in the network, you could create a filter to grant access to this subnet and no others. Similarly, a filter could be granted to block access to a specific subnet while granting access to all others.

## Encryption Settings

Encryption settings help determine what encryption will be used for the connection. Encryption will cipher the data so that it is not easily readable if intercepted. This gives four encryption choices:

- Basic Encryption (MPPE 40-bit)
- Strong Encryption (MPPE 56-bit)
- Strongest Encryption (MPPE 128-bit)
- No Encryption

## IP Settings

The IP settings determine how the client receives an IP address that is used for internal connections. A VPN client typically has a public IP address used to tunnel through the Internet to the VPN server, it will also need an IP address that leads to the internal network after it is connected.

This internal IP address can be assigned through a range of addresses assigned by the VPN server, requested from an internal DHCP server, or statically assigned. For a gateway-to-gateway VPN connection (where the VPN server accepts only a single connection), a statically assigned address is used. If you followed the steps in the chapter to configure Routing and Remote Access, you configured a range of IP addresses that are assigned to VPN clients.

## CREATING A NETWORK POLICY

Once you understand the elements of a network access policy, you can create your own. The following steps will lead you through the process of creating a network access policy to allow users in the Domain Users group to connect to your VPN server. These steps assume your VPN server is a member in the domain so that the Domain Users group can be used:

1. Launch the Routing and Remote Access Server (RRAS) console by selecting Server Manager > Routing and Remote Access.
2. Launch the Network Policy Server console by right-clicking Remote Access Logging and Policies and selecting NPS.
3. Select Network Policies in the Network Policy Server console. Right-click Network Policies, and select New.
4. Type Domain Users as the policy name.
5. Select Remote Access Server (VPN-Dial up) from the drop-down box as the type of network access server.
6. Your dialog will look like Figure 21.15. Click Next.
7. On the Specify Conditions page, click Add. Select Windows Groups, click Add, and then click the Groups button.

## FIGURE 21.5
Specifying the network policy name and connection type for a policy

![](img/41a83208e6906a3732620203b836cea7_1122_0.png)

8. Enter Domain Users as the object name, and click Check Names.
9. If prompted, enter credentials for the domain. Click OK to accept the group on the Select Group page. Click OK on the Windows Groups page, and click Next on the Specify Conditions page.

You can add any conditions as you like on the Specify Conditions page. However, if more than one condition is added, all conditions must be met to use the policy.

The Specify Access Permission page allows you to grant or deny access and override the user's dial-in properties.

10. Enter "Access granted" is selected. Select the "Access is determined by Dial-in properties (which override NPS policy)" box to ensure that dial-in users cannot override this policy. Click Next.

On the Configure Authentication Methods page, you can identify what authentication methods the server and clients will use.

11. Click Add to view the extensible authentication protocols that can be added.

Your display will look similar to Figure 21.16.

You can add the additional EAP methods, but for now leave the defaults.

## FIGURE 21.16
Choosing from the different authentication methods

![](img/41a83208e6906a3732620203b836cea7_1123_0.png)

EAP types are negotiated between NPS and the client in the order which they are laid.

12. Click to dismiss the Add EAP dialog box.

You'll explore the different authentication methods in greater depth in the next section.

13. Click Next.
14. On the Constraints page, ensure Idle Timeout is selected, and select the "Disconnect from the maximum idle time" box.
15. Change the 1 to 15 to indicate 15 minutes.
16. On the Configure Settings page, select "No encryption."
17. Click Next.
18. Click Finish.

At this point, you should be able to access the client and connect to the VPN server.

# CHAPTER 21 GETTING FROM THE OFFICE TO THE ROAD: VPNS

+   - Basic Encryption (MPPE 40-bit)

+   - Strong Encryption (MPPE 56-bit)

+   - Strongest Encryption (MPPE 128-bit)

+   - No Encryption

# IP Settings

The IP settings determine how the client receives an IP address that is used for internal connections. A VPN client typically has a public IP address used to tunnel through the Internet to the VPN server, it will also need an IP address that leads to the internal network after it is connected.

This internal IP address can be assigned through a range of addresses assigned by the VPN server, requested from an internal DHCP server, or statically assigned. For a gateway-to-gateway VPN connection (where the VPN server accepts only a single connection), a statically assigned address is used. If you followed the steps in the chapter to configure Routing and Remote Access, you configured a range of IP addresses that are assigned to VPN clients.

# CREATING A NETWORK POLICY

Once you understand the elements of a network access policy, you can create your own. The following steps will lead you through the process of creating a network access policy to allow users in the Domain Users group to connect to your VPN server. These steps assume your VPN server is a member in the domain so that the Domain Users group can be used:

+   1. Launch the Routing and Remote Access Server (RRAS) console by selecting Server Manager > Routing and Remote Access.

+   2. Launch the Network Policy Server console by right-clicking Remote Access Logging and Policies and selecting NPS.

+   3. Select Network Policies in the Network Policy Server console. Right-click Network Policies, and select New.

+   4. Type Domain Users as the policy name.

+   5. Select Remote Access Server (VPN-Dial up) from the drop-down box as the type of network access server.

+   6. Your dialog will look like Figure 21.15. Click Next.

+   7. On the Specify Conditions page, click Add. Select Windows Groups, click Add, and then click the Groups button.
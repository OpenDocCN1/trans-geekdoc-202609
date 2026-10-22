to ensure the endpoint provides the credentials necessary to authenticate to a particular SSID.

A drawback of SSID-/VLAN-based segmentation is increased wireless-network overhead and reduced performance due to multiple SSID memory requirements.

# Summary of Wireless Segmentation Controls

+   - LAN segmentation: protects internal LAN in the event of wireless compromise through VLAN and wireless IP–based firewall ACLs.
+   - VPNs can be used over a wireless medium to allow users to access LAN assets.
+   - Intra-wireless network segmentation:
+   - SSID based: The use of separate SSIDs for different business cases can easily be mapped to a VLAN and provide varying levels of segmentation.
+   - Group based: RADIUS-based VLAN assignment for wireless user's current group privileges.

# 33.7.3 User Segmentation.

A RADIUS server can make advanced authorization decisions for a valid username/password match. Leveraging designated user groups in the authorization process can provide fine-grained control over which users are able to use a wireless network segmented in large sweeps. If it’s known that domain admins, power users, or general service accounts should never be able to authenticate over a wireless connection, they can be implicitly denied through nonmembership in a wireless-users group. Any user group that requires the ability to authenticate over wireless should be a member of this group.

A default RSN implementation that can and will authorize any user within the provided directory can become a victim of attacks on default, inactive, guest, or test accounts within the designated directory. Test accounts may be vulnerable to weak canonical passwords (e.g., “test” or “password”) due to their creation during early stages of software or directory development or through other means that bypass corporate password policy. When a username/password authentication mechanism is in play, an attacker may attempt basic brute-force attacks to gain access to the network through standard test or guest accounts. Many organizations don’t feel this is a serious problem, but when a directory contains thousands of accounts, and organizations don’t audit on a regular basis, it’s easy for things to slip through the cracks.

The use of a designated wireless group:

+   - Decreases the surface area of an attack, even if an adversary is able to obtain a list of user accounts and leverage them to brute force a wireless network through the use of basic passwords.
+   - Decreases the number of endpoints with saved or remembered network profiles that can be attacked and used to capture username/password challenge hashes in a hotspot or RADIUS impersonation-style attack.

# 33.8 SECURITY AUDITING TOOLS.41

This section looks at the open source and commercial tools available to help audit a wireless environment and to understand the tools that war drivers have to attack a network. Exhibit 33.11 lists the main programs available, including older software still mentioned in discussions, and the platforms they run (or ran) under.
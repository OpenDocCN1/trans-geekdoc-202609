# Switch Learning and Forwarding (7.3.2)

A switch dynamically builds its MAC address table by examining the source MAC addresses of the frames received on a port. The switch forwards frames by searching for a match between the destination MAC address in a frame and an entry in the MAC address table.

# Examine the Source MAC Address

Every frame that enters a switch is checked for new information to learn. It does this by examining the source MAC address of the frame and the port number where the frame entered the switch. If the source MAC address does not exist, it is added to the table, along with the incoming port number. If the source MAC address does exist, the switch updates the refresh timer for that entry. By default, most Ethernet switches keep an entry in the table for 5 minutes.

In Figure 7-15, for example, PC-A is sending an Ethernet frame to PC-D. The table shows that the switch adds the MAC address for PC-A to the MAC address table.

Note

If the source MAC address exists in the table but on a different port, the switch treats this as a new entry. The entry is replaced using the same MAC address but with the more current port number.

# Find the Destination MAC Address

If the destination MAC address is a unicast address, the switch looks for a match between the destination MAC address of the frame and an entry in its MAC address table. If the destination MAC address is in the table, the switch forwards the frame out the specified port. If the destination MAC address is not in the table, the switch forwards the frame out all ports except the incoming port. This is called an *unknown unicast*.

As shown in Figure 7-16, the switch does not have the destination MAC address in its table for PC-D, so it sends the frame out all ports except port 1.

Note

If the destination MAC address is a broadcast or a multicast address, the frame is flooded out all ports except the incoming port.
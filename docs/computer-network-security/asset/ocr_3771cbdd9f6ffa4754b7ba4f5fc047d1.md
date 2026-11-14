# 7.2.4.2. Double tagging attack

# Overview of the attack

This attack consists of connecting to an interface that belongs to a native VLAN on a “trunk” port and sending a frame by inserting the fields related to the VLAN twice in an Ethernet frame.

Indeed, a double-tagging attack takes place in three steps:

+   1) the attacker generates and sends a 802.1Q frame, marked by double tags, to switch 1:
+   - the first tag carries the native VLAN identifier of the “trunk” port;
+   - the second tag carries the VLAN identifier of the target host.

| Data | Native VLAN ID | Target VLAN ID |
| --- | --- | --- |

# Figure 7.1. Frame 802.1Q, marked by two tags

2) switch 1 will remove the native VLAN tag. The attacker’s frame will now only contain the VLAN tag for the target host.

| Data | Target VLAN ID |
| --- | --- |

# Figure 7.2. Frame 802.1Q marked by the VLAN tag on the host target

3) switch 2 will send the frame to the port of the target host.

![](bbox=[0.137, 0.655, 0.862, 0.805])

# Figure 7.3. The steps in a double-tagging attack
settings and the system's event logs. There are also the obvious solutions, such as whether the network cable is plugged in. If the problem involves network communications, it can be helpful to review the configurations of the intermediate systems—that is, the routers, switches, and other devices on the path to the destination.

# Routing Tables

When troubleshooting a problem with packets not getting to their destination, checking routing tables is one way of narrowing down the location of the fault if there is. Begin by making sure that the routing table on the problem workstation is properly configured with a default gateway address. Then, examine the tables on the network's internal routers to see what path the packets are taking internally. If the packets are likely to be out of the local troubleshooter's hands, however it is still possible to use the traceroute (tracerert) tool to track the path of the packets to their destination.

# Interface Status

When troubleshooting a network performance issue, checking the interface status can provide significant diagnostic information. The status should indicate the speed of the network connection and whether it is running in half or full duplex. If aဆောင်'s network adapter is negotiating a lower than normal speed with the switch, or if it is running in half duplex when it should be full, the troubleshooter's next task is to find out why that is usually involves examining the switchport's interface and possibly configuring the interfaces manually.

# VLAN Assignment

A VLAN is essentially a virtualized subnet realized inside a switch, so is a workstation plugged into a switch with incorrect VLAN assignment (or just plugged into the wrong port) is connected to the wrong network. Trouble calls in when a user can connect to the network cannot find their familiar servers and printers, checking VLAN assignments should be on the troubleshooter checklist.

# Network Performance Baselines

As mentioned in Chapter 13, "Network Availability," it is a good practice for administrators to record baseline readings of network communication metrics at regular intervals. This is so that future troubleshooters have a history of documented readings they can compare to the current conditions. When users report that the network seems slow, for example, a baseline comparison can confirm to the troubleshooter that there is actually a slowdown. In addition, the baseline readings give the troubleshooter a way to confirm whether a solution has been successful.
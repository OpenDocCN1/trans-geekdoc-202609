# CHAPTER 4 WINDOWS SERVER 2012 R2 NETWORKING ENHANCEMENTS

# # Microsoft NIC Teaming

The purpose of NIC Teaming is to combine two or more interface adapters to create a single local adapter to provide fault tolerance or bandwidth aggregation for your network connections. Adapters that are members of a NIC team each maintain their own separate physical existence and each connect to network cables.

In earlier releases of Windows Server, NIC Teaming was available only through the use of third-party software solutions—such as HP, Intel, and Dell—and required network adapter hardware. If you had a network-connectivity problem on a server that had NIC Teaming configured and had to make a call to Microsoft to troubleshoot the problem, you would need to tell the third-party vendor for because NIC Teaming wasn't Microsoft's responsibility. In Windows Server 2012 R2, NIC Teaming is built into the operating system, and the tool is it's, free, and line-speed. This section will help you to understand the benefits of Windows Server 2012 R2 NIC Teaming, and we will show you how to easily create and manage a NIC team in your environment.

# ## Understanding the Benefits of a Windows
### Server 2012 R2 NIC Teaming

In today's always-connected world, it's essential that the network connections on your servers remain fault tolerant and that they can maintain uptime in the event of a failed adapter. Windows Server 2012 R2 helps to deliver this fault tolerance through the use of NIC Teaming—also known as load balancing and failover (LBFO). We need to purchase any additional (and potentially expensive) hardware or software. With NIC Teaming, multiple network adapters work together as a single logical connection, ensuring that connectivity is maintained even if one network adapter fails. It provides a scenario where a server can tolerate adapter and port failure up to the first switch segment.

You can also use it to aggregate bandwidth from multiple network adapters to deliver better and faster throughput. For example, if you had three 1-Gbps adapters in a server and decided to create a NIC team with them all, then you would end up with a new logical adapter that provides aggregate of 3 Gbps of throughput.

Other benefits of NIC Teaming are that it provides a common set of management tools for all network adapter types, eliminates potential problems caused by proprietary solutions, and of course, is fully supported by Microsoft.

# ## NIC Team Configurations

When you deploy NIC Teaming in Windows Server 2012 R2, you can choose from three basic teaming modes:

### Static Teaming Also known as switch-dependent, this type of configuration requires the switch to be aware of, and participate in the NIC teaming; Since the NIC team is dependent on the switch, you must ensure that all the members of the NIC team are connected to the same physical switch and not spread across multiple different switches, as seen in Figure 4.1.

Switch-independent Teaming Choosing a switch-independent teaming configuration does not require the switch to participate in the teaming; Here, the switch doesn't know that the network adapter is part of a team in the host, and so the adapters can be connected to different switches to provide basic fault tolerance at the switch level too. This teaming configuration
# Check Your Understanding—Scale to Larger Networks (17.3.4)

Refer to the online course to complete this activity.

# Verify Connectivity (17.4)

After a network has been implemented, a network administrator must be able to test the network connectivity to ensure that it is operating appropriately. In addition, it is a good idea for the network administrator to document the network.

# Verify Connectivity with Ping (17.4.1)

Whether a network is small and new, and even if you are scaling an existing network, you will always want to be able to verify that your components are properly connected to each other and to the internet. This section discusses some utilities that you can use to ensure that a network is connected.

Using the ping command is the most effective way to quickly test Layer 3 connectivity between a source IP address and a destination IP address. This command also displays various round-trip time statistics.

Specifically, the ping command uses the Internet Control Message Protocol (ICMP) Echo Request (ICMP Type 8) and Echo Reply (ICMP Type 0) messages. The ping command is available in most operating systems, including Windows, Linux, macOS, and Cisco IOS.

On a Windows 10 host, the ping command sends four consecutive ICMP Echo Request messages and expects four consecutive ICMP Echo Reply messages from the destination.

For example, say that PC A pings PC B. As shown in Figure 17-10, the PC A Windows host sends four consecutive ICMP Echo Request messages to PC B (that is, 10.1.1.10).

```
C:\> ping 10.1.1.10
```

![](bbox=[0.22, 0.78, 0.85, 0.88])

| Source IP | Destination IP | ICMP |
|---|---|---|
| 192.168.10.10 | 10.1.1.10 | Echo |

Figure 17-10 PC A Pinging PC B

The destination host receives and processes the ICMP Echo Request, sometimes referred to as an ICMP Echo. As shown in Figure 17-11, PC B responds by sending four ICMP Echo Reply messages to PC A.
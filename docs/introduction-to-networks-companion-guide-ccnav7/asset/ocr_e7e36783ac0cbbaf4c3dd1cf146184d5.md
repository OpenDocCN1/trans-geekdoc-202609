# The show cdp neighbors Command (17.5.6)

In addition to the commands discussed so far in this chapter, several other IOS commands are useful. Cisco Discovery Protocol (CDP) is a Cisco-proprietary protocol that runs at the data link layer. Because CDP operates at the data link layer, two or more Cisco network devices, such as routers that support different network layer protocols, can learn about each other even if Layer 3 connectivity has not been established.

When a Cisco device boots, CDP starts by default. CDP automatically discovers neighboring Cisco devices running CDP, regardless of which Layer 3 protocol or suites are running. CDP exchanges hardware and software device information with its directly connected CDP neighbors.

CDP provides the following information about each CDP neighbor device:

+   - **Device identifiers:** The configured hostname of a switch, router, or other device
- **Address list:** Up to one network layer address for each protocol supported
- **Port identifier:** The name of the local and remote ports, in the form of an ASCII character string, such as FastEthernet 0/0
- **Capabilities list:** Capabilities, such as whether a specific device is a Layer 2 switch or a Layer 3 switch
- **Platform:** The hardware platform of a device (for example, a Cisco 1841 series router)

Refer to the topology in Figure 17-21 and the show cdp neighbors command output in Example 17-26.

![](bbox=[0.25, 0.71, 0.88, 0.78])

Figure 17-21 CDP Neighbors Example Topology

# Example 17-26 The show cdp neighbors Command

```
R3# show cdp neighbors
Capability Codes: R - Router, T - Trans Bridge, B - Source Route Bridge
                S - Switch, H - Host, I - IGMP, r - Repeater, P - Phone,
                D - Remote, C - CVTA, M - Two-port Mac Relay

Device ID        Local Intrfce     Holdtime    Capability  Platform    Port ID
S3               Gig 0/0/1          122                 S I        WS-C2960+  Fas 0/5
Total cdp entries displayed : 1
R3#
```
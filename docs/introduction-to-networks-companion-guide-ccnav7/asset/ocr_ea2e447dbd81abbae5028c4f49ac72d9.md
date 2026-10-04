![](bbox=[0.22, 0.1, 0.78, 0.27])

Figure 17-23 Duplex Autonegotiation

# IP Addressing Issues on IOS Devices (17.7.2)

IP address-related problems are likely to prevent remote network devices from communicating. Because IP addresses are hierarchical, any IP address assigned to a network device must conform to that range of addresses in that network. Wrongly assigned IP addresses create a variety of issues, including IP address conflicts and routing problems.

Two common causes of incorrect IPv4 assignment are manual assignment mistakes and DHCP-related issues.

Network administrators often have to manually assign IP addresses to devices such as servers and routers. If a mistake is made during the assignment, communications issues with the device are very likely to occur.

On an IOS device, use the show ip interface command or the show ip interface brief command to verify what IPv4 addresses are assigned to the network interfaces. For example, issuing the show ip interface brief command as shown in Example 17-32 would validate the interface status on R1.

# Example 17-32 Using show ip interface brief to Verify IPv4 Addressing on a Cisco Device

```
```
R1# show ip interface brief
Interface              IP-Address      OK? Method Status                Protocol
GigabitEthernet0/0/0   209.165.200.225 YES manual up                    up
GigabitEthernet0/0/1   192.168.10.1    YES manual up                    up
Serial0/1/0            unassigned      NO  unset  down                  down
Serial0/1/1            unassigned      NO  unset  down                  down
GigabitEthernet0       unassigned      YES unset  administratively down down
R1#
```
```
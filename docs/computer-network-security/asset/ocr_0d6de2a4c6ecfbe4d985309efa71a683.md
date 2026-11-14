```
ASA1 (config-if)# nameif DMZ
ERROR: This license does not allow configuring more than 2 interfaces with nameif and without a “no forward” command on this interface or on 1 interface(s) with nameif already configured.
```

# 3.4. Explain why this error message is displayed.

# 3.5. Block any traffic between the internal network (vlan1) and the DMZ (vlan3).

```
ASA1(config-if)#no forward interface vlan 1
ASA1(config-if)#nameif DMZ
ASA1(config-if)# ip address 192.168.10.1 255.255.255.0
ASA1(config-if)# security-level 50
```

# 3.6. Assign ASA ports to the connected VLANs.

```
ASA1 (config)# interface e0/1
ASA1 (config-if)# switchport access vlan 1
ASA1 (config-if)# no shutdown
ASA1 (config-if)# interface e0/0
ASA1 (config-if)# switchport access vlan 2
ASA1 (config-if)# no shutdown
ASA1 (config-if)# interface e0/2
ASA1 (config-if)# switchport access vlan 3
ASA1 (config-if)# no shutdown
```

# 3.7. Check the configuration and port allocation using the sh interface ip brief, sh ip address and sh switch vlan commands.

# 4. Configure the DHCP service on ASA.

# 4.1. Configure the DHCP service for the company’s internal network.

```
ASA1(config)#dhcpd address 192.168.1.5-192.168.1.100 inside
Warning, DHCP pool range is limited to 32 addresses, set address range as: 192.168.1.5-192.168.1.36
ASA1(config)# dhcpd dns 192.168.1.1
```
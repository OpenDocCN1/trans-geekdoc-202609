```
ASA1 (config-if)# interface e0/0
ASA1 (config-if)# switchport access vlan 2
ASA1 (config-if)# no shutdown
```

# 4.4. Check the configuration and allocation of ports.

```
ASA1#sh interface ip brief
```

| Interface | IP-Address | OK? | Method | Status | Protocol |
|---|---|---|---|---|---|
| Ethernet0/0 | unassigned | YES | unset | up | up |
| Ethernet0/1 | unassigned | YES | unset | up | up |
| Ethernet0/2 | unassigned | YES | unset | up | up |
| ... | | | | | |
| Vlan1 | 192.168.1.1 | YES | manual | up | up |
| Vlan2 | 212.212.1.1 | YES | manual | up | up |

```
ASA1#sh ip address
```

| Interface | Name | IP address | Subnet mask | Method |
|---|---|---|---|---|
| Vlan1 | inside | 192.168.1.1 | 255.255.255.0 | manual |
| Vlan2 | outside | 212.212.1.1 | 255.255.255.252 | manual |

```
ASA1#sh switch vlan
```

| VLAN | Name | Status | Ports |
|---|---|---|---|
| 1 | inside | up | Et0/1, Et0/2, Et0/3, Et0/4
Et0/5, Et0/6, Et0/7 |
| 2 | outside | up | Et0/0 |

4.5. Ensure that the ping command was successful between ASA1 and R1 and between ASA1 and PC1.

# 5. Configure a default static route for the ASA.

# 5.1. Configure a default route towards the external networks.

```
ASA1(config)#route outside 0.0.0.0 0.0.0.0 212.212.1.2
```
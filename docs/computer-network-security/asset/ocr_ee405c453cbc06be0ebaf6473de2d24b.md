# 7.2.4. VLAN hopping attacks.

VLAN hopping attacks consist of connecting to a particular VLAN and attempting to access network traffic belonging to other VLANs. By using VLAN hopping, an attacker may capture another VLAN's network traffic or send data from one VLAN to another.

There are two types of VLAN hopping attacks, namely: “Switch spoofing” and “Double Tagging” attacks.

# 7.2.4.1. Switch spoofing attack

# Overview of the DTP protocol

DTP is the protocol used to dynamically create trunks (aggregated links) between two switches. This may be configured in three modes: “Dynamic Desirable”, “Dynamic Auto” or “Trunk”.

# Overview of the attack

This attack consists of connecting to the interface of a switch and generating DTP messages from a program to create a “trunk” link between the attacker’s computer and the switch. The attacker can now capture data from all other VLANs.

This attack can also take place through the introduction of a “spoofed switch”, configured for using the DTP protocol.

# Countermeasures

The following features are used to prevent this kind of attack:

| Command | Description |
|---|---|
| S1(config)#interface range gigabitethernet 0/0 - 20 S1(config-if-range)#switchport mode access | Configures the ports of a switch connected to hosts as access ports. |
| S1(config-if)# switchport mode trunk | Explicitly enables the aggregation links. |
| S1(config-if)# switchport nonegotiate | Disables DTP and prevents DTP messages from being generated. |
| S1(config)#interface range gigabitethernet 0/26 - 32 S1(config-if)# switchport access vlan Vlan S1(config-if)# shutdown | Assigns the unused ports to a dedicated VLAN and disables them. |
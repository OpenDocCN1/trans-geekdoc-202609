# 7.2. Types of attacks on Layer 2

In this chapter we will study several security threats that target Layer 2 of an OSI model and discuss countermeasures that can be used to protect against these risks. This is part of securing the “data plane”.

# 7.2.1. MAC address flooding attacks

# Overview of the attack

An attacker connects to a switch port and floods it using a large number of frames with fake source MAC addresses. Once the switch table is saturated, the switch acts as a hub. The attacker can then capture sensitive data from the network.

# Countermeasures

The “port security” feature is a countermeasure that can prevent MAC address flooding attacks.

| Command | Description |
| :--- | :--- |
| Switch(config-if)# switchport mode access<br>Switch(config-if)# switchport port-security | Enables port security and assign the current MAC address to the port.
The default port security values are:
– only one MAC address can be assigned;
– the violation action is set to the
deactivation of the port. |
| Switch(config-if)# switchport port-security maximum value | Defines the maximum possible number of MAC addresses secured for the interface. |
| Switch(config-if)# switchport port-security mac-address mac-address | Manually assigns the MAC addresses that can connect to this port. |
| Switch(config-if)# switchport port-security violation { protect | restrict |
shutdown [shutdown vlan ] } | Configures the action that must be taken when
the number of MAC addresses exceeds the
pre-defined maximum. |
| Switch(config-if)# errdisable recovery
interval seconds. | Configures the period of deactivation of a
port. |
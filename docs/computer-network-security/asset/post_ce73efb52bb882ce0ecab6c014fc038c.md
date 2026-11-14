
## 7.2.4. VLAN hopping attacks.

VLAN hopping attacks consist of connecting to a particular VLAN and attempting to access network traffic belonging to other VLANs. By using VLAN hopping, an attacker may capture another VLAN's network traffic or send data from one VLAN to another.

There are two types of VLAN hopping attacks, namely: “Switch spoofing” and “Double Tagging” attacks.

### 7.2.4.1. Switch spoofing attack

### Overview of the DTP protocol

DTP is the protocol used to dynamically create trunks (aggregated links) between two switches. This may be configured in three modes: “Dynamic Desirable”, “Dynamic Auto” or “Trunk”.

### Overview of the attack

This attack consists of connecting to the interface of a switch and generating DTP messages from a program to create a “trunk” link between the attacker’s computer and the switch. The attacker can now capture data from all other VLANs.

This attack can also take place through the introduction of a “spoofed switch”, configured for using the DTP protocol.

### Countermeasures

The following features are used to prevent this kind of attack:

| Command | Description |
|---|---|
| S1(config)#interface range gigabitethernet 0/0 - 20 S1(config-if-range)#switchport mode access | Configures the ports of a switch connected to hosts as access ports. |
| S1(config-if)# switchport mode trunk | Explicitly enables the aggregation links. |
| S1(config-if)# switchport nonegotiate | Disables DTP and prevents DTP messages from being generated. |
| S1(config)#interface range gigabitethernet 0/26 - 32 S1(config-if)# switchport access vlan Vlan S1(config-if)# shutdown | Assigns the unused ports to a dedicated VLAN and disables them. |

### 7.2.4.2. Double tagging attack

### Overview of the attack

This attack consists of connecting to an interface that belongs to a native VLAN on a “trunk” port and sending a frame by inserting the fields related to the VLAN twice in an Ethernet frame.

Indeed, a double-tagging attack takes place in three steps:

- 1) the attacker generates and sends a 802.1Q frame, marked by double tags, to switch 1:
  - the first tag carries the native VLAN identifier of the “trunk” port;
  - the second tag carries the VLAN identifier of the target host.

| Data | Native VLAN ID | Target VLAN ID |
| --- | --- | --- |

### Figure 7.1. Frame 802.1Q, marked by two tags

2) switch 1 will remove the native VLAN tag. The attacker’s frame will now only contain the VLAN tag for the target host.

| Data | Target VLAN ID |
| --- | --- |

### Figure 7.2. Frame 802.1Q marked by the VLAN tag on the host target

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_144_0.png)

### Figure 7.3. The steps in a double-tagging attack

— In figures 7.1, 7.2 and 7.3, the “data” field represents the information connected to an Ethernet frame, in addition to the other information from the packet and without taking into account the order of their succession in a 802.1Q frame.

— This type of attack is unidirectional and only works if the hacker is connected to a port in the same VLAN as the native trunk port VLAN.

### Countermeasures

The “native VLAN” feature is used to prevent this kind of attack.

| Command | Description |
|---|---|
| Switch(config-if)# switchport trunk native vlan vlan | Create a dedicated VLAN for native VLAN traffic separated from user traffic. |

### 7.2.5. STP-based attacks

### Overview of the STP

STP is a network protocol that makes it possible to create a loopless network topology by blocking certain paths in the LAN, consisting of multiple switches. Its function can be summarized as follows:

- selecting a “root bridge” switch for each VLAN;
- defining “root ports” that allow interconnection between the “root” switch and other switches;
- defining ports authorized to transmit data;
- blocking certain ports on the switches.

### Overview of the attack

This attack consists of introducing a “spoofed switch”, which will attempt to position itself as the “root bridge” by sending false “PDU” messages that contain a minimal “BID”. This will have the effect of modifying the STP topology and changing the role of the ports. From now on, the attacker can use the ports which were blocked earlier, in order to capture all the traffic passing through the network.

### Countermeasures

The “guard root” feature is used to prevent this kind of attack:

| Command | Description |
|---|---|
| S1(config-if)# spanning-tree guard root | Protects against the replacement of the original “root bridge” by another switch. |

NOTE.
- “bpdu guard” and “guard root” are similar, but have different impacts:
- bpdu guard disables the ports when receiving bpdu messages if the “portfast” option is activated on the port. You must manually reactivate the port or configure a “deactivation time”.
- guard root allows bpdu messages to travel across a port to maintain STP topology, unless another switch attempts to become the “root bridge”. The port is reactivated when the other switch stops its attempts.

## 7.3. The best security practices for protecting Layer 2

The best practices to protect Level 2, for each type of attack, include:

| Type of attack | Description | Countermeasures |
|---|---|---|
| MAC address attacks | – MAC address flooding<br>– MAC address spoofing | – Using port security for access ports.<br>– Configure the **DAI** feature. |
| STP attacks | – Modification of STP topology | – Configuring the **portfast** feature.<br>– Configuring the **bpdu guard** feature.<br>– Configure the **guard root** feature. |
| VLAN hopping attacks | – Using DTP<br>– Double tagging attack | – Disable DTP on the access ports.<br>– Explicitly configure the “trunk” ports.<br>– Always use a dedicated native VLAN.<br>– Deactivate all unused ports and place them in an unused VLAN.<br>– Avoid using VLAN 1. |

## 7.4. Exercises for application

EXERCISE 10.–

### Topology

![](img/6cc1cc8bbb23ba3014958aee841c4ff5_147_0.png)

For a color version of this figure, see www.iste.co.uk/sadiqui/computer.zip

### Addressing table

| Device | Interface | IP address | Subnet mask | Gateway |
|---|---|---|---|---|
| S1 | VLAN1 | 192.168.0.2 | /24 | 192.168.0.1 |
| S2 | VLAN1 | 192.168.0.3 | /24 | 192.168.0.1 |
| S3 | VLAN1 | 192.168.0.4 | /24 | 192.168.0.1 |
| PC1 | NIC | 192.168.0.5 | /24 | 192.168.0.1 |
| PC2 | NIC | 192.168.0.6 | /24 | 192.168.0.1 |
| dhcp-server | NIC | 192.168.0.7 | /24 | 192.168.0.1 |

### Objectives

- Securing passwords;
- Putting in place connection restrictions;
- Securing the local network against Level 2 attacks.

### Software to be used

- Packet Tracer.

### Part A: establishing the basic device configuration.

- 1. Configure the names of the host as indicated in the topology.
- 2. Apply the IP addresses to the device interfaces according to the addressing table.

### Part B: securing passwords

### On switch S1

- 1. Set the password “Ci$c0ena” for the privileged mode.
- 2. Configure the console ports and virtual access lines.
- 2.1. Set “Ci$c0con” as the password for the console port and set the inactivity interval to 5 minutes.
- 2.2. Set “Ci$c0vty” as the password on the VTY lines and set the inactivity interval to 2 minutes.
- 3. Encrypt all passwords.

### Part C: securing access to VTY lines using ssh

- 1. Configure ssh connections.

### On switch S1

- Use the following options to configure the ssh connections:
  - domain name: tri.local;
  - the user name: sshadmin with the password: Ci$c0ssh;
  - the RSA encryption key is 1024 bits;
  - the SSH version used is version 2;
  - the wait time is 90s;
  - the number of login attempts is 3;
  - only authorize ssh sessions.

- 2. Configure the connection parameters.

Use the “login block-for” command to configure the connection being blocked for **60s** if two connection attempts have failed within **30s**.

### Part D: securing the local network against Layer 2 attacks

### On switch S2

### 1. Secure LAN against MAC address flooding attacks.

### 1.1. Explain this type of an attack.

### 1.2. Set the maximum number of secured MAC addresses to be 2 on the FastEthernet ports 0/4 to 0/16.

```
S2(config)# int range f0/4-16
S2(config-if)# switchport mode access
S2(config-if)# switchport port-security
S2(config-if)# switchport port-security maximum 2
```

### 1.3. Block the frames received on the ports in case of access violation.

```
S2(config-if)# switchport port-security violation protect
```

### 1.4. Manually assign the MAC address of the Server_dhcp to port f0/3.

```
S2(config)# int f0/3
S2(config-if)# switchport mode access
S2(config-if)# switchport port-security
S2(config-if)# switchport port-security mac-address mac-address_server_dhcp
```

### 1.5. Deactivate the unused FastEthernet ports 0/17 to 0/24.

```
S2(config)# int range f0/17-24
S2(config-if)# shutdown
```

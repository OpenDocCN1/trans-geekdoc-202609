
With TCP/IP ports. Intruders can easily detect ports that are open to incoming traffic using scanning software. Once detected, the ports become targets for the intruder's exploitation.

For necessary services, their TCP/IP ports must be left open, and it is up to administrators to protect them with firewalls and other means. However, for any ports that are left open by services or daemons not being used, administrators should take action by disabling the services and closing the port to any incoming traffic.

## EXAM TIP

The term port has multiple definitions in the IT universe. A TCP/IP port is a logical endpoint through which an application communicates with the network. Switches also have ports, which are physical cable connectors that provide links to hosts and other network devices. Candidates for the Network+ exam should be aware of the term's uses.

## Change Default Passwords

Virtually all network devices require users or administrators to log on before they can access their administrative interface. While some devices require a user to create a password during the first connection, many have default usernames and passwords set by the manufacturer.

In these cases, the first thing the administrator should do when setting up the device is change the default password for a device, and if possible, the username as well. If intruders know the default username for a device, they can begin to cracking the password immediately. If the administrator has changed the username, intruders will have to guess that as the password.

## Password Complexity/Length

When specifying a password for a device or an account, the objective is to make the process of guessing the password as long and difficult as possible. The longer the password is, the greater the number of possibilities there are for an attacker to guess and the longer it takes to crack it.

As shown in Table 18.1, adding to the length of a password increases the number of possibilities dramatically, as adding basic symbols to the alphanumeric character set. Just increasing the password length by two characters, from eight to 10, increases the crack time from hours to months.

### TABLE 18.1 Effects of password length on possibilities and crack time

| Number of characters | Letters & numbers | Letters, numbers, & basic symbols | Offline crack time (with symbols) |
| :--- | :--- | :--- | :--- |
| 6 characters | 2.2 billion | 109 billion | 1.1 seconds |
| 8 characters | 2.9 trillion | 521 trillion | 1.45 hours |
| 10 characters | 3.7 quadrillion | 2.4 quintillion | 9.47 months |
| 15 characters | 227 sextillion | 3.88 octillion | 1.2 billion years |

All passwords are a trade-off between security and convenience, administrators should consider these figures when configuring passwords for network devices and creating password policies for the network's users.

## Enable DHCP Snooping

DHCP snooping is a feature found on many switches that is designed to prevent rogue DHCP servers from connecting to the network and allocating incorrect IP addresses to clients. These incorrect IP addresses can prevent the clients from accessing the real enterprise network, sending them instead of an alternative network run by the attacker responsible for the rogue. By itself, this is a form of denial-of-service attack, but it can also be the opening salvo of an on-path (man-in-the-middle) attack.

The DHCP snooping feature enables administrators to designate certain switch ports as trusted for DHCP server traffic. DHCP packets arriving at the switch from a untrusted port are silently discarded. The switch (snoops) the DHCP packets arriving through the trusted ports and uses the information to create a table of legitimate IP address-to-MAC mappings called a binding table.

## Change Default VLAN

By default, switches are equipped with a single VLAN—usually VLAN1—to which all of the switchports are assigned at the factory. The default VLAN is permanent and unchangeable, so potential attackers know it is there, where it presents a tempting target. Therefore, even if the administrators do not plan to segment the network using VLANs, they should create at least one new VLAN (hopefully not VLAN2) and move all of the switchports into it. Any attackers must then discover the VLAN before they can target it, which makes the target that much less tempting.

## Patch and Firmware Management

Operating systems, applications, and network devices all require software updates from time to time, but it is up to the administrators of the network to create a patch management policy that specifies when and if to apply the updates. The most critical types of updates for operating systems and applications are those that address the latest security issues.

Attackers and network devices look for vulnerabilities in software and hardware. When a vulnerability is found, the vendor may release a patch or update to fix the issue. It is the responsibility of the administrators to test and deploy these updates in a timely manner to protect the network from exploitation.

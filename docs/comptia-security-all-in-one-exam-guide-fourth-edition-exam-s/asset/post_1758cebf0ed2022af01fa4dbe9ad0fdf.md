
Cisco IOS also runs on many of Cisco’s Ethernet switching products. Like routers, these have capabilities for receiving and processing protocols such as Telnet and SNMP. Smaller network components do not usually run large software suites and typically have smaller software loaded on internal nonvolatile RAM (NVRAM). While the update process for this kind of software is typically called a firmware update, this does not change the security implications of keeping it up to date. In the case of a corporate network with several devices, someone must take ownership of updating the devices, and updates must be performed regularly according to security and administration policies.

## Network Device Configuration

As important as it is to keep software up to date, properly configuring network devices is equally, if not more, important. Many network devices, such as routers and switches, now have advanced remote management capabilities with multiple open ports accepting network connections. Proper configuration is necessary to keep these devices secure. Choosing a good password is very important in maintaining external and internal security, and closing or limiting access to any open ports is also a good step for securing the devices. On the more advanced devices, you must carefully consider what services the device is running, just as with a computer.

![](img/922567202a944c5e8d3ba0168d2ad3a5_319_0.png)

> **EXAM TIP** Remember that while a router is essentially just a device that forwards packets between networks, it can also be used to help secure the network by controlling traffic flowing into and leaving your network.

In many cases, a network device’s primary protection method is a password. Good passwords are one of the most effective security tools, because a good password can be resistant to several forms of attack. This resistance makes an attacker use simple brute-force methods, taking tremendous amounts of time and generating a large amount of network traffic, both increasing the likelihood of the attacker’s efforts being detected. Unfortunately, good passwords are often hard to remember, so weaker passwords are usually used.

To recognize the impact on security that a bad password can have, consider the fact that a typical brute-force program can try every word in the unabridged English dictionary in less than a day, but it would take several thousand years to attempt to brute force an eight-character password. This is based upon using not only the standard 26-character alphabet, but also adding capitalization for 26 more characters, numeric digits for 10 more, and special characters, adding another 33 different characters. This totals 95 different characters that can be used, giving 6,704,780,954,517,120, or 6 quadrillion, different possibilities for a one- to eight-character password. This is in stark contrast to the estimated 2 million words in the English language, or the 217 billion possibilities provided by simple lowercase alphabetic characters.

The best kinds of passwords bear no resemblance to actual words, such as “AvhB42^&nFh.” However, although such passwords provide greater security, they are difficult to remember, leading users to choose passwords that are based on regular dictionary words. While this is a concern for any password on any system, it is of greater concern on network infrastructure equipment, because many pieces of network equipment require only password authentication for access—typically, no username is required.

One of the password-related issues that many administrators overlook is SNMP, which was developed in 1988 and has been implemented on a huge variety of network devices. Its wide implementation is directly related to its simplicity and extensibility. Since every manufacturer can add objects to the Management Information Base (MIB), one manufacturer can add functionality without interfering with any other manufacturer’s portion of the MIB tree. This feature of the protocol lets manufacturers make SNMP very powerful for configuration and monitoring purposes. The downside is that many devices have SNMP turned on by default. Network administrators not using SNMP will often forget to disable SNMP or will forget to change the well-known default passwords—typically “public” for read-only access and “private” for read/write access. With the SNMP service active and using a default password, an attacker can retrieve a great deal of interesting information from a network device, as well as altering any SNMP-capable settings. If SNMP is employed, well-thought-out passwords should be used, as well as a schedule for password updates.

![](img/922567202a944c5e8d3ba0168d2ad3a5_320_0.png)

> **EXAM TIP** The use of the word “public” as a public SNMP community string is an extremely well-known vulnerability. Any system using an SNMP community string of “public” should be changed immediately.

Keep in mind that SNMP passwords are often passed in the clear, so it should never be treated as a trusted protocol. The SNMP service should also be limited only to connections from the management station’s IP address. If SNMP is not used, the service should be disabled, if possible. Otherwise, the ports for SNMP should not be accessible from anywhere on the external or internal network.

Another best practice for network devices is to eliminate the use of cleartext protocols such as Telnet and implement more secure alternatives such as SSH. SSH (Secure Shell) is an encrypted protocol that can be used to create a command-line–based connection to remote network devices and servers. Unlike Telnet, SSH is encrypted from end to end, so anything that is typed within an SSH session cannot be easily intercepted and viewed by potential attackers.

As with any system, security is largely dependent on proper configuration of the system itself. A router can be secured with proper configuration just as easily as it can be left unsecured through poor configuration. Good passwords and knowledge of what services the devices are running are important to maintaining the security of those devices.

## 802.1x

As described in Chapter 2, 802.1x acts as a method of limiting access to a network to only authorized users. Also known as *port-based network access control*, 802.1x is an IEEE standard and part of the IEEE 802.1 network protocol set. Employing edge-based access control for all systems increases the security posture. 802.1x is port-based security that ensures that authentication occurs before allowing a device to connect to a port.

![](img/922567202a944c5e8d3ba0168d2ad3a5_321_0.png)

> **EXAM TIP** 802.1x is an authentication method that controls access to a port on a device and is also called port-based network access control or port-based authentication.

## MAC Limiting and Filtering

The use of MAC addresses to perform port-level security on switches adds a layer of security to the system. This layer of security ensures that the hardware associated with the network is approved for use and connected as designed. This prevents the insertion of unauthorized communication channels into the network layer. MAC filtering can be very useful to ensure that the network connections are not rerouted to other machines, or that unauthorized connections to existing network jacks do not occur.

MAC limiting is the use of setting a limit to the number of MAC addresses a switch or port can learn. This prevents a wide variety of attacks including flooding attacks, as it ignores large numbers of "new" MAC addresses. Ports can also be constrained to specific MACs or groups of MACs to limit the ability of outside connections to a network.

## Disabling Unused Interfaces and Unused Application Service Ports

Just as in servers, an important management issue for running a secure system is to identify the specific needs of a system for its proper operation and to enable only items necessary for those functions. Keeping all other services and users off the system improves system throughput and increases security. Networks have ports and connections that need to be disabled if not in use. If a switch is prewired to outlets in rooms that are not used, these ports should be disabled until needed, preventing an attacker from using unused ports. Similarly, management interfaces and other options should be restricted and disabled if not actively used to prevent unauthorized use of these network functions. An attacker that gains access to a network device can reconfigure the device if open management interfaces are discoverable and used. Reducing the attack surface area associated with the network configuration reduces the vulnerabilities now and in the future as updates are required.

![](img/922567202a944c5e8d3ba0168d2ad3a5_321_1.png)

> **EXAM TIP** When designing and building out a network, any ports or functions that are not actively used should be disabled until needed, and only then enabled for use. This minimalist setup is similar to the implicit deny philosophy and can significantly reduce an attack surface.

## Rogue Machine Detection

One method of infiltrating a network is through the installation of rogue devices. Another case is where a user adds a device for some unauthorized purpose, such as a local wireless access point. These devices and network changes pose a variety of security is-


| Official Exam Objective | All-in-one Coverage | Chapter No. | Page No. |
|---|---|---:|---:|
| **3.6** Analyze a scenario and select the appropriate type of mitigation and deterrent techniques. | Mitigation Techniques | 15 | 267 |
| **3.7** Given a scenario, use appropriate tools and techniques to discover security threats and vulnerabilities. | Threat and Vulnerability Discovery | 16 | 289 |
| **3.8** Explain the proper use of penetration testing versus vulnerability scanning. | Threat and Vulnerability Discovery | 16 | 304 |
| **4.0 Application, Data and Host Security** |  |  |  |
| **4.1** Explain the importance of application security controls and techniques. | Application Security Controls | 17 | 317 |
| **4.2** Summarize mobile security concepts and technologies. | Mobile Device Security | 18 | 327 |
| **4.3** Given a scenario, select the appropriate solution to establish host security. | Host-based Security | 19 | 341 |
| **4.4** Implement the appropriate controls to ensure data security. | Host-based Security | 19 | 364 |
| **4.5** Compare and contrast alternative methods to mitigate security risks in static environments. | Securing Alternative Environments | 20 | 375 |
| **5.0 Access Control and Identity Management** |  |  |  |
| **5.1** Compare and contrast the function and purpose of authentication services. | Access Control and Authentication | 21 | 387 |
| **5.2** Given a scenario, select the appropriate authentication, authorization or access control. | Access Control and Authentication | 21 | 387 |
| **5.3** Install and configure security controls when performing account management, based on best practices. | Account Management | 22 | 417 |
| **6.0 Cryptography** |  |  |  |
| **6.1** Given a scenario, utilize general cryptography concepts. | Cryptographic Concepts | 23 | 431 |
| **6.2** Given a scenario, use appropriate cryptographic methods. | Cryptographic Methods | 24 | 447 |
| **6.3** Given a scenario, use appropriate PKI, certificate management and associated components. | Cryptographic Methods | 24 | 457 |

## PART I
### Network Security
- Chapter 1 Network Device Configuration
- Chapter 2 Secure Network Administration
- Chapter 3 Secure Network Design
- Chapter 4 Secure Wireless Networking

## Network Device Configuration

In this chapter, you will

- Implement security configuration parameters on network devices
- Implement security configuration parameters on other technologies

Networks are composed of devices and are configured via software to perform the desired activities. The correct configuration of network devices is a key element of securing the network infrastructure. Proper configuration can greatly assist in the network security posture. Learning how to properly configure network devices is important for passing the CompTIA Security+ exam.

### Network Devices

A complete network computer solution in today’s business environment consists of more than just client computers and servers. Devices are used to connect the clients and servers and to regulate the traffic between them. Devices are also needed to expand this network beyond simple client computers and servers to include yet other devices, such as wireless and handheld systems. Devices come in many forms and with many functions, from hubs and switches, to routers, wireless access points, and special-purpose devices such as virtual private network (VPN) devices. Each device has a specific network function and plays a role in maintaining network infrastructure security.

![](img/922567202a944c5e8d3ba0168d2ad3a5_46_0.png)

> **EXAM TIP** Expect questions on how to implement security configuration parameters on network devices.

### Firewalls

A firewall can be hardware, software, or a combination whose purpose is to enforce a set of network security policies across network connections. It is much like a wall with a window; the wall serves to keep things out, except those permitted through the window (see Figure 1-1). Network security policies act like the glass in the window; they permit

![](img/922567202a944c5e8d3ba0168d2ad3a5_47_0.png)

some things to pass, such as light, while blocking others, such as air. The heart of a firewall is the set of security policies that it enforces. Management determines what is allowed in the form of network traffic between devices, and these policies are used to build rule sets for the firewall devices used to filter network traffic across the network.

*Security policies* are rules that define what traffic is permissible and what traffic is to be blocked or denied. These are not universal rules, and many different sets of rules are created for a single company with multiple connections. A web server connected to the Internet may be configured to allow traffic only on port 80 for HTTP and have all other ports blocked, for example. An e-mail server may have only necessary ports for e-mail open, with others blocked. The network firewall can be programmed to block all traffic to the web server except for port 80 traffic, and to block all traffic bound to the mail server except for port 25. In this fashion, the firewall acts as a security filter, enabling control over network traffic, by machine, by port, and in some cases based on application-level detail. A key to setting security policies for firewalls is the same as has been seen for other security policies—the principle of least access. Allow only the necessary access for a function; block or deny all unneeded functionality. How a firm deploys its firewalls determines what is needed for security policies for each firewall.

As will be discussed later, the security topology will determine what network devices are employed at what points in a network. At a minimum, the corporate connection to the Internet should pass through a firewall. This firewall should block all network traffic except that specifically authorized by the firm. Blocking communications on a port is simple—just tell the firewall to close the port. The issue comes in deciding what services are needed by whom, and thus which ports should be open and which should be closed. This is what makes a security policy useful. The perfect set of network security policies for a firewall is one that the end user never sees and that never allows

**Figure 1-1**  How a firewall works

even a single unauthorized packet to enter the network. As with any other perfect item, it will be rare to find the perfect set of security policies for firewalls in an enterprise. When developing rules for a firewall, the principle of least access is best to use; you want the firewall to block as much traffic as possible, while allowing the authorized traffic through.

To develop a complete and comprehensive security policy, it is first necessary to have a complete and comprehensive understanding of your network resources and their uses. Once you know how the network will be used, you will have an idea of what to permit. In addition, once you understand what you need to protect, you will have an idea of what to block. Firewalls are designed to block attacks before they reach a target machine. Common targets are web servers, e-mail servers, DNS servers, FTP services, and databases. Each of these has separate functionality, and each has unique vulnerabilities. Once you have decided who should receive what type of traffic and what types should be blocked, you can administer this through the firewall.

### How Do Firewalls Work?

Firewalls enforce the established security policies through a variety of mechanisms, including the following:

- Network Address Translation (NAT)
- Basic packet filtering
- Stateful packet filtering
- Access control lists (ACLs)
- Application layer proxies

One of the most basic security functions provided by a firewall is NAT, which allows you to mask significant amounts of information from outside of the network. This allows an outside entity to communicate with an entity inside the firewall without truly knowing its address. NAT is a technique used in IPv4 to link private IP addresses to public ones. Private IP addresses are sets of IP addresses that can be used by anyone and, by definition, are not routable across the Internet. NAT can assist in security by preventing direct access to devices from outside the firm, without first having the address changed at a NAT device. The benefit is that fewer public IP addresses are needed, and from a security point of view, the internal address structure is not known to the outside world. If a hacker attacks the source address, he is simply attacking the NAT device, not the actual sender of the packet. NAT is described in detail in Chapter 3.

NAT was conceived to resolve an address shortage associated with IPv4 and is considered by many to be unnecessary for IPv6. The added security features of enforcing traffic translation and hiding internal network details from direct outside connections will give NAT life well into the IPv6 timeframe.

Basic packet filtering, the next most common firewall technique, involves looking at packets, their ports, protocols, and source and destination addresses, and checking that information against the rules configured on the firewall. Telnet and FTP connections

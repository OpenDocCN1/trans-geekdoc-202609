# Chapter 5 Hacking MFA in General 131

# Transmission/Network Channel

Most authentication solutions require use a transmission or network channel, especially when network authentication or access is involved. The channel is composed of software and hardware and can be compromised like any other software and hardware.

# Namespace

Most underlying MFA solutions rely on a digital namespace. A namespace is a way of naming, locating, storing, and categorizing objects. Common digital namespaces include Active Directory, Lightweight Directory Protocol (LDAP), Domain Name System (DNS), and Internet Protocol (IP) addresses, others and their components are often referenced in the namespace and used by other involved components in locating and verifying other components. Examples of DNS addresses roger@knowbe4.com, www.knowbe4.com, or www.knowbe4.com/Resources. An example (Distinguished Name) Active Directory could look like CN=Roger, OU=Users, OU=PRDept, DC=knowbe4, DC=com. Namespaces can hold not objects, but also claims, and attributes of objects. Chapter 10, "Subject Hijack Attacks," and Chapter 18, "DNS Hijacking" will cover examples of MFA attacks against namespaces.

# Supporting Infrastructures

Many, if not most, MFA solutions depend on a host of supporting infrastructures, like DHCP, TCP/IP and IP addresses. The routers involved in helping the MFA work across a network router protocols, such as Router Internet Protocol (RIP), Interior Gateway Routing Protocol (IGRP), Enhanced Internet Routing Protocol (EIGRP), Open Shortest Path First (OSPF), Intermediate System to Intermediate System (IS-IS), and Border Gateway Protocol (BGP). Network addresses are converted to physical Media Access Control (MAC) addresses by the Address Protocol (ARP). Most computers get their IP addresses from Dynamic Host Configuration Protocol (DHCP) services. Networked Windows computers use Active Directory services to connect. Linux computers often use LDAP. Apple computers use Bonjour for zero-configuration network services. New USB devices are often automatically registered and recognized because of the Universal Plug-n-Play (UPND) standard.

The idea is that all MFA solutions rely on multiple protocols, standards, and technologies, which they did not invent or control. Each of these technologies and supporting infrastructures can be attacked and hacked to compromise an MFA solution. For example, it is possible for a malicious USB port to rewrite a USB device's firmware instructions or eavesdrop and record the device's data. If you are not familiar with USB firmware hacks, type usb charger hacks in any search engine and to be amazed. Most hacks are simply proof-of-concept
Social engineering is a fancy phrase for lying. It involves tricking someone into sharing confidential information or gaining access to sensitive systems. In many cases, the attacker never comes face to face with the victim. Instead, the attacker might phone an employee and pose as a system administrator. All too often, attackers trick employees into sharing sensitive information. After all, employees think, what's wrong with giving your password to an administrator? You should train your users to recognize social-engineering attacks.

Another reconnaissance tool is the Whois service. This service provides information, such as names and phone numbers of administrators, that can help attackers. FIGURE 7-11 shows the output from a Whois request.

A zone transfer is a unique query of a DNS server that asks it for the contents of its zone. The zone is the domain that the server manages. Administrators often use this tool to synchronize DNS servers within the same organization. If you allow zone transfers without restriction, attackers can use this information to try to figure out the names and types of servers that reside both inside and outside your network. The best defense from this type of information leakage is to lock down your DNS server.

> **NOTE**
> 
> Organizations should be very careful to avoid letting their domain name registration lapse. Someone else might scoop it up and use it as his or her own. Such an action could cause great cost to the organization's reputation. This type of social engineering is a bit more sophisticated than the run-of-the-mill variety.

# Network-Mapping Methods

Network mapping is an extended type of reconnaissance. Network mapping discovers details about a network, including its hosts and host addresses as well as available services. This might enable attackers to identify certain types of systems, applications, services, and configurations. FIGURE 7-12 shows some of the information network mapping may provide.

An attacker can use Internet Control Message Protocol (ICMP; also known as ping) packets to discover a network layout. This gives the attacker an advantage in setting up an attack. As shown in FIGURE 7-13, blocking ping packets, as seen with the Tony router, can prevent the attacker from learning about the network. Of course, this also prevents the administrator from being able to use this valuable tool for network troubleshooting.

FIGURE 7-14 shows how an attacker can discover the services available on a target host using TCP/SYN scans. The attacker sends packets to common ports and can determine from the response whether the host accepts these services.

Attackers need to know what operating system a potential victim is running. The approach to attacking a system differs based on the target operating system. With operating system fingerprinting, an attacker uses port mapping to learn which operating system and version are running on a computer. This can also help an attacker discover computers that might be vulnerable because they don't have patches or may have known exploits. FIGURE 7-15 shows how operating system fingerprinting can provide attackers with valuable information.

# Covert Versus Overt Testers

You can carry out security testing—which can involve both internal and external staff—overtly or covertly. The personnel and methods you use might depend on regulations or on the skill level of internal staff. FIGURE 7-16 shows the various types of testers.
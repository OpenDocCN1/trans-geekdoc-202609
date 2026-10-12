
**D.** Signature verification

11. Which DNS record holds zone replication TTL information?

     **A.** PTR

     **B.** NS

     **C.** MX

     **D.** SOA

12. Which version of SNMP provides built-in security?

     **A.** Version C

     **B.** Version B

     **C.** Version 2

     **D.** Version 3

13. While using Wireshark, you have captured traffic on UDP port 69. What service or application might this be?

     **A.** FTP

     **B.** Finger

     **C.** SSH

     **D.** TFTP

14. Which of the following is not a valid UDP header field?

     **A.** Source port

     **B.** Length

     **C.** Checksum

     **D.** Flag

15. In DNS, what is another name for an alias?

     **A.** MX

     **B.** CNAME

     **C.** SOA

     **D.** NS

16. TSIG is used for what purpose?

     **A.** As a means of authentication updates to a Dynamic DNS database

     **B.** To prevent VLAN hopping

     **C.** As an LDAP security control

     **D.** To secure X.500

17. Cisco has several ways to incorporate VLAN traffic into trunking. These include which of the following?

     **A.** 802.1Q

     **B.** 802.1x

     **C.** 802.11

     **D.** LDAP

18. One of the big differences between IPv4 and IPv6 is the address length. IPv6 has address lengths of how many bits?

     **A.** 16

     **B.** 32

     **C.** 64

     **D.** 128

19. Which of the following is an extension to Simple Object Access Protocol (SOAP) and is designed to add security to web services?

     **A.** WS_Security

     **B.** ESB

     **C.** LDAP

     **D.** SSO

20. Which of the following is not a component of VoIP?

     **A.** SIP

     **B.** H.323

     **C.** RTP

     **D.** SPIT

# Chapter 3: Securing Virtualized, Distributed, and Shared Computing

The following CompTIA CASP exam objectives are covered in this chapter:

1.  ![correct](images/correct.png) **1.2 Explain the security implications associated with enterprise storage**

    *   Storage types
        *   Virtual storage
        *   Cloud storage
        *   Data warehousing
        *   Data archiving
        *   NAS
        *   SAN
        *   vSAN
    *   Storage protocols
        *   iSCSI
        *   FCoE
        *   NFS, CIFS
    *   Secure storage management
        *   Multipath
        *   Snapshots
        *   Deduplication
        *   Dynamic disk pools
        *   LUN masking/mapping
        *   HBA allocation
        *   Offsite or multisite replication

2.  ![correct](images/correct.png) **1.3 Given a scenario, analyze network and security components, concepts and architectures**

    *   Virtual networking and security components
        *   Switches
        *   Firewalls
        *   Wireless controllers
        *   Routers
        *   Proxies
    *   Software defined networking
    *   Cloud managed networks
    *   Advanced configuration of routers, switches and other network devices
        *   Trunking security

3.  ![correct](images/correct.png) **1.4 Given a scenario, select and troubleshoot security controls for hosts**

    *   Trusted OS (e.g. how and when to use it)
    *   Security advantages and disadvantages of virtualizing servers
        *   Type I
        *   Type II
        *   Container-based
    *   Cloud augmented security services
        *   Hash matching
            *   Anti-virus
            *   Anti-spam
            *   Vulnerability scanning
        *   Sandboxing
        *   Content filtering
    *   Vulnerabilities associated with co-mingling of hosts with different security requirements
        *   VM Escape
        *   Privilege elevation
        *   Live VM migration
        *   Data remnants
    *   Virtual Desktop Infrastructure (VDI)
    *   Terminal services/application delivery services
    *   VTPM

4.  ![correct](images/correct.png) **5.1 Given a scenario, integrate hosts, storage, networks, and applications into a secure enterprise architecture**

    *   Technical deployment models (outsourcing/insourcing/managed services/partnership)
        *   Cloud and virtualization considerations and hosting options
            *   Public
            *   Private
            *   Hybrid
            *   Community
            *   Multi-tenancy
            *   Single tenancy
        *   Vulnerabilities associated with a single physical server hosting multiple companies' virtual machines
        *   Vulnerabilities associated with a single platform hosting multiple companies' virtual machines
            *   Secure use of on-demand/elastic cloud computing
            *   Data remnants

## Enterprise Security

The term *enterprise security* refers to a holistic view of security. Our view of IT security has changed over the years in that items such as data security, IT security, and physical security are now seen as just components of a total security solution. Enterprise security is a framework for applying comprehensive controls designed to protect a company while mapping key services to needed information systems. The goals of enterprise security are as follows:

*   To add value to the company
*   To align the goals of IT with the goals of the company
*   To establish accountability
*   To verify that a pyramid of responsibility has been established that starts with the lowest level of employees and builds itself up to top management.

Enterprise security has become much more important in the last decade. It's easy to see why, when you consider the number of security breaches and number of reports of poor security management.

At its most fundamental level, enterprise security is based on confidentiality, integrity, and availability. These three concepts are at the core of information security. *Confidentiality* provides the assurance that only authorized subjects have access to information and data. *Integrity* provides trust that the data is unmodified and correct. *Availability* means that the information or service is available to those with access and that other unauthorized subjects should not be able to make those items unavailable. Other key security services include protection mechanisms, such as authentication and authorization; detection services, such as monitoring and auditing; and incident response and forensics. [Figure 3.1](#c03.xhtml#c03-fig-0001) shows some of the common components of enterprise security.

![FIGURE 3.1 Some of the components of enterprise security](images/c03f001.jpg)

[**FIGURE 3.1**](#c03.xhtml#c03-fig-anc-0001) Some of the components of enterprise security

Information security must support business activities to be of value to an organization. As a subset of corporate governance, it ensures that information security risks are managed. Notice that I use the term "managed." One of the purposes of information security management is to educate about risks an organization is taking and provide countermeasures that enable the business to accept as much risk as suits their goals. Different organizations have varying amounts of risk tolerance. Implementing enterprise security accomplishes the following:

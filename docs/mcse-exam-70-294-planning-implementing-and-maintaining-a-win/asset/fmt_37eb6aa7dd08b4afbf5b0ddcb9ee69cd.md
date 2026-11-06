
## 2.3 Monitor Active Directory replication failures. Tools might include Replication Monitor, Event Viewer, and support tools.

## 2.3.1 Monitor Active Directory replication.

## 2.3.3 Monitor File Replication service (FRS) replication.

## Introduction

In the previous chapter, we saw the logical structure of the network as defined by forests and domains. Sites and the subnets, of which sites are comprised, define the physical structure of an Active Directory network. Sites are important in an enterprise-level multiple location network for creating a topology that optimizes the process of replicating Active Directory information between domain controllers (DCs). Sites are used for replication and for optimizing the authentication process by reducing authentication traffic across slow, high-cost WAN links. Site and subnet information is also used by Active Directory-enabled services to help clients find the nearest service providers.

In this chapter, we discuss the role of sites in the Active Directory infrastructure, and how replication, authentication, and distribution of services information work within and across sites. We explain the relationship of sites with domains and subnets, and how to create sites and site links.

You’ll also learn about site replication and how to plan, create, and manage a replication topology. We’ll walk you through the steps of configuring replication between sites, and discuss how to troubleshoot replication failures.

## Understanding the Role of Sites

In today’s distributed network environment, the communication must always be rapid and reliable. Geographical and other restrictions resulted in the need to create smaller networks, known as subnets. These subnets provide rapid and reliable communication between locations, which can also be attained in larger networks by using Microsoft Windows Server 2003 Active Directory Sites. They ensure rapid and reliable communication by using the methods offered by Microsoft Windows Server 2003 Active Directory Sites to regulate inter-subnet traffic.

A site defines the network structure of a Windows Server 2003 Active Directory. A site consists of multiple Internet Protocol (IP) subnets linked together by rapid and reliable connections. The primary role of sites is to increase the performance of a network by economic and rapid transmission of data. The other roles of sites are replication and authentication. The Active Directory physical structure manages when and how the authentication and replication must take place. The Active Directory physical structure allows the management of Active Directory replication scheduling between sites. The performance of a network is also based on the location of objects and logon authentication as users log on to the network.

![u06-10-9781931836944](images/B978193183694450012X/u06-10-9781931836944.jpg)
Test Day Tip

As a network administrator, you must be familiar with the various roles and services offered by the Active Directory Sites. You needn’t worry about memorizing every detail for this particular exam. What you do have to know are the basics of how each role and services of Active Directory Sites works, and how Active Directory Sites can be used efficiently in terms of data transmission as part of a large network.

### Replication

Replication is defined as the practice of transferring data from a data store present on a source computer to an identical data store present on a destination computer to synchronize the data. In a network, the directory data must live in one or more places on the network to be equally available to all users. The Active Directory directory service manages a replica of directory data on one or more DCs, ensuring the availability of directory data to all users. The Active Directory works on the concept of sites to perform replication efficiently, and uses the Knowledge Consistency Checker (KCC) to choose the best replication topology for the network automatically.

![u06-10-9781931836944](images/B978193183694450012X/u06-10-9781931836944.jpg)
Note

The KCC is a process that runs on a DC, and identifies the most efficient replication topology for the network automatically, based on the data provided by the network in Active Directory Sites and Services.

### Authentication

Authentication is a process by which a system validates users, using the logon information provided. The authentication process includes the confirmation of the source and integrity of information, such as verifying the identity of a user or computer. The information such as user’s name and password are verified with the data available in the system. If the system finds a match, access is granted and an access token is generated that is used to subsequently determine the user’s level of access to objects according to the DACLs on those objects. The granting of the level of access based on permissions is called authorization.

An important characteristic of authentication in the Windows Server 2003 family is its support for single sign\-on. The single sign-on feature allows a user to log on to the network once, using a single password, and authenticate to any computer in a network.

The single sign-on feature offers the following security advantages:

■ For a user, the use of a single password reduces ambiguity and increases the work efficiency of the system.

■ For administrators, the level of administrative support needed for authenticating the domain users is reduced, since the administrator needs only to maintain one account per user.

![u06-11-9781931836944](images/B978193183694450012X/u06-11-9781931836944.jpg)
Exam Warning

Make sure you are familiar with the advantages of the single sign-on feature and how it works.

Windows Server 2003 uses two methods to carry out authentication:

■ Interactive logon authentication

■ Network authentication

![u06-10-9781931836944](images/B978193183694450012X/u06-10-9781931836944.jpg)
Test Day Tip

As a network administrator, you must be familiar with the various authentication mechanisms offered by Active Directory Sites. You needn’t worry about memorizing every detail for this particular exam. What you do have to know are the basics of how each of the authentication mechanisms of the Active Directory Sites works, and how Active Directory Sites can be used efficiently in terms of user authentication in a network.

#### Interactive Logon Authentication

Interactive logon authentication verifies the user’s logon information to either a domain account or to a local computer. This process of authentication is based on the type of user account, such as a domain account or a local computer account:

■ With a domain account, a user logs on to the network by providing logon information such as a password or smart card, using single sign-on data stored in the Active Directory directory service. When a user logs on to the network with a domain account, the user can access resources both in the domain to which he or she logs on and any other trusted domains.

■ With a local computer account, a user logs on to a local computer by providing logon information stored in the Security Accounts Manager (SAM) on the local machine.

![u06-10-9781931836944](images/B978193183694450012X/u06-10-9781931836944.jpg)
Note

SAM is a local security account database for local computer accounts. Local user accounts are usually stored on workstations or servers, and can only be used to access the local computer, not resources on any other computer on the network.

#### Network Authentication

Network authentication verifies the user’s identification to a network service to which the user tries to gain access. To offer this type of authentication, the security system of Windows Server 2003 supports authentication mechanisms:

■ Kerberos V5

■ Secure Socket Layer/Transport Layer Security (SSL/TLS)

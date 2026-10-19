
own technology platform and almost none of which will be designed to interface with the account management service. The process of building all those interfaces will be a daunting, time-consuming, and costly task to overcome and will require the resources of a dedicated team of programmers.

The security practitioner needs to be focused on working with the security architect and the security professional to ensure that there is agreement about which repository for user information will be considered “THE” authoritative repository for the enterprise. Some organizations will consider their HR database to be the repository, while others will use the LDAP system. Still others may not have a formal thought process in place and a system designated. The challenge for the security actors in this regard comes in the form of user decommissioning. When a user leaves the organization, for whatever reasons, the need to have a central system designated that will be where ALL information pertaining to that user will be found and managed is critically important. Things such as group and role based memberships will need to be addressed through this system, as will system access across the enterprise. Without a central authoritative repository to rely on, the security practitioner will not be able to validate that the user has been decommissioned properly, according to the standing policy of the organization. In addition, the security professional will not be able to validate compliance with the security policies of the organization, as well as any overarching legal standards or regulatory requirements that may have to be adhered to.

## Profile Management

Profiles are a collection of information associated with a particular identity or group. In addition to the user ID and password, a user profile may include personal information, such as name, telephone number, email address, home address, date of birth, etc. A profile can also contain information related to privileges and rights on specific systems. However, any information specific to a user is going to change over time, and the process to manage that change is an important component of an overall identity management process. When a change is required to a profile, the process should be easy to manage and be automatically propagated to key systems, such as the corporate directory and the individual systems a user logs into. Most customer relationship management (CRM) systems include some facility to manage user profiles, either administratively or using a self-service method. This capability is also available in some access management systems and password management systems. It is helpful to allow users to enter and manage those parts of their own profiles where new data are either not sensitive or do not have to be validated. This helps to reduce the cost and time to implement these

## X.500

X.500 protocol suite was developed by the telecommunications companies as a way to facilitate a standard method of developing electronic directories for use over telecommunications networks. The suite was originally developed to work with the OSI network communications model, although most current implementations allow it to operate over TCP/IP as well. X.500 actually consists of four separate protocols:

- The Directory Access Protocol (DAP). This is the primary protocol used in an X.500 directory.
- The Directory System Protocol (DSP)
- The Directory Information Shadowing Protocol (DISP)
- The Directory Operational Bindings Management Protocol (DOP)

Information in an X.500 directory is organized as a hierarchical database of information. The key field in the database is called the distinguished name (DN). The DN provides the full path through the X.500 database where a particular entry may be found. X.500 also supports the concept of a relative distinguished name (RDN). The RDN provides the name of a specific entry without the full path component attached.

## LDAP

Although it is a comprehensive suite of protocols for managing directory information, X.500 can be complex to implement and complicated to administer. It also originally required the implementation of the OSI protocol stack for operation. For that reason, organizations wanted a simpler directory protocol that could operate in a TCP/IP environment. In the early 1990s, the lightweight directory access protocol (LDAP) was developed. Based on X.500’s DAP, LDAP provides a simpler implementation of directory services for enterprises.

LDAP uses a hierarchical tree structure for directory entries. Like X.500, LDAP entries support the DN and RDN concepts. DN attributes are typically based on an entity’s DNS name. Each entry in the database has a series of name/value pairs to denote the various attributes associated with each entry. Common attributes for an LDAP entry include the following:

- **DN** – Distinguished Name
- **CN** – Common Name
- **DC** – Domain Component
- **OU** – Organizational Unit

LDAP operates in a client/server architecture. Clients make requests for access to LDAP servers, and the server responds back to the client with results of that request. Standard requests the client can make include connecting and disconnecting to the LDAP service, searching a directory entry, comparing information in the directory, and adding, deleting, or modifying directory information. LDAP typically runs over unsecured network connections using TCP port 389 for communications. If advanced security is required, version 3 of the LDAP protocol supports the use of TLS to encrypt communications.10

## Active Directory Domain Services (ADDS)

Active Directory Domain Services, commonly referred to simply as either the AD or ADDS, is an implementation of the LDAP protocol for Microsoft-based environments. Through the use of additional plug-in services, LDAP directories can also be utilized by many other systems, including UNIX, Linux, and even mainframe environments. ADDS provides central authentication and authorization capabilities for users and system services on an enterprise-wide level. ADDS implementations also have the ability to enforce organizational security and configuration policies across an enterprise. For that reason, many organizations use their ADDS implementations to enforce user and system-level security policies in a uniform and highly auditable manner.

ADDS uses LDAP for its naming structure. Like LDAP, ADDS uses a hierarchical framework to store information. ADDS directories are organized into forests and trees. A forest is a collection of all the objects and their associated attributes, and trees are logical groupings of one or more ADDS security domains within a forest. Domains in ADDS are identified by their DNS name. Objects in an ADDS database are grouped by Organizational Units.

## X.400

X.400 is a set of ITU-T guidelines for the exchange of email, known in parlance as Message Handling Systems (MHS). X.400 was originally developed in the early 1980s and designed to run on OSI-based networks. As with X.500, most X.400 systems currently in use have the ability to run in TCP/IP-based environments as well.

The X.400 protocol supports two primary functions: message transfer and message storage. X.400 addresses consist of a series of name/value pairs separated by semicolons. Typical elements of an address specification include:

- O — Organization name
- OU — Organizational Unit names
- **G** — Given name
- **I** — Initials
- **S** — Surname
- **C** — Country name

The implementation of security features was an early part of the X.400 specification, and early implementations included features related to message privacy and message integrity. These features were implemented in X.400 far earlier than in the next most common messaging protocol, SMTP. However, while X.400-based systems initially became popular in many parts of the world, they have been largely supplanted in recent years by SMTP-based email systems.

## Single Sign-On

Single sign-on (SSO) is a term used to describe a unified login experience (from the viewpoint of the end-user) when accessing one or more systems. Single sign-on is often referred to as reduced sign-on or federated ID management. Some network enterprise systems provide users with access to many different computer systems or applications for their daily work. This wide range of access may require the user to have a user ID and password for each available resource. Users who often log into many systems will prefer to sign into one master system and thereafter be able to access other systems without being repeatedly prompted to identify and authenticate themselves. There are numerous technical solutions that offer SSO to users, but most are associated with the centralization of user data, such as a centralized directory service. As previously discussed, many legacy systems do not support an external means to identify and authenticate users. Therefore, an SSO solution for these systems will need to store the credentials outside of the various applications and have them automatically entered on behalf of the user when an application is launched. Figure 5.1 shows the architecture for a typical SSO system.

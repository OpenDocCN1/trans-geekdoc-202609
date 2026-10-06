# CHAPTER 25 MIGRATING, MERGING, AND MODIFYING YOUR ACTIVE DIRECTORY

The swing migration involves these basic steps:

+   1. Prep the forest's schema to be compatible with Windows Server 2012.
2. Prep the domain for Windows Server 2012.
3. Prep the original domain controller for possible decommission or change of configuration.
4. Prep the new member server and add the Domain Controller role, followed by running DCPromo.
5. Perform post-migration procedures considering FSMO placement, IP address changes, or other changes.
6. Redeeploy the source domain controller as necessary.

# PREPPING THE FOREST/SCHEMA AND DOMAIN

As with the in-place upgrade, the existing forest and target domain need to be prepared for Windows Server 2012's Active Directory changes. You must run ForestPrep, DomainPrep, and GPrep, but with Windows Server 2012 when you add the Active Directory Services role it will run automatically, similarly to what we discussed in the “Migrating with an In-Place Upgrade” section.
Rollback points of all of the game are the same as for the in-place upgrade. You must restore the system state data on the schema master domain controller.

# BUILDING A WINDOWS SERVER 2012 MEMBER SERVER

The new Domain Controller will start as a Windows Server 2012 member server in the original domain. In preparation, you will need to install the Active Directory Domain Services role and DNS role prior to running the Active Directory Roles process.

# VERIFYING DNS

Since the new domain controller will support DNS, you should add it as a name server to the applicable forward and reverse zones. Once the member server is promoted as a domain controller, the DNS zones will be replicated.
To ensure proper name resolution of the domain controllers, you should test DNS resolution. Perform checks of the service resource records using nslookup and nsdig that we covered earlier in this chapter, in 5, “IP Address Management (IPAM) and DHCP Fail-over.”

# PREPPING THE SOURCE DOMAIN CONTROLLER

You should plan for what will be done with the source domain controller prior to the operation. If the server is to remain in the domain as a domain controller, little needs to be done. If it will be redeployed, you must consider how to replace the network's reliance on this server.
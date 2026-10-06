You can verify (and upgrade if needed) the domain functional level that your domain is currently using with the following steps:

+   1. Log onto a domain controller.
2. Launch Active Directory Users and Computers by selecting Server Manager > Tools > Active Directory Users and Computers.
3. Right-click the domain name, and Raise Domain Functional Level. Your display will look similar to Figure 23.6.

FIGURE 23.6
Verifying the domain functional level

![](bbox=[0.459, 0.285, 0.841, 0.489])

In the figure, the current domain functional level is Windows Server 2012 R2 and the domain is operating at the highest possible functional level until the next Windows Server release.

+   4. If the domain functional level is not at least Windows Server 2003, raise it to Windows Server 2003 by selecting Windows Server 2003 and clicking Raising.

Recalling previous prerequisites for a RODC, the domain functional level must be at least Windows Server 2003 for you to be able to use RODCs.

You need to raise the domain functional level on only one domain controller in the domain. It will replicate to all domain controllers within a short period of time.
If all controllers aren't running at least Windows Server 2012 R2, you won't be able to raise the domain functional level to Windows Server 2012 R2. After you click the Raise button, you will receive an error. Domain controllers running older operating systems will need to be removed from the domain or upgraded.

# FOREST FUNCTIONAL LEVELS

Just as domain functional levels provide different capabilities, forest functional levels provide different capabilities. The different forest functional levels are:

+   **Windows Server 2003** Used when all domains are running at least least Windows Server 2003 domain functional level. As a reminder, this is the minimum forest functional level required to support RODCs.
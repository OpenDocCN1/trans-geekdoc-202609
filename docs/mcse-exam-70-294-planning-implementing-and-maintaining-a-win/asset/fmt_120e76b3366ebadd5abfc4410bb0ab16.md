
# Creating a New Domain Tree in an Existing Forest

This will often be the second domain that you install, as shown in [Figure 4.17](#B9781931836944500106_1.xhtml#f0090). This type of arrangement accommodates a forest comprised of two different company divisions, or two companies within a larger corporation. Domains are used as boundaries for security and administration. With the procedure in [Exercise 4.06](#B9781931836944500106_1.xhtml#b0035), you will simultaneously create your first nonroot top–level domain, and the second tree in your forest. Note that a new bidirectional, transitive trust is automatically created with the forest root.

![Figure 4.17 Creating a New Domain Tree in an Existing Forest](images/B9781931836944500106/f04-17-9781931836944.jpg)
Figure 4.17 Creating a New Domain Tree in an Existing Forest

## Exercise 4.06
### Creating A New Domain Tree in AN Existing Forest

1. Log in as a local Administrator.
2. Click `Start | Run`.
3. Type `dcpromo`.
4. Click OK to start the Active Directory Installation Wizard.
5. In the Welcome to the Active Directory Installation Wizard window, click Next.
6. In the Operating System Compatibility window, click Next.
7. In the Domain Controller Type window, click Domain controller for a new domain | Next, as shown in [Figure 4.18](#B9781931836944500106_1.xhtml#f0095).
![Figure 4.18 The Domain ControllerType Dialog Box Used for a New Domain Tree in an Existing Forest](images/B9781931836944500106/f04-18-9781931836944.jpg)
Figure 4.18 The Domain ControllerType Dialog Box Used for a New Domain Tree in an Existing Forest
8. In the Create New Domain window, click Domain in an existing forest | Next, as shown in [Figure 4.19](#B9781931836944500106_1.xhtml#f0100).
![Figure 4.19 The Create New Domain Dialog Box Used for a New Domain Tree in an Existing Forest](images/B9781931836944500106/f04-19-9781931836944.jpg)
Figure 4.19 The Create New Domain Dialog Box Used for a New Domain Tree in an Existing Forest
9. In the Network Credentials window, type in the username, password, and domain name of an Enterprise Administrator or Domain Admin in the forest-root domain. Click Next.
10. In the New Domain Tree window, type the full DNS domain name for the new domain, and click Next.
11. In the NetBIOS Domain Name window, verify the NetBIOS name and click Next. The default name is generally the best one to use.
12. In the Database and Log Folders window, type or browse to the location where you want the database and log folders. Click Next.
13. In the Shared System Volume window, type or browse to the location where you want the `SYSVOL` folder. Click Next.
14. In the DNS Registration Diagnostics window, configure an existing DNS server to be authoritative for this tree, or click Install and configure the DNS server on this computer, and set this computer to use this DNS server as its preferred DNS server. Click Next, as shown in [Figure 4.20](#B9781931836944500106_1.xhtml#f0105).
![Figure 4.20 The DNS Registration Diagnostics Dialog Box Used for a New Domain Tree in an Existing Forest](images/B9781931836944500106/f04-20-9781931836944.jpg)
Figure 4.20 The DNS Registration Diagnostics Dialog Box Used for a New Domain Tree in an Existing Forest
15. In the Permissions window you have two options: Permissions compatible with pre-Windows 2000 server operating systems and Permissions compatible only with Windows 2000 or Windows Server 2003 operating systems. Select one, and then click Next.
16. In the Directory Services Restore Mode Administrator Password window, input and confirm the password for the Directory Services Restore Mode. Click Next.
17. Read the Summary window. Click Next, as shown in [Figure 4.21](#B9781931836944500106_1.xhtml#f0110). The installation will continue for several minutes.
![Figure 4.21 The Summary Dialog Box Used for a New Domain Tree in an Existing Forest](images/B9781931836944500106/f04-21-9781931836944.jpg)
Figure 4.21 The Summary Dialog Box Used for a New Domain Tree in an Existing Forest
18. Restart your new DC.
19. Verify that the installation was successful. Open a command prompt and enter the `Net Share` command. It should report the existence of the `Netlogon` and `SYSVOL` shares. To verify that the DNS service locator records for the new DC were successfully created, follow these steps:
1. Click `Start | Administrative Tools | DNS` to start the DNS administrator console.
2. Expand the server name.
3. Expand Forward Lookup Zones.
4. Expand the domain.
5. Verify that the `\_msdcs`, `\_sites`, `\_tcp`, and `\_udp` folders are present and contain records for your new DC. These service location records are crucial to the operation of the DC. See [Table 4.7](#B9781931836944500106_2.xhtml#t0040) for a more detailed description of the required records, and [Figure 4.16](#B9781931836944500106_1.xhtml#f0085) for a view of the DNS administrator tool used to view them.

# Creating a New Child Domain in an Existing Domain

This will often be the third domain that you install, as shown in [Figure 4.22](#B9781931836944500106_1.xhtml#f0115). This type of arrangement accommodates a tree comprised of two different company groups, sometimes in physically separate locations. Since domains are used as boundaries for security and administration, there are many reasons for segregating a subgroup. If a group requires higher or lower levels of security, or if a different group of administrators requires complete control, then a child domain is a good idea. With the procedure in [Exercise 4.07](#B9781931836944500106_1.xhtml#b0040), you will create your first child domain within any existing tree of your forest. Note that a new bidirectional, transitive trust is automatically created with the parent domain, simultaneously creating an implicit trust between the child domain and the forest-root. See the section Establishing Trust Relationships later in this chapter for more information on the transitivity and direction of trusts.

![Figure 4.22 Creating a New Child Domain in an Existing Domain](images/B9781931836944500106/f04-22-9781931836944.jpg)
Figure 4.22 Creating a New Child Domain in an Existing Domain

## Exercise 4.07
### Creating a New Child Domain in an Existing Domain

1. Log in as a local Administrator.
2. Click `Start | Run`.
3. Type `dcpromo`.
4. Click OK to start the Active Directory Installation Wizard.
5. In the Welcome to the Active Directory Installation Wizard window, click Next.
6. In the Operating System Compatibility window, click Next.
7. In the Domain Controller Type window, click Domain controller for a new domain | Next, as shown in [Figure 4.23](#B9781931836944500106_1.xhtml#f0120).
![Figure 4.23 The Domain Controller Type Dialog Box Used for a New Child Domain in an Existing Domain](images/B9781931836944500106/f04-23-9781931836944.jpg)
Figure 4.23 The Domain Controller Type Dialog Box Used for a New Child Domain in an Existing Domain
8. In the Create New Domain window, click Child Domain in an existing domain tree | Next, as shown in [Figure 4.24](#B9781931836944500106_1.xhtml#f0125).
![Figure 4.24 The Create New Domain Dialog Box Used for a New Child Domain in an Existing Domain](images/B9781931836944500106/f04-24-9781931836944.jpg)
Figure 4.24 The Create New Domain Dialog Box Used for a New Child Domain in an Existing Domain
9. In the Network Credentials window, type in the username, password, and domain name of an Enterprise Administrator in the forest-root domain, or a Domain Admin in the parent domain, and click Next.
10. In the Child Domain Installation window, verify the parent domain and type the name of the new child domain. Click Next, as shown in [Figure 4.25](#B9781931836944500106_1.xhtml#f0130).
![Figure 4.25 The Child Domain Installation Dialog Box Used for a New Child Domain in an Existing Domain](images/B9781931836944500106/f04-25-9781931836944.jpg)

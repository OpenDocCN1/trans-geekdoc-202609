
## 3. A large company has just merged with yours.
They have a corporate 24-hour Enterprise Administrators group running a forest at the Windows Server 2003 functional level. Your company has NT, 2000, and XP clients on a single NT domain. Your PDC and four of your five BDCs are still running Windows NT. Two of your permissions groups have more than 5000 members. The new conglomerate has given you a budget for upgrading the local infrastructure so that you can participate in the corporate forest structure through a cross-forest trust. What are the minimum requirements you must meet before joining the corporate forest? (Choose all that apply.)
A. Ask the Enterprise Administrators to temporarily set their forest to interim level using manual LDAP administrative tools.
B. Install new servers and create a pristine local forest root using your namespace.
C. Upgrade your PDC to Windows Server 2003, and join the corporate forest during the upgrade.
D. Upgrade your four Windows NT BDCs to Window’s Server 2003.

## 4. Two forests are joined with a cross-forest trust, linking the two for resource sharing.
Both forests synchronize their time with the Internet, they both contain some Windows NT 4.0 workstations, and they reside in different time zones. One day, the cross-forest trust fails, and users cannot authenticate across their forest boundaries, although the network is healthy at layer 3. What might have happened?
A. The two forests are using different time sources, or one forest-root PDC emulator has malfunctioned.
B. The Windows NT systems need to reboot, or use the scheduler service to run the `net time \\\\<timecomputer> /set /yes` command on each NT machine.
C. DCs in both forests should be set up to automatically run the `w32tm /config /syncfromflags: manual /manualpeerlist:.Peerlist` command, listing only each other as their time source.
D. The PDC Emulator needs its time reset, since Windows NT 4.0 workstations and servers automatically synchronize with their PDC.
E. The scenario is impossible, since Windows NT cannot function in a Window’s Server 2003 functional level domain, and cross-forest trusts can only be created in such a domain.

## 5. Your IT manager wants you to link four divisions of the company through a ring of eight unidirectional cross-forest trusts.
He uses this reasoning: If multiple forest trusts are established, then authentication requests made in any domain of any forest can pass through multiple forest trusts, hence multiple Kerberos domains, on their way to their destination. Why is he wrong?
A. While each cross-forest trust is transitive at the forest level, where all domains in both forests can authenticate, they are not transitive at the federated forest level as he suggests. The trust path cannot include more than one cross-forest trust.
B. Cross-forest trusts are not transitive, and will not allow pass-through authentication.
C. To create a ring of trust around four forests, you only need four cross-forest trusts.
D. Cross-forest trusts are bidirectional, so only three trusts are needed to link all four forests. Completing the “ring” is not necessary.

## 6. You are the database administrator for a large enterprise, and you are trying to install an Active Directory-integrated application.
The product literature says it implements new classes within the directory. The installation fails with an obscure message. What is the most likely reason for the failure?
A. The application uses a service account that is not a member of the Enterprise Administrators group.
B. You are not a member of the Domain Admins account in the domain where you are trying to install the application.
C. You are not in the Schema Administrators group.
D. You do not have permissions to create GPOs.

## 7. What FSMO roles should exist in a child domain in a Windows Server 2003 forest? (Choose all that apply.)
A. Schema Master
B. Domain Naming Master
C. PDC Emulator
D. RID Master
E. GC
F. Infrastructure Master

## Creating the Forest and Domain Structure
## 8. Your company is expanding its single location with five new offices, all in different states.
Each location will have 10 marketing employees or less to supplement the 25 already employed at the main office. Your security engineer says that all employees will abide by the same company security policy They will hire another systems administrator at your office to handle the increased workload. When asked about how the company’s single-domain Windows Server 2003 Active Directory will be affected by the expansion, you reply that new servers will have to be installed at the remote locations. Your manager wants to know what server hardware and software to budget for. What do you tell him? (Choose one).
A. Five servers and five copies of Windows Server 2003 Datacenter Edition
B. Five servers and five copies of Windows Server 2003 Standard
C. Ten servers and ten copies of Windows Server 2003 Enterprise Edition
D. Ten servers and ten copies of Windows Server 2003 Standard

## 9. You have just been hired to install an Active Directory for a new startup company.
An e-commerce Web farm has already been set up, waiting to join your root domain. [`Walleyedhucklemullys.com`](http://www.Walleyedhucklemullys.com) employs seven chemists who appear to split their rime evenly between research and development activities, two Web developers, one network engineer, and the owner of the company. The previous MCSE who ordered the computers and software has already left the company, and all you have is a pile of boxes and a crude sketch of a logical Active Directory forest. The owner of the company has already approved the design and wants you to work all weekend to make it work. After you clean up the drawing somewhat, it looks like Figure 4.57. Among the boxes you find six computers, three copies of Windows Server 2003 Standard, and three copies of Windows Server 2003 Web Edition. Under the pressure of time, you create the forest structure with two computers in each of the three domains. On Monday morning, you approach your new manager to say that the Active Directory design is weak. What is wrong with it? (Choose all that apply.)
A. DNS should be split, and the design is full of bad namespace and computer security practices.
B. Too many domains.
C. You should have installed Windows Server 2003 Enterprise instead of Standard.
D. Firewall is in the wrong place, because Web servers should be direcdy on the Internet.
E. Not enough DCs for the number of domains.

![Figure 4.57 Question #9 Diagram](images/B9781931836944500106/f04-57-9781931836944.jpg)
Figure 4.57 Question #9 Diagram

## 10. The name of your company has changed from Fish to Aquatics.
In her zeal to embrace the new company image, your CEO directs you to change the Active Directory domain name to reflect the new company name. You efforts are unsuccessful. Which of the following would cause the domain rename tool to fail? (Choose all that apply.)
A. Your DCs are running Windows Server 2000 Enterprise Edition.
B. The Active Directory forest functional level is set to Windows Server 2003 interim.
C. You are logged in as a Domain Admin.
D. Your current mail server is running Exchange 2000.
E. Your DFS root server is running Windows 2000 with Service Pack 3.
F. You are logged on to a Windows 2003 Server DC as an Enterprise Admin.

## 11. Your network operations center has identified excessive bandwidth utilization caused by authentication traffic in the root domain subnet, especially between [`Cahco.cats.com`](http://www.Cahco.cats.com) and `Labs.dogs.com`.
Your logical network is set up as shown in Figure 4.58. What type of trust or trusts would you set up to alleviate the situation?
A. Set up a bidirectional transitive parent and child trust between [`Calico.cats.com`](http://www.Calico.cats.com) and [`Labs.dogs.com`](http://www.Labs.dogs.com).


☑ B. If a user has been issued the Add workstations to a domain right, he or she has the ability to configure computers to join the domain. When adding computers to the domain, the user can create up to 10 computer accounts.
![wrong](images/wrong.png) Answer A is incorrect, because a user can create up to 10 computer accounts in a domain. Answer C is incorrect, because for a user to create an unlimited number of computer accounts, he or she would need to be a member of the Account Operators group, Domain Admins group Enterprise Admins group, or be granted additional special permissions, specifically the ability to Create Computer objects in the AD computers containers. Answer D is incorrect, because a user can create up to 10 computer accounts in a domain.
13. A new computer account is created in `Active Directory Users and Computers` for a workstation running Windows 2000 Professional. When viewing its properties, you check the Member Of tab and see that it is already included in the membership of a group. Which of the following groups is this account a member of?
A. Domain Users
B. Domain Computers
C. Domain Controllers
D. Enterprise Admins
☑ B. When a computer account is created, it is automatically made a member of the Domain Computers group. It is not a member of other groups, although you can add it to the membership of additional groups through the Member Of tab in the computer account s properties.
![wrong](images/wrong.png) Answer A is incorrect. This is the default group of which all user accounts are members. Answer C is incorrect, because the Domain Controllers group consists of all DCs within the domain. Answer D is incorrect, because the Enterprise Admins group is an administration group with great control over domains in a forest. For this reason, accounts are not automatically added to it upon creation.
### Managing Multiple Accounts
14. Your company has an external DNS domain that is used for the company’s Web site, and an internal DNS domain that is used for the network. The external DNS domain is hosted on a UNIX server that hosts the company’s Web site. The Web site using this external domain name is well known, and due to its popularity, users are confused as to which domain to log on to. Which of the following can you do to allow users to log on to the internal network using the external domain name?
A. Use `DSADD` to add users to the external DNS domain.
B. Use `MOVETREE` to add users to the external DNS domain.
C. Use `Active Directory Users and Computers` to create an alternate UPN suffix.
D. Use `Active Directory Domains and Trusts` to create an alternate UPN suffix.
☑ D. Use `Active Directory Domains and Trusts` to create an alternate UPN suffix. A UPN suffix is part of the `upn` that is used for logging on to a domain. The logon name indicates the account that’s being logged on with. Alternative UPN suffixes can be created using `Active Directory Domains and Trusts`, so users can log on to their domain using a different UPN suffix. In this case, the alternate UPN suffix could be the same name as the external DNS domain, and can then be used by users to log on to the internal Active Directory domain.
![wrong](images/wrong.png) Answer A is incorrect, because `DSADD` is used to add new objects to Active Directory. Because the external DNS address is hosted on a UNIX server that isn’t connected to the internal network, this tool cannot be used. Answer B is incorrect, because `MOVETREE` is used to move objects between different domains within a forest. It cannot be used for managing domain names that are hosted by UNIX servers. Answer C is incorrect, because `Active Directory Users and Computers` isn’t used to create alternate UPN suffixes.
15. You want to move a user account from an OU located in one domain, to an OU located in another domain. Which of the following tools will you use to perform this task?
A. `Active Directory Users and Computers`
B. `Active Directory Domains and Trusts`
C. `DSMOVE`
D. `MOVETREE`
☑ D. `MOVETREE` is the Active Directory Object Manager, which is a command-line tool that allows you to move objects from one location in Active Directory to another. Using this tool, you can move an object from an OU in one domain to an OU located in another domain.
![wrong](images/wrong.png) Answers A and C are incorrect because both of these tools can only move objects within a domain. `Active Directory Users and Computers` is a graphical tool, while `DSMOVE` is a command-line tool. With both of these, you can move an object from one location in the directory tree to another location, but you can’t move them to locations in other domains. Answer B is also incorrect, because `Active Directory Domains and Trusts` isn’t used to move accounts within Active Directory.
## Chapter 3 Creating User and Group Strategies
### Creating a Password Policy for Domain Users
1. What is a potential drawback of creating a password policy on your network that requires user passwords to be 25 characters long?
A. Users will be more likely to write down a password that is so difficult to remember.
B. User passwords should be at least 30 characters long to guard against brute-force password attacks.
C. There are no drawbacks; this solution creates network passwords that will be impossible for an unauthorized user to penetrate.
D. Windows Server 2003 will not allow a password of more than eight characters.
☑ A. A 25-character password is unreasonably long for most environments, and could prompt your users to write them down. Passwords that are written down can be discovered, especially if they are stored near the computer. This can easily render the use of strong passwords meaningless.
![wrong](images/wrong.png) Answer B is incorrect. A password length of 8 to 14 characters is usually sufficient to guard against most brute-force attacks. Answer C is also incorrect. A 25-character password will create the issues described in Answer A. Answer D is incorrect because Windows passwords can be up to 255 characters in length.
2. You have recently started a new position as a network administrator for a Windows Server 2003 network. Shortly before the previous administrator left the company, the `syskey` utility was used on one of your domain controllers to create a password that needs to be entered when the machine is booted. You reboot the domain controller, only to discover that the password the previous administrator documented is incorrect. You are unable to contact your predecessor to obtain the correct one. How can you return this DC to service as quickly as possible?
A. Reformat the system drive on the server and reinstall Windows Server 2003.
B. Boot the server into Directory Services Restore Mode and restore the DC from a point before the previous administrator ran the `syskey` utility.
C. Boot the server into Safe Mode and run `syskey` again to change the password.
D. Use `ntdsutil` to seize the PDC Emulator role and transfer it to another DC.
☑ B. If you misplace the password or diskette that’s created when you run the `syskey` utility, your only option is to restore the system from a point before the `syskey` utility was run.
![wrong](images/wrong.png) Answer A is incorrect. It is not the quickest way to restore the DC to service, because you will lose application and Registry data stored on the system drive. All applications will need to be reinstalled and any shares recreated. Answer C is also incorrect. You cannot change the `syskey` password without knowing the original one. This is by design so that an attacker cannot circumvent `syskey` security by simply rebooting the server. Answer D is incorrect because transferring the PDC Emulator role will do nothing to return this DC to service.
3. According to Microsoft, which of the following would be considered weak passwords for a user account named `jronick`? (Choose all that apply.)
A. S#n$lUsN7
B. soprano
C. ronickij
D. Oo!dIx2
E. new

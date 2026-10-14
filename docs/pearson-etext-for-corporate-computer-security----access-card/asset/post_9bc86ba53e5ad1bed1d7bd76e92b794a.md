
## PATCH MANAGEMENT SERVERS

Faced with overwhelming patching loads, many companies now use internal patch management servers. Patch management servers learn what software is running on the firm’s servers. Patch management servers then actively assess what programs on each host need to be patched and push patches out to the servers. Patch management servers can greatly reduce patching costs.

In corporate environments using Windows Server, it is possible to manage patches, hotfixes, and updates through Windows Server Update Services (WSUS). It allows systems administrators to manage the download, distribution, and application from a centrally managed server (Figure 7-14). Administrators can make sure each machine is updated and apply patches when appropriate.

## THE RISKS OF PATCH INSTALLATION

Installing patches is not without its own risks. First, added security often comes at the cost of reduced functionality, which might not be justified given the degree of added safety offered by a patch.

Second, some patches actually freeze machines or do other damage. This is particularly bad if a patch has no uninstall option. Firms typically download a patch on a test system and examine the effects of the patch thoroughly before rolling the patch out to all servers or clients. If a company has a standard security baseline for various types of hosts, chances are good that experiences on the test system will mirror those on other hosts.

## Test Your Understanding

- 8. a. Why do firms have a difficult time applying patches?
- b. Why do many firms prioritize patches?
- c. How do patch management servers help?
- d. What two risks does patching raise?

## 7.4 Managing Users and Groups

7.4 Explain how to manage users and groups.

## The Importance of Groups in Security Management

The next aspect of host hardening we will discuss is creating and managing user accounts and groups. Every user must have an account. In addition, it is common to create groups and then add individual users to these groups. When security measures, such as requiring long and complex passwords, are applied to groups, all users in these groups are automatically subjected to these measures. Applying security measures to groups obviously requires much less labor than applying these measures to accounts individually.

Applying measures to groups also tends to reduce errors because most groups have well-defined roles that lead to clear security requirements. Individuals, by contrast, may have multiple roles with different security requirements, making it difficult to assign proper security settings to individual accounts.

## Test Your Understanding

- 9. Give two reasons why assigning security measures to groups is better than assigning security measures to individuals within groups.

## Creating and Managing Users and Groups in Windows

For stand-alone Windows servers, an administrator can turn to the Computer Management MMC. As Figure 7-16 shows, there is a Local Users and Groups snap-in with two subcategories—Users and Groups. The Users category is selected.

In the right pane, a list of users is shown. The Administrator user is selected. If the systems administrator selects the Action menu or right-clicks any account, he or she will be able to rename the account, delete it, change its security properties, or take other actions.

## THE ADMINISTRATOR ACCOUNT

Each operating system has a super user account that has total control over the computer. In Windows, the super user account is administrator. In UNIX, it is the root account.

Anyone logging into the super user account has total control of the computer. He or she can see everything and change anything. Consequently, the main goal of hackers is to take over the super user account. Because hacking began on UNIX computers, taking over the super user account on any computer is called hacking root.

To minimize dangers, systems administrators should use the super user account as little as possible. Whenever they do not require super user powers, they should work with individual personal accounts that have few privileges. Only when they need super user permissions should they log into the super user account.

In Windows Server, the RunAs command allows them to switch between running as administrator and working with their normal account. In UNIX, the su (switch user) command can switch the systems administrator between the root account and his or her limited personal accounts.

## MANAGING ACCOUNTS

Figure 7-18 shows what happens if the systems administrator right-clicks on an account (in this case, the Administrator account) and selects Properties. This action will take the user to the dialog box shown in the figure. The General tab (shown) allows the systems administrator to place password restrictions on the user. Another tab allows the systems administrator to add the user account to multiple groups.

## CREATING USERS

The Action command (see Figure 7-16) allows new user accounts to be created. To create a new account, the systems administrator will enter an account name, a password, and other information about the account.

## WINDOWS GROUPS

In Figure 7-16, selecting the Groups choice instead of Users will show a list of groups. The systems administrator will be able to look at each group to see its members, then add to or delete members from the group.

- **Accounts**
- Every user must have an account
- **Groups**
- Individual accounts can be consolidated into groups
- Can assign security measures to groups
- Inherited by each group's individual members
- **Why Assign Security Measures to Groups?**
- Reduces labor costs compared to assigning security measures to individual accounts
- Assigning permissions to groups reduces errors
- Because group permissions are more obvious than individual permissions

Figure 7-15 Managing Users and Groups (Study Figure)

## Figure 7-16 Users and Groups in Windows

![](img/073342643701cc54eb7875c41ab92ef2_365_0.png)

> **Super User Account**  
> Every operating system has a super user account  
> The owner of this account can see or do anything on the computer  
> Called administrator in Windows  
> Called root in UNIX  
> 
> **Hacking Root**  
> Goal is to take over the super user account  
> Will then “own the box”  
> Generically called hacking root  
> 
> **Appropriate Use of a Super User Account**  
> Log in as an ordinary user  
> Switch to super user only when needed  
> In Windows, the command is **RunAs**  
> In UNIX, the command is **su** (switch user)  
> Quickly revert to ordinary account when super user privileges are no longer needed

## Figure 7-17 The Super User Account (Study Figure)

## Figure 7-18 Windows User Account Properties

![](img/073342643701cc54eb7875c41ab92ef2_365_1.png)

## Test Your Understanding

- 10.
- a. What Windows snap-in is used to manage users and groups?
- b. On which MMC is this snap-in available?
- c. In this snap-in, if the administrator clicks on an account, what may he or she do?
- d. How does the administrator create a new account?
- e. How does an administrator add an account to a group?
- f. How does the administrator create a new group?

- 11.
- a. What privileges does the super user account have?
- b. What is the super user account in Windows?
- c. What is the super user account in UNIX?
- d. What is hacking root, and why is it desirable to hackers?
- e. When should a Windows systems administrator use the Administrator account?
- f. How does the administrator get to the super user account in Windows? In UNIX?

## 7.5 Managing Permissions

7.5 Explain how to manage permissions.

### Permissions

Just because someone logs in correctly does not mean that they should have free rein to do anything they wish on the server. To each account and group, systems administrators assign **permissions**, which specify what the user or group can do and not do to files, directories, and subdirectories. Permissions can range from not even being able to see a directory to being allowed to do everything to it.

> Permissions specify what the user or group can do or not do to files, directories, and subdirectories.

![](img/073342643701cc54eb7875c41ab92ef2_366_0.png)

Figure 7-19 Managing Permissions in Windows (Study Figure)

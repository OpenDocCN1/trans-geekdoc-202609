
# FIGURE 9.48

Giving the power to reset words

![](img/41a83208e6906a3732620203b836cea7_566_0.png)

# The Bottom Line

Understand local policies and Group Policy objects. Every computer from Windows 2000 Professional and later has a local group policy. Windows 8 has many local group policies, which can accommodate for various situations where the computer might be located. There are Group Policy objects stored in Active Directory too, which allow for central administration of computers and users who are associated with the domain.

**Master IT** Which of the following is not a group policy?

- Local Computer Policy
- Administrator
- Non-Administrator
- All Users

**Create GPOs.** Group Policy objects can be created within your Active Directory domain. These GPOs allow you to control settings, software, and security on the different users and computers that you have within the domain. GPOs are typically linked to OUs but can be linked to the domain name and AD sites. GPOs are created within AD by using the Group Policy Management console.

**Master IT** Create a new GPO and link it to the HRUsers OU.

Trouhoot group policies. At times a GPO setting or group policy fails to apply. There can be many reasons for this, and you can use many tools to investigate the issue. Some tools, such as the rsop.msc tool, are presented in a resulting window, and others such as gpresult, are used on the command line. Regardless of the tool you use, troubleshooting Group Policy is sometimes required.

**Master It** Which tool would you use to ensure that all settings in all GPOs linked to Active Directory have applied, even if there have not been any changes to a GPO or a setting in a GPO?

**Delegate control using organizational units.** Delegation is a powerful feature in Active Directory that allows domain administrators to delegate tasks to junior administrators. The idea is that the delegation is narrow in scope, providing only limited capabilities within Active Directory and the objects contained within.

**Master It** Establish delegation on organizational unit such that HelpDesk security group can reset passwords for all users in the HRUsers OU.

**Advanced delegation manually.** There are thousands of individual permissions for any given AD object. Advanced delegation provides the ability to set any of these permissions to give a user or security group access to the specified object. Delegation Control Wizard is a useful tool to grant common tasks, but when the wizard does not provide the level of detail required, you must grant delegation manually.

**Master It** Delegation is another term for which of the following?

- Replicating AD database
- Read-only domain controller
- Setting permissions on AD
- Using Group Policy

**Find out which delegations have been set.** It is unfortunate, but Delegation Control Wizard is a tool that can only grant permissions, not report what has been set. To find out what delegations have been set, you have to use other tools.

**Master It** Name a tool that you can use to view what delegations have been set.

# Chapter 10

## Active Directory Federation Services

Active Directory has made managing domains so much easier and connecting to multiple organizations easily in a secure manner. Since Windows Server 2003, Active Directory Federation Services (AD FS) is a software component developed by Microsoft that can be installed on Windows Server to provide users with single sign-on (SSO) to applications and services across boundaries that were previously unreachable with a single login. AD FS issues a secure token to an entity, allowing it to cross multiple forests and authenticate into applications and websites. Windows Server 2012 R2 has taken the ability to federate multiple AD forests and expanded functionality, allowing organizations to manage identities across multiple platforms around the world. As you can imagine, trying to manage all identities across a large realm of directories can be difficult. Luckily for us, Microsoft continues to provide excellent directory synchronization tools like Federation Identity Manager (FIM). FIM allows organizations to synchronize identity information across a multitude of heterogeneous directory stores. In this chapter we will take a deep dive into working with AD FS. You will learn to:

- Install the AD FS role on a server
- Configure the first federation server in a farm
- Configure AD FS performance monitoring

# Understanding AD FS Key Components and Terminology

Before we jump in and start building out an AD FS implementation, it’s a good idea to go over the key components and terminology that will be used throughout this chapter. AD FS uses terminology from multiple technologies, including Internet Services (IIS), Active Directory Domain Services (AD DS), Active Directory Certificate Services (AD CS), Active Directory Lightweight Directory Services (AD LDS), and Web Services. Following is a list of terms and definitions used in this chapter that will help you gain a better understanding of AD FS.

# AD FS Commonly Used Terms and Components

The following are key components and terminology of AD FS:

**Account Partner** The account partner is the organization that issues the security tokens used by users to access resources in the resource partner's environment. The account partner's responsibility is to authenticate user accounts, create the user's claim, and package claims into tokens used by the resource partner for authentication in their applications and services. Account partners and resource partners work together in a federation relationship to provide SSO capability among themselves.

**AD FS Configuration Database** The AD FS configuration database is used to store all configuration data for the federation server. There is an AD FS configuration database for each individual federation farm. AD FS gives you the option to store the data on a Windows Internal Database (WID), or you can use Microsoft SQL Server. Please keep in mind that you can run either WID or SQL in a single AD FS instance; you cannot run both. We need to consider what database topology works best for your deployment, whereas WID is capped at a limit of five servers per federation farm. 

**Attribute Store** The attribute store is defined as a database or directory service that contains attributes about clients. You can use these attributes to issue claims about the clients. AD FS supports few different possibilities for an attribute store. For the most part, Active Directory and SQL are used primarily as the attribute store. Custom attribute stores can be built and used with additional configuration requirements like building a custom connection string.

**Claim** A claim is a statement that makes something about itself or another object. For example, the statement can be a name, email, group, privilege, or capability. Claims are issued and consumed between account partners and resource partners to provide single sign-on access for users to travel between organizations or services. These claims are used for logon authentication and authorization purposes in an application shared between the provider and the consumer. Claims identify a group of attributes for a user account such as the user's name or role. The account partner packages claims into security tokens and sends them tokens to the resource partner requesting user authentication into applications and services hosted by the resource partner.

**Federation Metadata** Federation metadata can be described as the data format that is used to communicate configuration data between the relying parties and the federation.

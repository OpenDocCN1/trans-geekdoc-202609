
# Role-Based Access Control and Active Directory Security

Access control can be managed based on the role an Active Directory object plays in an organization. Since objects represent users, computers, and other tangible elements of an organization, and these people and things serve different purposes in a company, it makes sense to configure these objects so that they reflect the tasks they perform. Role-based administration is used to configure object settings, so that computers and users have the necessary permissions needed to do their jobs based on the roles they fill.

The roles that users and computers are assigned correspond to the functions they serve in a company. Two categories of roles can be used for role based access control: authorization and computer configuration.

Authorization roles are based on the tasks a person performs as part of his or her job. For example, Help Desk personnel would need the ability to change passwords, while accountants would need to be able to access financial information and audit transactions. Using role-based access control, you can give each person the access he or she needs to perform these tasks.

Authorization roles are similar to security groups, to which users can become members and acquire a level of security that gives them the ability to perform certain tasks. However, authorization roles differ in that they are used for applications. Role-based access can be applied to a single application, set of applications, or a scope within the application. Another important difference is that role-based authorization can be dynamic, so that users become part of a group membership as an application runs. This is different from security groups that require membership to be set beforehand.

In the same way that users have different purposes in a company, so do computers. A business might have DCs, mail servers, file servers, Web servers, and any number of other machines providing services to users and applications in an organization. Computer configuration roles are used to control which features, services, and options should be installed and configured on a machine, based on the function it serves in the company.

## Authorization Manager

Authorization Manager is a snap-in for the MMC that allows you to configure role-based access for applications. By using roles, you ensure that users only have access to the functions and resources they need to perform their jobs, and are prohibited from using other features and resources they’re not authorized to use. For example, personnel in Payroll would need to view information on employees (so they can be paid), but wouldn’t need to access administrative features that allow them to modify passwords.

In Authorization Manager, roles are designed based on the tasks that are supported by the application. After the role is developed, users and groups can then be assigned to the role so they have the access necessary to perform these tasks. The tasks that are available for users to use depend on the application, as the ability to support roles and the functions available are part of the software design.

## Active Directory Authentication

When you log on to a Windows Server 2003 domain, a single logon gives access to any resources you’re permitted to use, regardless of their location on the network. A user doesn’t need to re-enter a password every time the user accesses a server or other resources, because any authentication after initially logging on is transparent. Because only one logon is needed, the system needs to verify a person is who he or she claims to be, before any access is given.

Authentication is used to verify a user’s logon credentials. The primary method of determining the identity of a user is by logging on to the local computer and network, where a person enters a username and password. If these don’t match the username and password for the local computer or Active Directory account, the person isn’t able to gain access.

Operating systems such as Windows NT, 2000, and Server 2003 store account information in the SAM database. The SAM stores credentials that are used to access the local machine. When a user logs on to a computer with a local user account that’s stored in the SAM, the user is authenticated to the local machine. The user’s access is limited to just that computer when logging on to the machine.

When users log on to the Windows Server 2003 domain, an account in Active Directory is used to access network resources located within the domain, or in other trusted domains. When a user logs on, the Local Security Authority (LSA) is used to log users on to the local computer. It is also used to authenticate to Active Directory. After validating the user’s identity in Active Directory, the LSA on the DC that authenticates the user creates an access token and associates a SID with the user.

The access token is made up of data that contains information about the user. It holds information about the user’s name, group affiliation, SID, and SIDs for the groups of which he or she is a member. The access token is created each time the user logs on. Because the access token is created at logon, any changes to the user’s group membership or other security settings won’t appear until after the user logs off and back on again. For example, if the user became a backup operator, he or she would have to log off and log back on before these changes affected the user’s access.

![test](images/note.jpg)Test Day Tip

Access control and authentication are vital parts of Active Directory’s security, so it is important that you understand the features and controls of Active Directory. The initial security feature that users will experience is the interactive logon. When users log on, an access token is created to indicate the user’s security capabilities. When changes are made to a user’s account, they will not apply to the user until that user logs on to the domain.

## Standards and Protocols

Authentication relies on standards and protocols that are used to confirm the identity of a user or object. Windows Server 2003 supports several types of network authentication:

![Squareb](images/Squareb.png) Kerberos

![Squareb](images/Squareb.png) X.509 certificates

![Squareb](images/Squareb.png) Lightweight Directory Access Protocol/Secure Sockets Layer (LDAP/SSL)

![Squareb](images/Squareb.png) Public Key Infrastructure (PKI)

As we’ll see in the paragraphs that follow, some of these standards and protocols not only provide a method of authenticating users, but also the ability to encrypt data. By encrypting data, you ensure that unauthorized users and applications won’t be able to view or modify the data. The data is encoded at one end, and decoded at the other. By providing encryption/decryption features, the privacy of information is better maintained.

### Kerberos

Kerberos version 5 is an industry standard security protocol that Windows Server 2003 uses as the default authentication service. It is used to handle authentication in Windows Server 2003 trust relationships, and is the primary security protocol for authentication within domains.

Kerberos uses mutual authentication to verify the identity of a user or computer, and the network service being accessed. Each side proves to the other that they are who they claim to be. Kerberos does this through the use of tickets.

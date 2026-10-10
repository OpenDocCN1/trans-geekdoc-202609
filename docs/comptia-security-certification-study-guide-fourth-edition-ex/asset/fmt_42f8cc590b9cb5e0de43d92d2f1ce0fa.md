
### Password vault
A password vault is an encrypted database used to store the many different passwords for the local systems and web sites a user may visit. The password manager software generates complex passwords and retrieves them for the different systems.

### TPM
The Trusted Platform Module (`TPM`) is a computer chip on a system that can be used to store encryption keys for a system that has encrypted drives. `TPM` can also be used with Secure Boot to ensure the integrity of the boot environment.

### HSM
A hardware security module (`HSM`) is a card that can be added to a system and is used to generate and store encryption keys. It can also perform encryption and decryption of data on the system as needed.

### Knowledge-based authentication
When the system or person validating your identity asks you for information that only you would know. For example, if you call your bank, they might ask you for information on the last purchase made on your account, or if you call the Canada Revenue Agency (`CRA`), they ask you for details on last year's tax return, such as "What is the value on line 150 of your tax return for last year?"

#### Single Sign-On
An important concept regarding authentication is single sign-on, also known as `SSO`. Single sign-on is the principle that when you authenticate to the network, you have the capability to access multiple systems based on your authentication information. With `SSO`, you are not required to authenticate with each different system you access—you authenticate once and then can gain access to multiple systems without authenticating again.

Why is `SSO` so valuable? Many years ago, you would have to authenticate with each server individually. This meant that each system stored a separate username and password database, and users had to remember various passwords to access more than one server. With `SSO`, the user logs on with one set of credentials and then accesses many different servers, even servers in other organizations. Authenticating against an identity store in your organization and being authorized to use network services from other organizations is known as *identity federation*.

![Image](exam.jpg)

**The Security+ exam expects you to know that single sign–on (`SSO`) allows a user to authenticate to the network once and access multiple systems without needing to provide additional credentials.**

`SSO` has the benefit that, as a network administrator, you do not need to manage multiple usernames and passwords for each server. However, at the same time, the drawback of `SSO` is that if a hacker hacks the account, they can gain access to multiple servers. If you are not in an `SSO` environment and the hacker hacks the account, they would have access only to the one server and would need to hack another password to access a different server.

![Image](exam.jpg)

**For the Security+ exam, know that there is a risk to `SSO` environments. If a hacker is able to compromise the authentication scheme, such as crack passwords, then they are able to gain access to multiple systems on the network.**

##### Access Tokens
When a user logs on to a system or network, an access token is created for the user that's used to determine whether they should be allowed to access a resource or to perform an operating system task. This logical token maintains all the information required for resource validation and includes the following information:

- **Security identifier (`SID`)** An `SID` is a unique number assigned to the user. The `SID` is what Windows uses to identify the user instead of the actual username. We know Bob as the `bsmith` user account, but Windows knows Bob as his `SID`, which looks something like `S-1-5-21-2752813485-788270693-1974236881-116`.
- **Group security identifier** The access token contains a list of any groups that the user is a member of. This is important because when a user double-clicks a resource, the resource is normally configured with permissions assigned to groups. Windows checks to see which groups the user is a member of through the access token and then checks to see if one of those groups has permission for the resource being accessed. If a group that is contained in the access token is allowed access to the resource, the user will gain access to the resource.
- **Primary group security identifier** For POSIX compliance, you can specify your primary group—this is, the group that becomes the owner of files and directories in POSIX environments. The primary group is, by default, set to Domain Users and is rarely used in the Microsoft environment.
- **Access rights** During the logon process, Windows determines the rights you have within the operating system and stores the list of your rights within the access token. For example, if you have the "Change the System Time" right, that information is stored in the access token during the logon process. If you try to change the time on the computer, your access token will be checked for that right; if the right is in the access token, you are allowed to change the system time.

It is important to note that the access token is created only at logon, so if you add a user to a new group, the user would need to log off and log on again for the access token to contain the new group in the group membership list. After logging on again, the user should be able to access any resources that the newly added group can access because the access token has been updated.

#### Cloud vs. On-Premises Requirements
When we look at authentication schemes for on-premises environments—that is, servers on your local LAN or WAN that you access day in and day out—most of these systems require you to authenticate to the network first. For regular networks you typically just log in with a username and password, but for highly secure networks you may use a form of multifactor authentication (`MFA`).

For cloud-based environments or any web site you use that requires authentication, you should look to implement `MFA`. Most cloud services allow the user to register a mobile device with their user account so that, when they log on, a code is sent to their phone that they then must input to prove they are who they claim to be. This ensures that someone cannot get into the web site or cloud service even if they figure out your username and password.

### CERTIFICATION OBJECTIVE 10.02

### Authentication Protocols
When users provide credentials such as a username and a password, they are passed to an authentication server via an authentication protocol. The authentication protocol determines how the authentication information is passed from the client to the server. In this section you will learn about different authentication protocols.

#### Windows Authentication Protocols
The first type of authentication protocols I want to go over are the Windows authentication protocols. These authentication protocols are found in Microsoft products such as Internet Information Services (`IIS`) and Exchange Server. Here's a description of a number of authentication methods used in the Microsoft world:

- **Anonymous authentication** You are not required to log on to the server. Windows uses an account for the actual service, and you are passed through as that account. Whatever permissions the anonymous account has are the permissions you will have while you are connected anonymously. This is a popular authentication method for web sites and FTP servers.
- **Basic authentication** You are required to log on, and the username and password are sent to the server in clear text. This means that if someone has a packet sniffer between you and the server, that person will be able to capture your password and view it because it is not encrypted.

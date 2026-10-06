In this case, the domain is the Windows Server 2012 R2 domain functional level, which is the highest domain functional level available at this time. Also, the dialog box doesn't provide the option of changing it. Functional levels can be changed up but not downward. In this case, it's as far as we can go with this domain.

Changing the domain functional level should be performed with caution and consideration. Since it is a one-way operation, you need to ensure all domain controllers within the domain can meet that functional level. Otherwise, a legacy domain controller can be left out of the loop. It will need the proper replication and end up with incompatible data within its database.

Here's what you get from each functional level:

**Windows Server 2003 Domain Functional Level** To get here, you need to have all your DCs in the domain running Windows Server 2003. There are several exotic exotic features here. These changes don't affect your job significantly. You may never see them working for you:

+   - Domain rename; see Chapter 25.

+   - User and computer containers can be redirected.

+   - Constrained delegation.

+   - Selective authorization. This is related to trusts.

+   - Logon timestamp update.

**Windows Server 2008 Domain Functional Level** Again, you need to have all your domain controllers on this version. However, there is a caveat in the Windows Server 2008 R2 help. Specifically, if you plan to add earlier versions as Windows Server 2008 or 2003 domain controllers, you could set the domain functional level to this value. Here are some features of this level:

+   - DFS replication support. In Chapter 14, "Creating and Managing Shared Folders," you read about the improved DDFS replication. These improvements can be applied to the folder as well.

+   - Advanced Encryption Services (AES 128 and 256).

+   - Track last login information for users on workstations.

+   - Password policies.

**Windows Server 2012 R2 Domain Functional Level** Yes, this version has its own domain functional level. Its sole feature is authentication mechanism. This secures the token for users to pass to members for access to resources. Basically, notifies you that the user was authenticated with a certificate instead of username/password credentials. Applications and resources can then be configured to grant permission based on this information.

**Windows Server 2012 and Windows Server 2012 R2 Domain Functional Level** The Windows Server 2012 R2 domain functional level includes all of the great features provided by the previous domain functional levels. In addition, it comes with a few extras that are worth mentioning. Now with Dynamic Access Control (DC AC) in Windows Server 2012, Kerberos 5 authentication has changed a bit. Using the new Kerberos Key Distribution Center (KDC) support for claims, compound authentication, and the Kerberos armoring, KDC
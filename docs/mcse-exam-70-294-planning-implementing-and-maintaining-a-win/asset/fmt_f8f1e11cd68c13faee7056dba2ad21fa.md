
# Domain Group Scopes and Functional Levels

Domain local groups are used when assigning permissions or user rights. Microsoft wants you to use `DLG`s when modifying the `ACL` of an object such as a file, or assigning a user right. Other groups are added to a `DLG` to have their members receive the group’s assigned permissions or rights. In a Windows 2000 mixed functional level domain, domain local groups can consist of users, computers, and global groups from the domain the `DLG` exists in, and any trusted domain. When the functional level of the domain is raised to Windows 2000 native or Windows Server 2003, a `DLG` can also contain other domain local groups from its local domain, as well as universal groups.

Microsoft specifies global groups as the primary container for user and computer objects. They call for grouping users according to role, function, responsibility, or department into global groups. In a Windows 2000 mixed functional level domain, a global group can contain users and computers from the same domain in which it exists. When the functional level of the domain is raised to Windows 2000 native or Windows Server 2003, a `GG` can also contain other global groups from its local domain.

Unlike global and domain local groups, universal groups (`UGs`) are stored in the Global Catalog (`GC`). Adding or removing objects from a universal group triggers forest-wide replication. To minimize this, Microsoft recommends that other groups, and not individual user and computer accounts, be the primary members of a universal group. Universal security groups do not exist in a Windows 2000 mixed functional level domain. When the functional level of the domain is raised to Windows 2000 native or Windows Server 2003, universal security groups can contain domain users, computer accounts, and global groups from any trusted domain, as well as other universal groups.

An administrator can change an existing group’s scope. Universal groups can be converted to global or domain local groups, and global and domain local groups can be converted to universal groups. However, global groups cannot be converted directly to domain local groups (and vice versa). You cannot convert from one group type to another if the current membership of the group that is being converted is not compatible with the membership allowed for the target scope.

Microsoft has a number of acronyms that describe how groups should be used in different scenarios, including:

■ `AGDLP` Accounts (user and computer objects) are placed into Global groups, which are placed into Domain Local groups, which are added to access control lists (`ACL`s) and granted Permissions to a resource. This model is used in a single or multiple domain environment, when the Windows 2000 mixed domain functional level is in use.

■ `AGGDLP` Accounts are placed into Global groups that can be placed into other Global groups and/or Domain Local groups, which are added to `ACL`s and granted Permissions to resources. This model can only be used in domains that have a Windows 2000 native or Windows Server 2003 functional level.

■ `AGGUDLP` (or `AGUDLP`) Accounts should be placed into Global groups that can be placed into other Global groups and/or Universal groups, and then into Domain Local groups, which are added to `ACL`s and granted Permissions to resources. This model can only be used in domains that have a Windows 2000 native or Windows Server 2003 functional level. In addition, it is primarily used in a multiple domain environment.

## Exam Objectives Fast Track

### Creating a Password Policy for Domain Users

☑ According to Microsoft, complex passwords consist of at least seven characters, including three of the following four character types: uppercase letters, lowercase letters, numeric digits, and non-alphanumeric characters such as & $ \* and !.
☑ Password policies and account lockout policies are set at the domain level in Group Policy.
☑ If a subset of your user base requires a different set of account policies and other security settings, you should create a separate domain to meet their requirements.
☑ Be sure that you understand the implications of an account lockout policy before you enable one in a production environment.

### Creating User Authentication Strategies

☑ Within a domain, `Kerberos v5` is the default communication method between two machines that are running Windows 2000 or later.
☑ Pre-Windows 2000 computers use `NTLM` (or `NTLMv2`) authentication in an Active Directory domain.
☑ To provide authentication for Web applications, you can implement either `SSL/TLS` or Microsoft Digest.

### Planning a Smart Card Authentication Strategy

☑ Microsoft Windows Server 2003 relies on its public key infrastructure (`PKI`) and Certificate Services to facilitate smart card authentication.
☑ Smart card certificates are based on the following three certificate templates: Enrollment Agent, Smartcard Logon, and Smartcard User.
☑ Several Group Policy settings are specific to smart card implementations; most other account policy settings will also affect smart card users.

### Planning a Security Group Strategy

☑ There are two types of groups in a Windows Server 2003 domain: distribution and security.
☑ Only security groups can be used to assign permissions.
☑ There are three group scopes in a Windows Server 2003 domain: domain local, global, and universal.
☑ Additional group nesting and universal security groups are only available at the Windows 2000 native and Windows Server 2003 domain functional levels.
☑ Existing groups can have their scopes changed in Windows 2000 native and Windows Server 2003 functional level domains.

## Exam Objectives Frequently Asked Questions

The following Frequently Asked Questions, answered by the authors of this book, are designed to both measure your understanding of the Exam Objectives presented in this chapter, and to assist you with real-life implementation of these concepts. You will also gain access to thousands of other FAQs at [ITFAQnet.com](http://www.ITFAQnet.com),

Q: How can I configure a smart card user to be able to temporarily log on to the network if the user has forgotten his or her card?

A: In the Properties of the user’s account within `Active Directory Users and Computers`, make the following changes on the `Account tab`:
1. Clear the check mark next to `Smart card is required for interactive logon`.
2. Place a check mark next to `User must change password at next logon`.
Finally, right-click the user object and select `Reset Password`. Inform the user of the new password, and that it will need to be changed at next logon.

Q: What are the advantages of implementing a “soft lockout” policy versus a “hard lockout”?

A: A hard lockout policy refers to an account that must be manually unlocked by an administrator. This setting provides the highest level of security but carries with it the risk that legitimate users will be unable to access network resources. In some circumstances, it can be used to effectively create a DoS attack against your own network. Hard lockouts place a greater burden on account administrators, because at least one must always be available for users to contact when they need their accounts unlocked. A soft lockout expires after a set amount of time and helps limit the effectiveness of password attacks against your network, while reducing the burden placed on administrators in a hard lockout environment.

Q: My organization is in the planning stages of a smart card rollout. What are the security considerations involved in setting up a smart card enrollment station?

A: Since a smart card enrollment station allows you to create certificates on behalf of any user within your Windows Server 2003 domain, you should secure these machines heavily in terms of both physical location and software patches. Imagine the damage that could be done if a malicious user were able to create a smart card logon certificate for a member of the `Domain Admins` group and use it to log on to your network at will.

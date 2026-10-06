
# AN INTRODUCTION AND ACTIVE DIRECTORY BASICS

This will ensure that the user changes the password and no one knows it, even your. Your display will look similar to Figure 7.20.

# FIGURE 7.20
Creating a user in ADAC

![](img/41a83208e6906a3732620203b836cea7_328_0.png)

# USER LOGON NAME

Companies typically have an established standard of how logon names are created. Some methods are first initial and last name, first name and last name, first name dot last name, and many. If you're starting at a new company, you should learn what the standard is and ensure that you follow this standard when creating accounts.

The account is shared by multiple users (such as a temporary job filled by different workers), you may want to select "User cannot change password." If you are creating service accounts (user accounts to start services), you may select "Password never expires" to ensure an expired password doesn't lock out the account. Finally, if the account isn't going to be used for a while, consider disabling it.

- 5. Click Next.
- 6. Review the information on the page, and click OK.

# CREATING USERS WITH POWSHELL

Before PowerShell was born, we used a tool called DSAdd to create users and other Active Directory objects. It was a great tool back then, but today it's considered a legacy tool that still and grows. It might be a step into batch scripting and offers a first touch into the automated command-line world. The only way to get serious about automating and making life easier is to use PowerShell.

Just as you used PowerShell to create OUs, you can create user accounts. You will be surprised to learn that the basic cmdlet doesn't differ from the DSAD command. The cmdlet you need is the following:

```powershell
New-ADUser -Path "OU=Sales,DC=bigfirm,DC=com" -AccountPassword (ConvertTo-SecureString $Password -AsPlainText) -Name "Maria Smith" -GivenName Surname -DisplayName "Maria Smith" -SamAccountName "Maria Smith" -UserPrincipalName "Maria.Smith@bigfirm.com" -ChangePasswordAtLogon 1 -Enabled 1
```

This PowerShell example shows how to create a user Maria Smith with the exact parameters. You might think, that the PowerShell command has more code than the DSAD command in the previous example. Now you are probably thinking the same thing. The advantage is if you have to type or make some thing. The strength of PowerShell lies in its object-oriented approach with all its bells and whistles.

Notice in the example that we could not just specify a password in string format; we needed to convert this to a secure string before submitting it to the -AccountPassword parameter. The -ChangePasswordAtLogon requires an input value of type Boolean. Boolean means either (false) or (true). Review the rest of the command and you will see that it is self-explanatory.

# CREATING GROUPS

You may also create some groups. The most common reason to create groups is to organize users and then assign permissions to groups. Whenever possible, you could assign permissions to groups rather than users. You may have heard before the saying "Users come and go, but groups stay forever." Well, you've maybe heard it before we made it up, but it makes sense, and it is a good way to remember that you always assign permissions to groups instead of users.

As an example, you could have several users in the sales department. Instead of assigning permissions to each individual in the sales department, you could create a global security group G_Sales. Place all the users in the sales department into this group and assigning to the G_Sales group. If a user leaves, take him out of the G_Sales group and he will no longer have the permissions of group. If a user joins the sales team, put her into the G_Sales group, and she will have the same permissions as everyone else in the group.

That sounds pretty easy, but there is more than one type of group; there are several types of each of them its own purpose. The two types of groups are distribution and security. Distribution groups are used for email, and security groups are used to assign permissions. Security groups can also be used for email.

There are three group scopes:

- Global groups are used to organize users. This is the most commonly used group and the one you will create in this chapter. Users will be placed in the global groups, and permissions can be assigned to the global groups.
- Domain Local: in some implementations, domain local groups are used in a DL group strategy where A indicates accounts, G indicates global groups, DL indicates domain local groups, and P indicates permissions. User accounts are placed in global groups. Global groups are placed into domain local, and permissions are assigned to the domain local groups. When used this way, the domain local groups are an added layer to identify resources. The recommended approach is to design your group strategy using the AGDLP principle.
- Universal Universal groups are used only in multiple-domain environments. For example, in a network with two domains, Europe and UnitedStates, and global group G_Sales in each domain, you can create a universal group UG_Sales that has as members the two G_Sales groups, UnitedStates\G_Sales and Europe\Sales. This group can then be used anywhere in the enterprise. Any changes in the membership of the individual G_Sales groups will not cause replication of the G_Sales group. You can now add the universal group into a domain local group and give resource permission to the team all over the world. This strategy is referred to as AGUDLP, where U stands for universal group.

The most common way to create these groups is with Active Directory Users and Computers or with Active Directory Administrative Center. You can use the following steps to create a global security:

- 1. Launch Active Directory Administrative Center by pressing WIN+R to start the dialog, type dsac.exe into the text box, and click OK.
- 2. Right-click the Sales OU, and select New ➢ Group.
- 3. Enter G_Sales in the "Group name" box. Your display will look similar to Figure 7.21. Click OK.

![](img/41a83208e6906a3732620203b836cea7_330_0.png)

- 4. Right-click the Sales OU, and select New ➢ Group. Then enter G_SalesAdmins in the "Group name" box. Click OK.

Your G_Sales group is created, and you can now use this group to assign permissions.

# AN INTRODUCTION AND ACTIVE DIRECTORY BASICS (Repeated Header)

# CREATING USERS WITH POWSHELL (Repeated Header)

# CREATING GROUPS (Repeated Header)

# AN INTRODUCTION AND ACTIVE DIRECTORY BASICS (Repeated Header)

# CREATING GROUPS WITH POWSHELL (Repeated Header)

# CREATING GROUPS WITH POWSHELL (New Header)

# POWSHELL HISTORY VIEWER (New Header)

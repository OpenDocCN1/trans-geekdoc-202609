
# CHAPTER 8 CREATING AND MANAGING USER ACCOUNTS

FIGURE 8.23
Active Directory user Telephones tab

![](img/41a83208e6906a3732620203b836cea7_437_0.png)

# ORGANIZATION TAB

The Organization tab is another one of the information tabs (see Figure 8.24). We've mentioned several times that applications can use this sort of information. For example, the settings could be loaded by a WindowsSharePoint Services (WSS) implementation. This information is presented in a web interface when users look to find more about an owner of some documentation or a site within the WSS implementation. WSS loads this information from the user's Active Directory user account object. For example, if you viewed Steve Red on a WSS server, then the properties of SRed would be read by WSS from Active Directory.

This tab allows you to describe the role of the user within the organization—it's more of a human resources thing and doesn't have anything to do with Active Directory delegation or administration. You can also select their line manager by browsing to another domain-based user account in Active Directory.

# FIGURE 8.24

Active Directory user Organization tab

![](img/41a83208e6906a3732620203b836cea7_438_0.png)

# COM+ TAB

You're delving into application programming country with the COM+ tab in Figure 8.25. A partition is an application configuration. An application can have many configurations. This means you can have many of COM+ partitions within Active Directory. You can read more about application partitions on MSDN.

# FIGURE 8.25

Active Directory COM+ tab

![](img/41a83208e6906a3732620203b836cea7_438_1.png)

A partition set can contain many partitions. You can link users to partition sets and in to the contained partitions. Not only can you link a single user, but you can link all users in an OU by linking the OU to a partition set. You can read more about creating partition sets within Active Directory on MSDN at http://tinyurl.com/2naoft

# Attribute Editor Tab

You've seen this tab before you looked at the properties of an OU (see Figure 8.26). You can view or directly edit the properties of a user object here if you want.

![](img/41a83208e6906a3732620203b836cea7_439_0.png)

# PUBLISHED CERTIFICATES TAB

Certificates give you an encryption-based security mechanism that is used to provide identity (see Figure 8.27).
Here you can view certificates that have been automatically assigned to the user through Active Directory using Certificate Services. You can actually manually assign certificates to your own local certificate stores or from certificates that are stored on the file system.

# FIGURE 8.27
Active Directory
user Published
Certificates tab

![](img/41a83208e6906a3732620203b836cea7_440_0.png)

# MEMBER OF TAB

The Member Of tab allows you to control group membership of this user account (see Figure 8.28).
I'll return to this later when we cover groups and group membership in this chapter.

# FIGURE 8.28
Active Directory
user group
memberships

![](img/41a83208e6906a3732620203b836cea7_440_1.png)

You can see that you can also control the primary group of the user. This is required only in POSIX applications or Macintosh client computers. When one of these clients creates a file or folder on a Windows server, this primary group is assigned to the new object. The group must be in the user's domain, or it must be a global or universal security group.

# PASSWORD REPLICATION TAB

The Password Replication tab is used to view which read-only domain controllers (RODCs) this user's password has been replicated to (see Figure 8.29). An RODC is an Active Directory architecture option that was added with Windows Server 2008. You can place an RODC in branch offices where the physical security of a normal domain controller cannot be guaranteed. In the event of the threat or compromise of an RODC, you can isolate accounts that have their details stored on that RODC.

FIGURE 8.29nActive Directory user Password Replication tab

![](img/41a83208e6906a3732620203b836cea7_441_0.png)

# OBJECT TAB

You'll find the Object tab, shown in Figure 8.30, to be quite useful when doing some troubleshooting. You can view some useful information as the following:

# CREATING AND MANAGING USER ACCOUNTS

- When the object was created
- When it was last modified
- USN information that is used to control Active Directory replication

FIGURE 8.30
Active Directory user object properties

![](img/41a83208e6906a3732620203b836cea7_442_0.png)

A nice new option on this tab is the ability to protect the user account against accidental deletion using the check box at the bottom. This would be pretty useful to ensure that no one unintentionally deletes the user account for a critical service account, such as the CEO or a senior government official.

# SECURITY TAB

The tab, as shown in Figure 8.31 allows you to control what can do to this user account object. This is known as *delegation*. We'll discuss this in great depth later in this book.
Take a look at the permissions assigned to SELF by clicking it. SELF is the user in question. That is, what can Steve Red do to the SRed account? If you scroll down to the “Permissions for SELF” control, you will see that Steve can actually change a lot of settings in his own user account. This means that Steve can alter settings such as who his manager is, how his contact details are, and so on. In theory, you could present users with some web-like application that allows them to easily edit these settings. This approach would be much easier for them to understand than asking them to fire up Active Directory User and Computers and edit their accounts there!

# CHAPTER 8 CREATING AND MANAGING USER ACCOUNTS

FIGURE 8.31
Active Directory user security

![](img/41a83208e6906a3732620203b836cea7_443_0.png)

# EDITING MANY USER ACCOUNTS AT ONCE

It's pretty easy to change all of those settings for an individual account, as you've seen. If you want to modify more than one account at once? That's easy too. For this, create a new set of users in the OUs, as shown in Figure 8.32.

FIGURE 8.32
Additional Active
Directory users

![](img/41a83208e6906a3732620203b836cea7_443_1.png)

# CREATING AND MANAGING USER ACCOUNTS

Say you want to modify settings for all the users in this OU. Select all the user accounts, right-click, and select Properties.
This opens up a proper' dialog box, shown in Figure 8.33. It actually doesn't make sense to offer all the settings for more than one user, so you see only a subset of the options.

FIGURE 8.33
Properties of multiple Active Directory objects

![](img/41a83208e6906a3732620203b836cea7_444_0.png)

To modify a setting, select the check box associated with it. This makes the edit box available to you. You can now edit the setting for all the users you previously selected, as shown in Figure 8.34.

FIGURE 8.34
Changing attributes of multiple Active Directory objects

![](img/41a83208e6906a3732620203b836cea7_444_1.png)

# CHAPTER 8 CREATING AND MANAGING USER ACCOUNTS

Managing domain-based user account objects is pretty when using Active Directory Users and Computers.

# MANAGING DOMAIN-BASED USER PROPERTIES AT THE COMMAND LINE

Let's look at how you can do it when the command prompt is your only option. You'll be using a command called dsmod. You can view the help for this by running the following:

```
dsmod user /?
```

Notice that you have to use the DN of the user you want to modify. Check out the previous tip to get the DistinguishedName of the user ("Obtaining the Easy Way"). That's all well and good if you have a GUI available. What if you don't? If you know the UPN of the user, then you can run dsquery to get the DN:

```
dsquery user -upn bigfirm.com
"CN=Steve Red,OU=Users,OU=Bigfirm,DC=bigfirm,DC=com"
```

Alternatively, you can run the dsquery using the SAM account name, which is the friendly name that you know as SRed:

```
C:\Administrator\dsquery user -samid SRed
"CN=Steve Red,OU=Users,OU=Bigfirm,DC=bigfirm,DC=com"
```

dsquery is a fairly powerful command, it's well worth knowing it with /?
Now you can proceed with dsmod. Let's see how you can configure a home drive and a drive to map it for: Steve Red:

```
dsmod user "CN=Steve Red,OU=Users,OU=Bigfirm,DC=bigfirm,DC=com" -hmir \DC01\nhome$\SRed -hendrv P
```

This will configure a home drive (a network-based shared folder specific to this user) with the drive letter whenever Steve Red logs in.

You now want to configure the manager for Steve Red. You've just learned that Marcel Zehner has been promoted to the department head. You can do this by running the following:

```
dsmod user "CN=Steve Red,OU=Users,OU=Bigfirm,DC=bigfirm,DC=com" -mgr "CN=Marcel Zehner,OU=Users,OU=Bigfirm,DC=bigfirm,DC=com"
```

Notice that you didn't enter something like bigfirm or mezhner as the manager. You actually used the DN for the account that is the manager.

At first, dsmod looks like a difficult command to Play with it for a few minutes, and you'll see that it's not actually that bad.

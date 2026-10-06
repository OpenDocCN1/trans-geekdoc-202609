
# WINDOWS SERVER 2012 (R2) COMPATIBILITY

We would like to point out if we are writing about Windows Server 2012 we are also meaning Windows Server 2012 R2 and all features apply to both versions.

# Creating and Managing User Accounts

In this section, we'll cover how to create, manage, and delete local user accounts and domain-based user accounts. You'll learn how to do this with the GUI-based, command line-based, and PowerShell-based administrative tools, although you have to realize that the command-line tools are becoming extinct. Microsoft is going to push PowerShell in a big way.

The working environment for this chapter contains a domain controller DC01.bigfirm and a member server Server01.bigfirm.com. This will allow us to demonstrate how to create and manage local and domain user accounts.

# Creating Local User Accounts

We'll cover how to create local user accounts first. There is one major tool to manage local user accounts, Computer Management. You can find it in Server Manager by choosing Tools Computer Management. This tool will give you the same options when managing users and groups as in Windows 2008 R2.

To follow along with this example, log into Server01.bigfirm.com as Administrator, Computer Management, and navigate into \Local Users and Groups\Users (see Figure 8.1). You can see two user accounts:

![](img/41a83208e6906a3732620203b836cea7_413_0.png)

Administrator is the default administrative user account. We will talk a little more about this account in a few moments.

Guest The purpose of this account is to allow people who do not have an actual user account to log into the computer. This might be something an administrator might want if they have lots of guest users coming and going.

You'll notice that the Guest account has a little down arrow on its icon. This is because best practices dictate that account should be disabled. Microsoft has done this by default for you. Having a Guest account is not a common requirement on a server, you might never need to enable it.

# Real World Scenario

# THE ADMINISTRATOR ACCOUNT

It is critical that you protect the Administrator account in a manner that is suitable for your organization. The local Administrator account has complete control over your server, and the domain Administrator account has complete control over your network! So, it makes sense to have a very strong password for this account.

Administrator is an anonymous account in larger organizations. Take a look in Event Viewer and ask, "How do I know who was using the Administrator account?" It is because of that you should create a user account with administrative or delegated rights for administrators who need them. Using the default Administrator account is often banned unless it is an emergency. If every member of IT is to be audited by the Security log, you will need to create accounts for each administrator. To ensure that each administrator has only the rights and permissions to do their job.

Some organizations choose to disable the Administrator account altogether. That's one solution that you might not be big enough on account in the case of password lockouts. Administrator is the one who cannot be locked out. Those organizations would use an alternative approach. You can think of it as the "nuclear" option. You've seen many movies where two generals have to turn two different keys in start a nuclear missile launch. You can do the same with the Administrator account. It can be set by two individuals who do the same thing with the first half of the password and the other typing the second half. Organizations in this sort of option often have an IT security or internal audit department that is the holder of one of the password while the server administration team retains the other.

One final option is to rename the Administrator account. There's some debate about this account because the security identifier (SID), a code that Windows uses internally to uniquely identify an object) of the account can be predicted before you have access to the server or the domain. Some argue that renaming the account is pointless. However, most Internet-based attacks are actually robotic and unintelligent. They target typical names such as SA, root, or Administrator and brute-force attacks to guess the password. It is still worthwhile to rename the Administrator account to defend against these forms of attack.

In the end, same old security rules apply. Set a very strong password on your Administrator accounts, restrict knowledge of the passwords, restrict remote access where you can, and control physical access to your servers.

In this example, we'll show how to create a user account for a member of staff named Steve Red. Steve does then and get select New User. In \Local Users\Users, right-click in the middle panel and then select New User. The New User dialog box opens.

Now fill in some details about the user with the following fields (see Figure 8.2):

# CHAPTER 8 CREATING AND MANAGING USER ACCOUNTS

FIGURE 8.2
Creating a new user

![](img/41a83208e6906a3732620203b836cea7_415_0.png)

**User Name** This is the name that the user will enter when they log in. We strongly recommend implementing some of naming standard. A smaller organization might get with SRed for Steve. You might want to add a numeric scheme, such as SRed1Red, SRed01, or SRed10Red. Some organizations take things further. Some use the company employee ID as a username. Others use the person's initials (including the middle name) with a number, such as SRed10. More anonymous systems might be appropriate where personal data is deemed sensitive.

**Full Name** The "full name" is just the name of the person who will use the account. You probably don't want to store those names on servers that will be facing the Internet.

**Password** Next, you need to set the password. One of the best ways to set a password is to use a *phrase*. Read the case study to learn more about passphrases.

**User Change Password at Next Login** We've left the "User must change password at next login" enabled for this example. That does exactly what it says on the tin. You can set an easy-to-communicate password such as "your passphrase" and leave this box selected (it's by default). The new user will be able to log on but *must change* their password to complete the process. This guarantees that no IT will know the user's password. You'll notice that the next two boxes are grayed out and unavailable. To change this, you should clear the "User must change password at next login" check box. Logically, this makes sense.

**User Cannot Change Password** You can prevent the user from being able to change their password. A scenario where this might use is when you are creating a user account that.

**Password Expires** "Password never expires" overrides any expiration policies. (Note: corrected based on context "Password never expires")

**Account Is Disabled** "Account is disabled" is pretty-explanatory.

In this example, we'll show how to create a user account for a member of staff named Steve Red. Steve does then and get select New User. In \Local Users\Users, right-click in the middle panel and then select New User. The New User dialog box opens.

Now fill in some details about the user with the following fields (see Figure 8.2):

(Note: The OCR text provided in the prompt contained fragmented sentences and repetitions in the latter half, but I have reconstructed the logical flow of the field descriptions.)

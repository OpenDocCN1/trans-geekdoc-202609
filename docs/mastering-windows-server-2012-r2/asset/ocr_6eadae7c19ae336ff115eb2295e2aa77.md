# CHAPTER 8 CREATING AND MANAGING USER ACCOUNTS

FIGURE 8.6
Creating a new Active Directory user

![](bbox=[0.31, 0.1, 0.66, 0.35])

This is probably a good time to use some terminology for people new to Active Directory and user account management. Every user has two types of names with which they can access resources on the network:

**User Logon Name** is the name that you are probably most familiar with, such as SRed.

**User Principal Name** is a username that looks like an email address. You can see in Figure 8.6 that the UPN for Steve Red is SRed@bigfirm.com. The UPN suffix @bigfirm.com is inherited from the name of the domain by default. Note that you can add UPN suffixes to your Active Directory forest by following the instructions at http://tinyurl.com/3y4zw.

The user logon, which was retained by Microsoft for backward compatibility, is visible as SRed. You can also see that the pre-Windows 2000 username is Bigfirm\SRed. Fortunately enough, this pre-Windows 2000 username is exactly what users will be prompted to enter when they log into the domain:

+   7. Click Next to go to the New Object - User page, shown in Figure 8.7.

FIGURE 8.7
Setting the new AD user password

![](bbox=[0.31, 0.69, 0.66, 0.94])
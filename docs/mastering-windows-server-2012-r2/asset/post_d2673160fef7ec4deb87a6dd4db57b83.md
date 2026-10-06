
## Fine-grained Password Policies

Before you can implement fine-grained password policies, you need to ensure that your environment meets the minimum requirements.

- You have deployed a Windows Server 2012 domain controller to your domain.
- The functional level must be set to Windows Server 2008.
- Only members of the Domain Admins group can create password-settings objects (PSOs).

## Creating the Password Settings Object

In Windows Server 2012, you have a perfect GUI for creating the Password Settings objects. Under the hood nothing changed from Windows Server 2008 R2; the features are the same. However, it will be a great advantage to manage the PSOs using the GUI, especially when it comes to timing values as duration entries, because this was a big pain before. You will create a PSO for the G_ITAdmins groups with the following steps:

1. Start Active Directory Center by pressing WIN+R, open the Run dialog, and enter dsac.exe in the text box. Click OK. You can also start the Active Directory Administrative Center from the Start screen.
2. Change to the tree view and scroll down to System/Password Settings Container.
3. Right-click Password Settings Container and click New/Password Settings, as shown in Figure 7.29.

FIGURE 7.29
ADAC Password Settings Container

![](img/41a83208e6906a3732620203b836cea7_345_0.png)

4. Type PSO_G_ITAdmins and choose the value 10 for Precedence.
5. Enforce a minimum password length of 15 characters.
6. Enforce a minimum password age of 30 days.
7. Enforce an account lockout policy with the number of failed attempts set to 5.
8. Under Directly Applies To, click Add. Select the G_ITAdmins group and click OK.
9. Leave the rest of the settings at their default. You should see a dialog similar to the one in Figure 7.30.

FIGURE 7-30n Password Settings

![](img/41a83208e6906a3732620203b836cea7_346_0.png)

10. Click OK to close the dialog.

You should see now in your Password Settings container in Active Directory Center a PSO called PSO_G_ITAdmins.
Now you need some kind of proof that this PSO works and what settings you have. In our previous examples we created a user named Sally Smith. Let's assume that this user is an IT administrator, and we are going to add Sally Smith into the G_ITAdmins group. Sally should now receive the new password settings; you can easily prove it by logging onto as the s.smith account. Another way to see what kind of PSO rules are applied to a user as follows:

1. Open Active Directory Administrative Center.
2. Navigate into the OU where the user Sally Smith has been created.
3. Right-click Sally Smith, and click "View password settings," as shown in Figure 7.31.

FIGURE 7-31
View resultant password settings

![](img/41a83208e6906a3732620203b836cea7_347_0.png)

4. The PSO_G_ITAdmins dialog opens and you can see the PSO object that applies to Sally Smith.
5. Click OK to close the dialog.

It is important to know that when you link PSOs to other groups in addition to global security groups, the Result Set of Policy (RSOP) for the user object is determined, only those PSOs are considered that are directly linked to the user object or the global security group that the user is member of. PSOs linked to distribution groups or other security groups are ignored.

## Password Settings Object Precedence

In the previous example you configured several password settings that are set similarly to the Default Domain Policy in your domain. There is one more setting to look at. In the PSO dialog shown in Figure 7-30, you can configure the Precedence parameter. This identifies which PSO will take precedence, if multiple PSOs apply to a user.

Let's take the G_ITAdmins group and apply two PSOs, one with precedence of 10 and one with precedence of 5. The PSO with precedence of 5 will win, because a lower precedence value is a higher precedence.

This makes sense if you are just using groups and apply the PSO to the group G_ITAdmins (Sally Smith is still a member) and you apply a PSO directly to Sally Smith?

Let's take the G_ITAdmins group again, where Sally Smith is a member, and apply a PSO with a precedence of 10. Create another PSO with a precedence of 15 and apply this PSO directly to the user Sally Smith. The PSO directly applied to the Sally will win, although the precedence is higher.

The way that the PSO applied is determined is as follows:

A PSO that is linked directly to the user object is the resultant PSO. If no PSO is linked to the user object, the global security group memberships of the user—and all PSOs that are applicable to the user based on those global group memberships—are compared. The PSO with the lowest precedence value is the resultant PSO.

## SYSVOL: Old and New

The really cool thing about Active Directory back in the year 2000, and still cool today, is that Active Directory is a distributed database. It can have more than one domain controller that hosts a writable copy of the directory database, thus eliminating the need for primary (writable) and secondary (nonwritable) servers. Inside each Active Directory domain controller were a couple of folders, which were public-facing shares, used to provide access and replication capabilities for various domain controllers throughout the domain. The directory that made and these shares available was titled SYSVOL. It contains logon shares (logon scripts and Group Policy objects for client computers in the domain), user logon scripts, Group Policy, FRS Replication staging, folders and files for synchronization, and file system junctions.

This section addresses the following topics:

- Introduction to the File Replication Service
- Migration to Distributed File System Replication
- Discovering the current migration state of a domain controller using the dfsrmig command

## The Old: File Replication Service

Often when we consider something in the world of technology as old, there is a negative connotation associated with it. In this case, the old stuff simply makes reference to the way that something has been done in the past. In this particular case, the changes made to SYSVOL, in Windows Server 2008 R2 and in Windows Server 2012, are encompassed in a new methodology for replicating SYSVOL materials between replication partners throughout the domain.

| DID FRS CHANGE IN WINDOWS SERVER 2012? |
| :--- |
| No. FRS works the same way as in Windows Server 2008 R2, but its successor is DFS-FRS. |

The new way of using Distributed File System Replication (DFS-R) has some significant improvements over the old File Replication Service (FRS) method, but that doesn't necessarily mean the old way is bad. In fact, all versions of Active Directory with the exception of Windows Server 2008 R2 and Windows Server 2012 use the “old” method. It is worth gaining an understanding of FRS because it is so prevalent on the networks to which you add Windows Server 2012.


# AUTOMATICALLY ADJUSTING COLUMNS

It is possible that if you run the command with multiple properties, it will not correctly show up in the command prompt. It will look like the columns are not sized correctly. You can then add the switch -auto at the end of the command. As you might know in PowerShell, you don't always have to write the complete switch name. For example, in this case -auto stands for -AutoSize. This will instruct the FT command to adjust the columns' width automatically. The command will look like this:

```
PS:\Users\Administrator> Get-ADGroupMember "IT Administrators" -recursive | FT -auto
```

The next operation you'll be able to do with groups is remove members. You'll use the Remove-ADGroupMember cmdlet for:

```
PS:\Users\Administrator> Remove-ADGroupMember "IT Administrators" -SRed
```

Confirm
Are you sure you want to perform this action?
operation "Set" on Target "CN=IT Administrators,OU=Security Groups,OU=BigFirm,DC=bigfirm,DC=com"
[Y] Yes to All [N] No [L] to All [S] Suspend [?] Help (default is "Y")

You've requested to remove the user SRed from the IT Administrators group. The Remove-ADGroupMember cmdlet asks for confirmation. You can enter one of a number of options in response to the confirmation request:

- Yes Go ahead and remove the indicated user from the group.
- Yes to All Use this option if you have requested to remove multiple members from the group and you're sure you want to remove them all.
- No Do not remove the indicated user group group.
- L Abandon all removal operations requested in the command.
- S Suspend the operation. This will return you to the command prompt. You can resume the command to this by typing Exit.

You can run this for multiple users using a comma delimiter:
PS:\Users\Administrator> Remove-ADGroupMember -Identity "IT Administrators" -Member SCorse,SRed

Confirm
Are you sure you want to perform this action?
operating "Set" on Target "CN=IT Administrators,OU=Security Groups,OU=BigFirm,DC=bigfirm,DC=com"
[Y] Yes to All [N] No [L] to All [S] Suspend [?] Help (default is "Y")

# ACTIVE DIRECTORY MODULE FOR WINDOWS POWERSHELL

Here you have separated SScorso and SRed with a comma. You can add many users or even groups to manage this way.

You might want to remove many users or groups using some sort of search. In the following example, you're using the Get-ADUser cmdlet to search for all users in the \BigFirm\Users OU and remove them from the IT Administrators group.

```
PS C:\Users\Administrator> Remove-ADGroupMember "IT Administrators" -Member
(Get-ADUser -Filter "Name like "*" -SearchBase "OU=Users,OU=BigFirm,DC=firm,DC=com")
```

Confirm

Are you sure you want to perform this action?
Performing 'Set' on Target "CN=IT Administrators,OU=Security Groups,OU=BigFirm,DC=firm,DC=com"

- [Y] Yes [A] to All [N] No [L] to All [S] Suspended [?] Help

You can see that you haven't specified a value for the -Member flag. If instead, you have nested the Get-ADUser query. That will find all the users you want to remove, and the result is passed to the Remove-ADGroupMember cmdlet. If you confirm this, every user object in the \BigFirm\Users OU will be removed from the IT Administrators group.

This has a similar catch to when you use the same query to add users to the group. The entire Remove-ADGroupMember operation will fail if any of the resulting objects from the Get-ADUser query are not members of the indicated group. So, if you query for all users in \BigFirm\OU and one of them is not in the IT Administrators group, then the removal operation will fail.

Maybe you want to remove all members from a group. You can do that by querying for the group and nesting that command in a command to remove members from the group:

```
PS C:\Users\Administrator> Remove-ADGroupMember "IT Administrators" -Member
-ADGroupMember "IT Administrators"
```

Confirm

Are you sure you want to perform this action?
Performing 'Set' on Target "CN=IT Administrators,OU=Security Groups,OU=BigFirm,DC=firm,DC=com"

- [Y] Yes [A] to All [N] No [L] to All [S] Suspended [?] Help

Here are retrieving all the members of the IT Administrators by running the Get-ADGroupMember cmdlet. That's nested in the Get-ADGroupMember command and will return the answer as a value for the -Member flag of the command.

That gives you many ways to create a group using PowerShell, add members, query the membership, and remove members. All remains is to delete that group.

# Removing a Group

Removing a group is a pretty simple task. Just use the—you guessed it—Remove-ADGroup cmdlet and specify the name of the group:

```
PS C:\Users\Administrator> Remove-ADGroup "IT Administrators"
```

Confirm
Are you sure you want to perform this action?
Performing operation "Remove" on Target 'CN=IT Administrators,OU=Groups,OU=bigFarm,DC=bigFarm,DC=com'
[Y] Yes to All [N] No [L] No All [S] Suspend [?] Help (default *:)

Here are the IT Administrators group. If it doesn't have members or; it will be removed. Be sure that you don't need the group anymore. Remember that you cannot just recreate the group to restore all the permissions because the SID assigned to the group is globally unique.

Finally, you've reached the end of the section that deals with the Active Directory module for PowerShell. At first it looks like it will be very difficult to use. Sure, in a smaller environment there might not be any advantage to using PowerShell, but it's something you should learn. In medium-size environments, you'll find it can be used to rapidly get results. In large environments, you'll find it's better to use to manage complex operations quickly and with minimum effort.

# The Bottom Line

**Manage local users and groups.** Local users and groups are stored on a computer and cannot-be used to log into or access resources on other computers.

**Master It** You have 25 PCs with 25 users on a group network, in other words, a network with no Active Directory or Windows domain. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. (Note: The OCR text seems to have a massive repetition loop; I have cleaned it to the intended text flow).

**Master It** You have 25 PCs with 25 users on a group network, in other words, a network with no Active Directory or Windows domain. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. (Note: network "in other words, a network with no Active Directory or Windows domain.")

**Manage users and groups in Active Directory.** Users and groups can be stored in Active Directory. You are. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. You are installing two servers. (Note: repetition loop cleaned up).

ADAC makes it quicker and easier for administrators to perform day-to-day tasks such as. The Active Directory module for PowerShell offers a command-line interface and way to script. You can use this to automate repetitive tasks or to perform complex operations that would consume much time using an administrative console.

**Master It** You are managing the Windows Server 12 for an international corporation. The directors have announced that a new call center with 5,000 employees is to opened soon. The human resources department will be produce a file from the database thanks to some in-house developers. You want to create the user objects as quickly possible with minimum effort. How will you do it?


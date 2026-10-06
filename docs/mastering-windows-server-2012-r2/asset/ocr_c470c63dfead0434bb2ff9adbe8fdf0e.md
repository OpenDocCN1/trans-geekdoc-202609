# ACTIVE DIRECTORY MODULE FOR WINDOWS POWERSHELL

This uses the same example for finding users as we covered just a moment ago. Once we have the objects, you can feed them in parameters via the pipe into Set-ADUser. You're changing the property of all the found users to Member of It.

# Enabling an Account

Earlier we said you might want to create a user object and enable it only when the human user was ready to use. Here's how to enable a user object for Philip Witschi:

```
PS C:\Administrator> Enable-ADAccount -Identity PWitschi
```

# Disabling an Account

We discussed you might want to disable accounts for a certain amount of time before deleting them. Here's how to disable an account:

```
PS C:\Administrator> Disable-ADAccount -Identity PWitschi
```

Finally, you go to the point where you want to delete a user account:

```
PS C:\Administrator> Remove-ADUser -Identity PWitschi -confirm
```

Confirm
Are you sure you want to perform this action?
Performing operation "Remove" on Target "CN=PWitschi,CN=Users,DC=bigfig,DC=com"
[Y] [A] Yes to All [L] [N] No to All [S] Suspend [?] Help (default is "Y")

We've been careful by using the -confirm flag at the end of the Remove-ADUser cmdlet. That will ask whether you want to continue with this action. Doing things from the command line is very quick, so a deletion is something you need to be careful about. If you are writing a script, you will probably not use the -confirm flag because you want the script to execute halfway through without having to interact with it.

That wraps up our coverage on managing users using PowerShell. We'll now move on to group management. To create a group using the New-ADGroup cmdlet, we noticed how similar all these cmdlets are. That's a feature of PowerShell. Set, or New and then something descriptive to identify what the cmdlet does.

```
PS C:\Administrator> New-ADGroup -Name "IT Administrators" -SamAccountName "IT Administrators" -GroupCategory Security -GroupScope DomainLocal -DisplayName "IT Administrators" -Path "OU=Groups,OU=bigfig,DC=bigfig,DC=com -Description "This group is in IT"
```

That command will create a domain local group set to create IT administrators in the \BigFirm OU using these flags:

+   -Name This is the name of the group!

+   -SamAccountName This is the name associated with the pre-Windows 2000 group object attribute.

+   -GroupCategory This will be either Security (or 1) or Distribution (or 0).

+   -GroupScope This will be either DomainLocal (or 0), Global (or 1), or Universal (or 2).

![](bbox=[0.176, 0.943, 0.235, 0.963])

# CHAPTER 8 CREATING AND MANAGING USER ACCOUNTS

- End Task
- Clear All
- Show All

The copy command lets you copy the entire command string from your PowerShell History window, and if you want, you can paste it into the editor of your choice, such as Notepad. You can even select multiple commands by holding the Ctrl key and selecting all the commands you want and then copy them:

You may have realized that this small window gets filled quickly, and if you want to track a certain action, you may have trouble determining which cmdlets belong to which. Because of that you can use the Start Task, End Task, and Clear All tasks. Before we start, make sure the Show All check box, shown previously in Figure 8.79, is deselected. We will explain later what this option does, but for now leave it unchecked and follow these:

1. Clear the All task.
This will empty all the commands from your PowerShell history, and you will have a clean pane.
2. Start Task, which will give you a rectangular description box in which you can type a meaningful description of the task you are going to perform, for, New User.
3. Create a new user in Active Directory using the ADAC, click the OK button on the user-creation dialog, and then end Task.
4. Start Task again, and type into the rectangular description box Delete User.
5. Go to your previously created user in ADAC and delete it.
6. Click End Task once more. You should have a grouped view of your commands, as shown in Figure 8.81.

Figure 8.81
Grouping PowerShell commands

| WINDOWS POWHELL HISTORY | |
| :--- | :--- |
| Search | Copy Start Task End Task Clear All |
| Cmdlet | |
| New User | |
| -New-ADUser | |
| -DisplayName:Name="Test"GivenName="Test"Name="Test"-Path... | |
| -New-ADUser | |
| -DisplayName:Name="Test01"GivenName="Test01"Name="Test01... | |
| -Set-AccountPassword | |
| -Identity="Test01,OU,OU=Bigfirm;DC=bigfirm,DC | |
| -Enable-ADAccount | |
| -Identity="Test01,OU,OU=Bigfirm;DC=bigfirm,DC... | |
| -AccountNotDeleted=False -AllowReversiblePasswordEncry... | |
| -Set-AccountControl | |
| -Set-ADUser | |
| -ChangePasswordAtLogon=True-CN=Test01,OU,OU=Bigfirm... | |
| Delete User | |
| -Remove-ADObject | |
| -Confirm=$False -Identity="Test01,OU,OU=Bigfirm... | |

# ACTIVE ACTIVE DIRECTORY MODULE FOR WINDOWS POWERSHELL

Not only do you get a structured overview in your window, but if you copy the commands into your editor, you will see that the descriptions "New User" and "Delete User" are added as a comment in your script, which is really helpful.

The last option you can center is Show All. Active Directory Administrative Center will show even more commands in the PowerShell History.

7. Select the BigFirmUsers OU, which we created, and hit F5 to refresh the OU content.
Notice that you get new commands that you didn't see before. Why is that? Think about it: ADAC is on top of PowerShell, and if you refresh your OU, you actually force ADAC to query the OU. In PowerShell this is done by the Get-ADObject cmdlet. You probably don't like to get flooded with PowerShell commands, so you are better off deselecting this object.

Now you've had an introduction to creating objects in PowerShell. In the next section you will get a more detailed view into basic PowerShell.

# Active Directory Module for Windows PowerShell

The Active Directory module for Windows PowerShell allows you to perform command-line and scripted operations using Microsoft's new shell language. Like ADAC, it is available only for Windows Server 2012 and 8 (using Remote Administration Tools). Also ADAC, it requires the Directory Services to be installed on at least one domain controller in the domain you wish to manage. You can also install the Directory Services Gateway (http://technet.microsoft.com) on Windows Server 2003 or Windows Server 2008 for optimum performance. We will now cover how to manage users and groups using this module. We strongly recommend that you check out the site at http://technet.microsoft.com/en-us/library/ss5274.aspx to read more about this subject. We'll cover the more common scenarios. Launch the Active Directory module for Windows PowerShell from Windows Server 2012 R2 when you need PowerShell for the first time, you need to load the Active Directory module by typing:

```powershell
PS:\Users\Administrator> Import-Module ActiveDirectory
```

In Windows Server 2012 you are in a comfortable situation that the module will be loaded automatically. So when you enter a command that the shell recognizes as an Active Directory cmdlet, the module will be loaded automatically. The basic PowerShell commands for creating Active Directory objects like users, groups, computers, OUs, and so on will also work in PowerShell.

# UPDATE HELP FILES

I highly recommend before diving into PowerShell 3.0 / 4.0 that you update the stored files. You can do that by running the Update-Help command. This command connects to the Internet and downloads the latest help files for the current modules loaded in your shell and those installed on your computer. The help files are XML files which will be extracted and copied to the appropriate path automatically. So if you don't have an Internet connection, you can use the Save-Help command where you can specify a path to store the files, for example, Update-Help -SourcePath C:\Temp. There is a lot more information available if you are interested in this topic, go to: https://technet.microsoft.com/en-us/library/hh8972.aspx.

# Creating Users

Let's start with some user administration. It makes sense to create a user first. The PowerShell cmdlet for it is New-ADUser:

```powershell
PS:\Users\Administrator> New-ADUser "Philipp Witschi"
```

PowerShell contains help and examples. If you want help with New-ADUser, then you can run this command:

```powershell
PS:\Users\Administrator> Get-Help New-ADUser
```

You can get examples of cmdlet usage like this:

```powershell
PS:\Users\Administrator> Get-Help New-ADUser -examples
```

These help commands are consistent with all the cmdlets supplied by Microsoft modules. There are a few other useful things to note. You can add a -whatif flag to a cmdlet to see what will happen if you run it:

```powershell
PS:\Users\Administrator> New-ADUser PWitschi -whatif
What: Performing operation "New" on Target "CN=PWitschi,CN=Users,DC=bigfig,DC=com".
```

Nothing is actually changed; this simulates the command and tells you what the result would be if you removed the -whatif flag. You can also tell PowerShell to seek a confirmation before executing the command. That's useful so you can double-check what you have typed before running the command:

```powershell
PS:\Users\Administrator> New-ADUser PWitschi -confirm
```

Confirm
Are sure you want to perform this action?
Performing operation "New" on Target "CN=PWitschi,CN=Users,DC=bigfirm,DC=com".
[Y] Yes [A] Yes to All [N] No [L] No to All [S] Suspend [?] Help (default "Y")

You can use -whatif -confirm on all the following cmdlet examples to be sure what you are doing is correct.

The previous New-ADUser command creates the new user, PWitschi, in the default location for new users, usually the Users container. As we stated earlier, that's not the best place for storing user accounts. It contains a number of special users and groups, so you should treat it as specified. You have a location in \BigFirm\ your user accounts. Say you want to specify a number of configurations for this user. This is what you can:

```powershell
PS:\Users> New-ADUser "Philipp Witschi" -SamAccountName PWitschi -GivenName "Philipp" -Surname "Witschi" -DisplayName "Philipp Witschi" -Path "OU=Users,DC=BigFirm,DC=com" -UserPrincipalName PWitschi@bigfirm.com
```

Let's look at the flags:

- -SamAccountName is the user logon name (pre-Windows 2000) in the user object properties. In this case, you entered PWitschi, so the user will be able to log in using the domain name Big-Firm\PWitschi.
- -GivenName refers to the first name of the user.
- -Surname is the last name of the user.
- -DisplayName is the display name of the user object.
- -Path refers to the distinguished name of the OU where you want to create the new user object. In this case, it will be the \BigFirm\Users OU in the bigfirm.com domain.
- -UserPrincipalName the UPN is the user logon name in the user object, that is, the one that takes an email-like form.

If you run this command, you'll find the new user is created in the OU that you have specified. You'll also find that the user is disabled. PowerShell wants to specify that the user should be enabled.

# Setting Passwords

Speaking of passwords, you didn't set one, did you? You're forced to do so. However, if you want to, you can specify a password using the -AccountPassword flag. There's a catch here: -AccountPassword requires a secure string to be entered, so you can't just add My Password. You have to create a secure string before creating the user.

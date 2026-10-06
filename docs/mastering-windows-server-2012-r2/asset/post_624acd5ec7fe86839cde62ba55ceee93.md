
# CHAPTER 7 ACTIVE DIRECTORY IN WINDOWS SERVER 2012

If you are experiencing connectivity problems and you notice that DNS is missing records, there is a simple fix. Go to command prompt and issue the following two commands:

```
net stop netlogon
```

```
net start netlogon
```

The netlogon service will re-create the records, and you will be in business.

# RAISING DOMAIN AND FOREST FUNCTIONAL LEVELS

You may want to raise your domain and/or forest functional levels after you have initially created your forest or after upgrading from a Windows Server 2008 environment. The primary reason why you would want to do so is to take advantage of additional features available at the higher levels. Although Windows Server 2012 forest functional levels don't offer any new features, you might still need to raise the domain functional level to Windows Server 2012. Anybody, the big-picture steps your domain controllers would take as follows:

- 1. Ensure your domain controllers are running Windows Server 2012.
- 2. Raise the domain functional level to Windows Server 2012.
- 3. Raise the forest functional level to Windows Server 2012.

It is important to remember that once you raise the level, there is no turning back. If your current domain functional level is Windows Server 2008 R2 and you raise it to Windows Server 2012, you will no longer be able to promote anything less than a Windows Server 2012 server to a domain controller. If that fits in your plans, raise the levels.

# FUNCTIONAL LEVELS CAN(NOT) BE LOWERED

Well, that's not exactly true. If you have a functional level of 2012, you could lower the forest and domain functional level to Windows Server 2008 R2. It does not work in the GUI but you could run two PowerShell commands to accomplish the task.

First, lower the functional level to Windows Server 2008 R2:

```
Set-ADForestMode -Identity "bigfirm.com" -ForestMode Windows2008R2Forest
```

And as a second step you lower the domain to Windows Server 2008 R2:

```
Set-ADDomainMode -Identity "bigfirm.com" -DomainMode Windows2008R2Domain
```

Keep in mind that lowering the forest functional level will also break the deployed features, for example, Dynamic Access Control.

There are four tools you can use to raise the domain functional levels:

- Active Directory Users and Computers (to raise the domain functional level)
- Active Directory Domains and Trusts (to raise the forest functional level)
- Active Directory Administrative Center (to raise the domain and forest functional levels)
- PowerShell 3.0 (to raise the domain and forest functional levels)

# AN INTRODUCTION AND ACTIVE DIRECTORY BASICS

Depending on your version, whichever method is appropriate for you. Because the Active Directory Administrative Center is new, we will now have a look at this console and how to raise the domain functional level there.

You can raise the domain functional level by following these steps:

- 1. Launch the Active Directory Administrative Center by pressing WIN+R to start the Run dialog and typing dsac.exe into the text box. Click OK.
- 2. Also start the console for the Start screen.
- 3. Right-click the domain name, and select “Raise the domain functional level,” as shown in Figure 7.27.

Figure 7.27 Raising functional levels in Active Directory Administrative Center

![](img/41a83208e6906a3732620203b836cea7_338_0.png)

- 4. Review the information on the Raise Domain Functional level.

Notice that this page informs you what the current functional level is and gives you the option to raise it. Select Windows Server 2012 from the drop-down box.

- 5. Click OK.

You will receive another warning reminding you that this action isn’t reversible.

- 6. Click OK.

After a moment, a dialog box will indicate that the level was raised successfully.

- 7. Click OK.

You can raise the forest functional level the same way you raised the domain functional:

# ACTIVE DIRECTORY IN WINDOWS SERVER 2012

- 1. Launch the Active Directory Administrative Center by pressing WIN+R to start the Run dialog and typing dsac.exe into the text box. Click OK.
- 2. Also start the console for the Start screen.
- 3. Right-click the domain name and select "Raise the forest functional level."
- 4. Review the information on the Raise Forest Functional page.

Notice that this page informs you what the current functional level is and gives you option to raise it. Select Windows Server 2012 from the drop-down box.

- 5. Click OK.

You will receive a warning reminding that this action isn't reversible.

- 6. Click OK.

After a moment, a dialog will indicate the level was raised successfully.

- 7. Click OK.

Many of the additional features of the higher functional levels will be available automatically. Only a few (such as the Active Directory Recycle Bin) require additional steps to enable them.

# RAISE DOMAIN FORESTS LEVELS WITH POWHELL

Raising functional levels or forest functional level is not an administrator's daily task. Ever, you will do it few times in your career, and you will probably not use a script to raise these levels. Therefore, this might not be a perfect case for using PowerShell.

# USING NETDOM

A valuable command-line tool is Netdom (short for "domain manager"). It is available at the command prompt to manage trusts in environments with more than one domain.

# JOIN A COMPUTER TO A DOM

If you want to join a computer to a domain from the command prompt or via a script, you can use Netdom. The simplest implementation is as follows:

```
Netdom join server01 /d:bigfirm.com /reboot
```

This command will join the computer named server01 to the domain bigfirm.com and force a reboot. Normally, the account for a computer that has joined the domain is placed into the Computers container. As mentioned previously, you can use the redirc command to have computer accounts created somewhere else.

# RENAME COMPUTERS (INCLUDING DOM CONTROLLERS)

You can use the netdom computername to rename domain controllers and member servers. In early versions of Windows, renaming a domain controller wasn't possible unless you first promoted it. Be aware that if you use Netdom to rename a domain controller, it may take a couple of reboots before everything settles. For example, if you have a domain controller DC01 in the bigfirm.com but you want to rename it to DC03, first give it an alternate name with the following command:

```
Netdom computername DC01 /add:DC03.bigfirm.com
```

At this point, the server has two names: its primary name and an alternate name. Next, rename the computer to the alternate name with this command:

```
Netdom computername DC01 /makername:DC03.bigfirm.com
```

Netdom will indicate and prompt you to reboot the server. With your reboot, your domain controller will change the alternate name to its primary name. As a last step you need to remove the old name DC01 from the domain controller computer object with this command:

```
Netdom computername DC03 /remove:DC01.bigfirm.com
```

Now your domain controller has a new name.

# RAISE DOMAIN FORESTS LEVELS WITH POWHELL

Raising functional levels or forest functional level is not an administrator's daily task. Ever, you will do it few times in your career, and you will probably not use a script to raise these levels. Therefore, this might not be a perfect case for using PowerShell.

It is also possible to fetch get with Netdom, but it tends to be more difficult than using the directory service command-line tools (such as DSMove). For example, if you want to move the computer account from the Computers container to the Sales OU, you could follow the NetDom join with the DSMove command.

```
Dsmove "CN=Server01,CN=Computers,DC=bigfirm.com,DC=com" -newparent
"OU=Sales,DC=bigfirm.com,DC=com"
```

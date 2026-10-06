# Using the New Features for User and Group Management

Everything we have discussed in this chapter applies to both Windows Server 2008 R2, Windows Server 2012 and Windows Server 2012 R2. Windows Server 2012 has two major changes that are relevant to basic user and group management:

+   - Microsoft has renewed the Active Directory Administrative Center (ADAC) and built it on top of PowerShell. In addition, new features have been integrated into the console, like a GUI for Active Directory Recycle Bin and Fine-grained Password Policies.
- Microsoft has added PowerShell History into the ADAC for more easily managing and creating users and groups as well as other objects.
- Windows Server 2008 R2 has already natively integrated PowerShell 2.0, and in terms of managing users, there are not new cmdlets in Windows Server 2012. Although Windows Server 2012 has integrated the brand-new PowerShell 3.0 and Windows Server 2012 R2 PowerShell 4.0, most new cmdlets in the Active Directory field are for managing the Active Directory components and not users.
- However, you can download Quest's PowerShell Commands for Active Directory from http://tinyurl.com/5otff8. These cmdlets have syntax like the built-in Windows Server 2012 cmdlets, but in ways they offer a better support and flexibility, in example, of of accessing user attributes. In this section we will be covering the new Windows Server 2012 PowerShell cmdlets.

# Active Directory Administrative Center

Microsoft extended and finally adjusted the Active Directory Administrative Center to give you a more task-oriented command interface. Rumor has it Active Directory Users and Computers (ADUC) will be discontinued and Microsoft's focus will be on Active Directory Administrative Center. However, in Windows Server 2012 both tools are available, and one cannot work without the other. Since ADAC is just a GUI for PowerShell functionality, it is clear: PowerShell is worth investigating the power of this tool. Microsoft wanted to make it quick and easy to do for repetitive tasks, such as dealing with user lockouts on Windows Server 2012 domain controller. You can also use it on Windows 8 if you install the Remote Active Directory Administration Tools for Windows 8; see http://www.microsoft.com/en-us/download/details.aspx?id=28972. If you are already running Windows 8.1 and you would like to manage Windows Server 2012 R2, go to http://www.microsoft.com/en-us/download/details.aspx?id=39296. It takes a little longer than Active Directory Users and Computers to load, so you might find it useful in the morning and later.

# ADAC Essentials

You can see what we mean by task oriented when ADAC opens, as shown in Figure 8.65. The center pane is an interface dedicated to resetting passwords and unlocking user accounts. These are the most common Active Directory tasks for IT, so it makes sense that the tool is right there.

What happens without ADAC when a user calls the help desk ask to have their password reset or their account locked? The help-desk technician needs to search the organizational units in Active Directory for the user. Then they have to right-click the user and
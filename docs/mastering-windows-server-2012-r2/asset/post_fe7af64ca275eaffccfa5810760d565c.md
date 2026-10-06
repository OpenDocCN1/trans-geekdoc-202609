
# CHAPTER 7 ACTIVE DIRECTORY IN WINDOWS SERVER 2012

Make sure you document the password you set here. Many organizations document critical passwords by writing them down and storing them in a safe. You won't be able to access DSRM command without this. The DSRM administrator account password is sometimes confused with the regular administrator password you set for the Domain Admin account, but it is different. From a security standpoint, this DSRM password is critical in that you can locally log onto a domain controller and use it to gain access to the Active Directory database. If you realize all passwords are stored in this database, you will think twice about where you store the DSRM password.

## CHANGING THE DSRM PASSWORD

If you have 100 domain controllers, it is somewhat difficult to control each DSRM password, or you might need to change a DSRM password, by running the DSGMNT or NTDSUTIL on a running domain controller. You don't need to enter DSRM mode to change the DSRM password. You can find more about this TechNet:

http://tech.microsoft.com/en-us/library/cc75334.aspx

One geeky to keep your DSRM password known to you is to synchronize the password with a domain account. How does this work? First, you need to create a domain user account, let's say DSRMaccount. This can be a regular domain user account. Next, start an elevated prompt and type the following command:

```
NTDSUTIL
Set password
SYNC FROM DOMAIN ACCOUNT DSRMaccount
Q
```

![](img/41a83208e6906a3732620203b836cea7_309_0.png)

Your DSRM account is synchronized with the DSRM Account in Active Directory. This does not permanently synchronize the password; it synchronizes it for the moment. Therefore, if you change the DSRM Account password, you'll need to execute the command again. You could either apply a GPO to all domain controllers or write a PowerShell script to execute this command on all domain controllers. You would just to call C:\Windows\System32\NTDSUTIL.exe and submit the parameters as shown:

```
"SET DSRM PASSWORD" "SYNC FROM DOMAIN ACCOUNT DSRMaccount" Q Q
```

There is a great post about this on TechNet:
http://blogs.technet.com/b/askds/archive/2009/03/11/ds-restore-mode-password-maintenance.aspx

## AN INTRODUCTION AND ACTIVE DIRECTORY BASICS

### RUNNING THE ACTIVE DIRECTORY DOMAIN SERVICES CONFIGURATION WIZARD

Now that you know what you will encounter, the next step is to add the Active Directory role and then run the Active Directory Domain Services Configuration Wizard. In Windows Server 2012, adding the Active Directory role adds all the necessary binaries and then you can configure Active Directory.

The following steps assume you have a clean installation of Windows Server 2012 without any additional roles installed. If you have installed additional roles, you may have some minor differences.

- 1. Log onto a Windows Server 2012 server using an account with local administrator privileges.
- 2. Start Server Manager and choose Manage ➤ Add Roles and Features.
- 3. Review the information on the “Before you begin” page.
- 4. Select “Role-based or feature-based installation.”
- 5. Select your destination for the server pool (see Figure 7.8).

![](img/41a83208e6906a3732620203b836cea7_310_0.png)

- 6. Select the Active Directory Services role and add the recommended features, as Remote Server Administration Tools.
- 7. On the Features dialog you don't need to select anything.
- 8. Review the Active Directory Domain Services dialog.
- 9. If you want to restart the server automatically, select the option “Restart the destination automatically if required.”

After the binaries are installed, a yellow exclamation mark appears in Server Manager.

- 10. Click the yellow exclamation mark and click the “Promote this to a domain controller” link.

This will start the Active Directory Domain Services Configuration Wizard.

- 11. On the Active Directory Deployment Configuration dialog, select “Add a new forest and enter a name for the root domain (see Figure 7.9). Choose any two-part domain name you like. Click Next.

FIGURE 7.9
Add a new forest

![](img/41a83208e6906a3732620203b836cea7_311_0.png)

- 12. Leave the forest and domain functional level at its default Windows Server 2012. Make sure the Domain Name System (DNS) Server option is selected to install the DNS role. The Global Catalog (GC) option is selected and cannot be changed, because this is the first domain controller in the domain. Enter the Directory Services Restore Mode (DSRM) password twice. Click Next.

Active Directory will attempt to locate a DNS server. If you have not pre-staged a server, you will now receive a warning, letting you know the zone for your domain can’t be created. This is not normal.

- 13. Click Next to continue.
- 14. There is no reason to change the NetBIOS name for the domain. Leave it as its default and click Next.

- 15. The path for database, log file, and SYSVOL will appear. You could change the path of the files but accept the defaults and click Next.
- 16. Review the options on the summary page and click Next to continue. Notice in the lower-right corner there is a button called “View script” (See Figure 7.10).

## FIGURE 7.10
“View script"

![](img/41a83208e6906a3732620203b836cea7_312_0.png)

If you click this button a Notepad window will open and present the PowerShell command to set up an exact forest with all the options you selected.

- 17. Review all the commands and all the options (see Figure 7.11).

You could open a PowerShell command window on any Windows Server 2012 server where you have the Active Directory Domain Services role installed and copy and paste these commands. At the PowerShell command you will be prompted for the DM password. Because of security reasons the password will not be visible in the PowerShell script.

But if you want to provide the password without being prompted every time you execute the script, you could use the line in the previous example that will provide the password to the script:

```
-SafeModeAdministratorPassword (ConvertToString("password") -AsPlainText -Force) '
```

- 18. When you finish the wizard you will be on the On Prerequisite Check page and two warnings will appear, the wizard will show a green mark indicating that all prerequisites passed successfully. As previously discussed, these warnings are normal. Click Install.

## FIGURE 7-11
PowerShell commands generated by the wizard

![](img/41a83208e6906a3732620203b836cea7_313_0.png)

Now it is time to take a break and install the server instance. Once the wizard finishes running and reverts, you will be prompted to log on.

- 19. Press Ctrl+Alt+Del

The password for the domain is the same as the password for the administrator. Figure 7-12 shows domain controller using PowerShell.

## FIGURE 7-12
Installing domain controller using PowerShell

![](img/41a83208e6906a3732620203b836cea7_313_0.png)

## AN INTRODUCTION AND ACTIVE DIRECTORY BASICS

### ADMINISTERING WINDOWS SERVER 2012 REMOTELY

The recommended way of administering Windows 2012 is remotely, using Remote Server Administration Tools (RSAT). To use RSAT, you must first install it on your client computer. In Windows Server 2012, RSAT is a feature that can be installed on demand.

The following tools can be installed:
- Active Directory Domain Services
- DNS Server
- DHCP Server
- IP Address Management
- Policy Management
- Remote Services Management
- File Services Tools
- Print Services Tools
- Hyper-V Tools
- Management Tools

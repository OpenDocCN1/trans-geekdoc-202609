FilesSpecsToBackup :
FilesSpecsToExclude :
ComponentsToBackup :
BMR : False
SystemState : False
OverwriteOldFormatVhd : False
VbackBackupOptions : VSCopyBackup

Now that you see the New-WBPolicy properties, you can use the following script to set them. This script will set the policy to back everything in the Sales folder every morning at 9 a.m.:

```
PS C:\Users\Administrator> $policy = New-WBPolicy

$fileSpec = New-WBFileSpec -FileSpec C:\Sales
Add-WBFileSpec -Policy $policy -FileSpec $fileSpec

Add-WBareMetalRecovery $policy

$disks = Get-WBDisk
$backupLocation = New-WBBackupTarget -Disk $disks[2]
Add-WBBackupTarget -Policy $policy -Target $backupLocation

Set-WBSchedule -Policy $policy 09:00

Set-WBPolicy -Policy $policy $
```

That will get you started using PowerShell to handle your Windows Server Backup. You can reference the complete cmdlet list for Windows Server Backup at http://microsoft.com/en-us/library/ee706683.aspx.

# The Bottom Line

Use the new functionality in Server Core. The Windows Server 2012 Server operating system is a trimmed-down version of its full installation. The removed code reduces the profile for security threats and also reduces performance. The primary administration interface is the command prompt. It can perform well but not all of the roles with the full installation.

+   **Master It** The Windows Server 2012 Server Core version differs from the original release in Windows Server 2008. What are those key differences, and how does that impact the roles the server can perform?

**Install and configure Server Core.** The installation of Server Core is the same as installing a full installation of Windows Server 2012. The full installation provides a list of initial tasks such as joining the domain, initiating automatic updates, and installing features. Each of these operations has a command associated with it.

+   **Master It** Server Core has a specific script to perform several common tasks that edit the registry. What is this script's name? What parameter can provide a list of additional commands to perform many of the common configuration tasks?
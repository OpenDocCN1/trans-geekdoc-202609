# CHAPTER 12: WINDOWS 2012 R2 STORAGE: STORAGE SPACES, SANISH ABILITIES, AND BETTER TOOLS

it is very hard to predict what you may need in a year's time. How would you manage your storage to get the most out of it and meet your future storage needs?

**Master It** In your lab create a storage pool using the GUI with three disks. Create a virtual disk three times the size of the total usable capacity of the disk. Format it and get it ready to use.

**Solution** In Server Manager, under *File and Storage Services*, navigate to Storage Pools. From the primordial pool, right-click and select a new storage pool. Enter a name and then select three physical disks (note their individual capacities) and add them up. Select your pool and name from the Storage Pool window, and create a new virtual disk from it. Give it a useful name and select Parity as the storage layer. Select Simple and Thin the Disk. For its size use the total capacity you worked out three times. Create a volume on that virtual disk and copy some files into it.

**Create additional storage on a virtual disk.** A common occurrence in enterprises today is last-minute requests for provisioning of applications that require large amounts of storage. Often the storage available locally in the server is not large enough to meet the need. How can you get additional storage onto the server without adding local storage?

**Master It** In your lab deploy an iSCSI target, create a virtual disk, and then connect to your newly created target.

**Solution** New 2012 R2 Microsoft has introduced a variety of cmdlets to help you configure the iSCSI target and client software. The steps you would take to configure this figure using PowerShell are listed as follows:

+   1. From PowerShell on the server you have selected as your iSCSI target, run the following cmdlet:
Add-WindowsFeature FS-ISCSITarget-Server -IncludeManagementTools
2. Create a new iSCSI target:
New-ISCSITarget -TargetName TestTarget1 -InitiatorID iqn.1995-01.com.microsoft:server01.contoso (Change the id to that of your remote server).
3. Add a new virtual disk to the pool using the following cmdlet:
New-IsciVirtualDisk -path e:\newdisk.vhdx -SizeBytes 20GB
4. Add the disk to the previously created iSCSI target, as shown here:
Add-DiskVirtualTargetMapping -TargetName TestTarget1 -path e:\newdisk.vhdx
5. On the remote server where you need the extra storage, from an elevated PowerShell prompt run the following:
Start-Service -Name msiscs -StartupType Automatic
Start-Service msiscs
6. Type:
New-iscsitargetportal -targetportaladdress TestTarget1
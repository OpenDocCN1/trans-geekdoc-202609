# CHAPTER 32 WINDOWS SERVER 2012 R2 AND ACTIVE DIRECTORY BACKUP AND MAINTENANCE

+   Managing backup versions and backup retention has been improved, and you can define deletion policies to manage your used space.

+   The limitation of only backing up volumes with a capacity of no than 2 TB and size of 512 bytes has been removed. Large volumes or drives as the new 64 TB virtual disk (VHDX) format can be backed up, and sizes of 4 kilobytes are supported.

+   Cluster Shared Volumes (CSVs) are now supported although there are a few limitations, as virtual machines hosted on CSVs can't be backed up and full CSV recovery isn't available.

+   Neater configuration of System State component reporting means that the System Writer now reports service files to be part of the Windows 8 client operating system and not Windows 2012 R2. This means a more efficient system state backup.

# BACKING UP TO FILE WITH WINDOWS SERVER BACK

Windows Server Backup does not support tape backups (this has been the case since Windows Server 2008 R2). If your organization requires the more traditional backup-to-tape method, then you will need to deploy a product, such as Microsoft's System Center 2012 R2 Data Protection Manager.

# Installing Windows Server Backup

Windows Server Backup is installed as a feature within Windows Server 2012 R2 and comprises three components:

+   Microsoft Management Console (MMC) snap-in

+   Command-line tools (wbadmin.exe)

+   Windows PowerShell cmdlets

Windows Server Backup is not installed by default, here's what you need to do to get it up and running:

+   1. To begin, log on to your domain-joined Windows Server 2012 R2 installation with an account that has administrative permissions, and from the Server Manager > Local Server > Manage, choose the Roles and Features option.

+   2. In the Before You login box, click Next.

+   3. Ensure that Role-Based or Feature-Based Installation is selected in the Select Installation Type dialog box, then click Next.

+   4. In the Select Destination dialog box, leave the default option of "Select a Server from the Server Pool" checked, confirm that your server is highlighted in the Server Pool section, and then click Next to continue.

+   5. When you reach the Server Roles dialog box, just click Next to continue.

# CHAPTER 32 WINDOWS SERVER 2012 R2 AND ACTIVE DIRECTORY BACKUP AND MAINTENANCE

- Managing backup versions and backup retention has been improved, and you can define deletion policies to manage your used space.

- The limitation of only backing up volumes with a capacity of no less than 2 TB and size of 512 bytes has been removed. Large volumes or drives as the new 64 TB virtual disk (VHDX) format can be backed up, and sizes of 4 kilobytes are supported.

- Cluster Shared Volumes (CSVs) are now supported although there are a few limitations, as virtual machines hosted on CSVs can't be backed up and full CSV recovery isn't available.

- Neater configuration of System State component reporting means that the System Writer now reports service files to be part of the Windows 8 client operating system and not Windows 2012 R2. This means a more efficient system state backup.

## BACKING UP TO FILE WITH WINDOWS BACK

Windows Server Backup does not support tape backups (this has been the case since Windows Server 2008 R2). If your organization requires the more traditional backup-to-tape method, then you will need to deploy a product, such as Microsoft's System Center 2012 R2 Data Protection Manager.

## Installing Windows Server Backup

Windows Server Backup is installed as a feature within Windows Server 2012 R2 and comprises three components:

- Microsoft Management Console (MMC) snap-in
- Command-line tools (wbadmin.exe)
- Windows PowerShell cmdlets

Windows Server Backup is not installed by default, here's what you need to do to get it up and running:

- 1. To begin, log on to your domain-joined Windows Server 2012 R2 installation with an account that has administrative permissions, and from the Server Manager > Local Server > Manage, choose the Roles and Features option.

- 2. In the Before You login box, click Next.

- 3. Ensure that Role-Based or Feature-Based Installation is selected in the Select Installation Type dialog box, then click Next.

- 4. In the Select Destination dialog box, leave the default option of "Select a Server from the Server Pool" checked, confirm that your server is highlighted in the Server Pool section, and then click Next to continue.

- 5. When you reach the Server Roles dialog box, just click Next to continue.

- 6. When you reach the Select Features dialog box, scroll down the list until you find Windows Server Backup, check the box, and then click Next.

- 7. At the Confirm Installation Selections dialog box, click the Install button to start the installation, and click Finish once the wizard has finished.

## Backing Up and Restoring a Full Server

The biggest difference between storing backups in a network shared folder versus a local disk is that Windows Server Backup will store multiple versions of backups on a local disk but will store only the most recent version of a backup in a remote location. Having multiple backups for a specific server computer means you can recover from changes made on those days as well as recover from a complete data loss. This is most useful when restoring data that may have been changed or deleted prior to the most recent backup.

When backing up to disk, consider using some type of removable disk, such as an external USB or eSATA hard disk. A better implementation would involve multiple disks that could then be restored to off-site storage to provide a higher level of disaster-recovery. Windows Server Backup can identify disks to use for backup and automatically use whichever disk is present, deleting the oldest backup on the disk to make room for the current backup operation.

Performing a full server backup is one of the easiest types to perform and is one of the best types in terms of recovery. A full server backup includes the following parts:

- All local volumes (virtual disks hosted on local volumes will not be backed up if they are online)
- Critical volumes
- System state

With a full backup, you can recover individual files and folders and entire volumes in case of failure. You can also perform a “bare-metal” recovery if you have replaced the entire server computer (or at least the hard disks containing the operating system and system state) and there is no operating system installed. The drawbacks of a full server backup are the size of the backup and the time required to perform the backup.

## PERFORMING A FULL SERVER BACKUP

These steps assume that you will be performing a full server backup to a local disk:

- 1. From Server Manager > Local Server > Tools, click Windows Backup to open.
- 2. From the left pane, click Backup Schedule.
- 3. In the Getting Started dialog, click Next.
- 4. Select "Full server (recommended)" for the backup type, then click Next.
- 5. Set the time of day to start the backup, as shown in Figure 32.
- 6. Click Next.
- 7. Select the disk to use for the backup. To use off-site rotation, specify multiple disks on this page. Click Next.
- 8. You will be warned that finishing this wizard will cause the selected disks to be formatted, losing any data on the disks.
- 9. If you are certain you want to use the selected disks, click Yes to proceed.
- 10. Review your options for the scheduled server backup. If you are satisfied with the options, click Finish to format the disks and start the backup.

## WHEN TO UP

Remember that performing a backup requires heavy disk and processor cycles. Because of this, backups should be performed only when user activity is low, such as overnight.

## PERFORMING A FULL SERVER BACKUP FROM THE COMMAND LINE

Windows Backup's command-line component, wbadmin.exe, can be used in cases where you want to script backup operations or when you prefer to use the command line to maintain a server. These steps assume that you are creating a scheduled full backup using the command line:

- 1. Open an elevated command prompt. You must be a member of the Administrators or Backup Operators group to perform these steps.

- 2. Enter the following command:
wbadmin.exe enable backup -vssFull -schedule:02:00 -addtarget:E: -include:C:\
The vssFull switch indicates a full server backup, and -addtarget defines the destination path to store the backup. -include:C:\ indicates that the C drive should be included. When you use a drive with -include, you must include the final backslash. Figure 32-4 shows the result of this command.

- 3. Enter the following command to start the backup you just created:
wbadmin.exe start backup

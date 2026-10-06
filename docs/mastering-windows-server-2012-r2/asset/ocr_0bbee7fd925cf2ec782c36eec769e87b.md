+   4. In the Add Custom Field page, enter a field name for your custom field within the log file.

The field name cannot have any spaces.

+   5. For the source type, you can select from Request Header, Response Header, or Server Variable.

+   6. For the source, select the name of the HTTP header or server variable that contains a value that you want to log, or you can enter your own custom source string.

+   7. Click OK.

+   8. Click Apply in the Actions panel to apply your new settings.

Your log file has "-x" appended to the filename to show that it contains custom fields. It is worth pointing out that the total size of the data collected from all the custom fields cannot exceed 64 KB. If it does, IIS will truncate the data.

# # Backing Up and Restoring Data

No discussion of IIS 8 would be complete without at least mentioning disaster recovery. After, no one expects anticipation or system failures, but it's best to have a plan for the inevitable. Frankly, the architecture of IIS 8 makes it a simpler network application to back up. We have already discussed taking snapshots of sites for portant; those snapshots could be used to restore a site to a previous version. Also, the XML configuration files reside on NTFS and as need only backed up as part of the regular I/O backup strategy. It is worth pointing out that a system state backup will back up the database and not the configuration files.

So, if it's just a matter of backing up the configuration and content files, is there anything unique to IIS 8 about backing up? Just one thing—the PowerShell commands that can be used to create, restore, delete, and list backups:

+   * To generate a backup, use this:

```
Backup-WebConfiguration -Name {backup name}
```

+   * To restore a backup, use this:

```
Restore-WebConfiguration -Name {Backup name}
```

+   * To delete a backup (clean up), use this:

```
Remove-WebConfigurationBackup {Backup name}
```

+   * To list backups, use this:

```
Get-WebConfigurationBackup
```

These PowerShell commands can be written into a script and scheduled with the weeks. But what if something goes wrong with the OS, and unknown to the IIS administrator there has been no backup created of the applicationhost.config file in weeks? Not to worry, IIS maintains a configuration history of applicationhost.config according to the default schedule in the %windir%system32\inetsrv\config\iis_schema.xml file. These automatic backups will appear in the results of a Get-WebConfiguration list PowerShell command along with manually generated backups and can be restored with the Restore-WebConfiguration PowerShell command.
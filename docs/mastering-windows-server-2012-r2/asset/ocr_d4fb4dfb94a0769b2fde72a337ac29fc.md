# CHAPTER 31 PATCH MANAGEMENT

In the next section we are going to shift away from the client settings and look at an overview of the migration from your current WSUS deployment to Windows Server 2012 R2 and the built-in role for Windows Server Update Services.

# Migration from WSUS 3.0 to Windows Server 2012 R2

WSUS 3.0 is packaged as a stand-alone installer available from the Microsoft Download Center, whereas WSUS v6 (or 4.0 as some refer to it) is a built-in role in Windows Server 2012 R2. In this section, you will learn the basics of how to migrate from your WSUS 3.0 installation to the new built-in of Windows Server 2012 R2.

Microsoft provides an outline for a four-step process to migrate from your existing WSUS to a new destination server running Windows Server 2012 R2. You can find this outline on TechNet at http://tinyurl.com/c31wsusmigrate.

You need to consider many things before doing any migration in your production environment. Making sure you have a solid review and inventory of all servers should always be a secondary priority only to all the possible migration scenarios.

Windows Server 2012 R2 Standard and Datacenter editions are supported as destination servers, and migrating from a physical to a virtual OS. The upgrade will support the migration from SQL or to Windows Internal Database (WID) as part of this migration process. Additionally, you can migrate from WID to SQL server.

The process to migrate from WSUS 3.0 to Windows Server 2012 R2 WSUS infrastructure requires some effort but it is critical that you have a backup/back-out plan if something does not work as expected. When starting your migration process, the initial effort requires taking all of WSUS updates and moving them from your old source server to the new Windows Server 2012 R2 destination server. Utilizing tools like XCopy or Robopy is a viable option, but using PowerShell cmdlets and management is far more important to master. Utilizing PowerShell to move binaries like yours is explained in full detail here: http://tinyurl.com/c31PSbackup.

# Backing Up Your WSUS Database

Before tackling any major migration task, you should always have a solid backup of the configuration, patches that have been applied, and databases. Always make sure you have tested the backup-and-restore process before any major upgrade or migration tasks.

Part of the best practices migration strategy is to back up your WSUS 3.0 SP2 database and restore that on the new destination server. Once you have restored your new Windows Server 2012 R2 WSUS v6, things should transition smoothly and with no loss of reports, compliance data, or superseded patches.

Backups for the WSUS information and the method used to restore them will depend on the type of backup you are doing. There is one way to backup and restore the Windows Internal Database and a series of different steps if you are leveraging SQL Server as your database server. You can review the backup of SQL here here: http://tinyurl.com/c31sqlbackup.

The WID is stored in the Object Explorer; if you expand the databases it will be labeled in all instances SUSDB.

For more in-depth information about WSUS backups and step-by-step guidance for this, refer to http://tinyurl.com/c31widusbackup.
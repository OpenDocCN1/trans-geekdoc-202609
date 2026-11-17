# Backups Versus Redundancy

Redundancy, or fault-tolerance options, provides for alternate resources if a primary resource fails. In other words, a system can experience a fault but tolerate it and keep operating. However, you must know that redundancies are not replacements for backups.

For example, RAID 1 mirroring writes data to two disks instead of one. Should one disk fail, the system can continue to operate. The data are still available on the second disk. However, imagine that you have a server protected with RAID. If a catastrophic failure in the server destroys all the drives, the data are gone. If you don’t have a backup, the data are gone forever.

Similarly, you can set up clustered servers so that standby servers take over if the primary server fails. Again, though, just because a service is using a cluster for fault tolerance, you still need backups.

+   • **Differential backup**—With this type of backup, you start by making a full backup, perhaps on Sunday, when network traffic is lightest. On Monday through Saturday, you back up changes made since Sunday’s full backup on a daily basis. As the week progresses, each night’s backup (the differential) takes a little longer.

+   • **Incremental backup**—Again, you start with a full backup when network traffic is light. Then, each night, you back up only that day’s changes. As the week progresses, the nightly (incremental) backup takes about the same amount of time.

It is faster to create the incremental weekday backups than the differential backups. This comes at a price, however. If you need to use the backup images to restore data, systems using differential backups would need to restore only the full backup and then the latest differential. Those using incremental backups would need to restore the full backup and then each day’s incremental backups to complete the restore.

You should back up items other than just data. These include router, switch, and other network device configurations, user access permissions and configurations (e.g., Active Directory), and server/workstation operating systems and configurations. To make this more manageable, most large companies have a standard base configuration for workstations that can be reloaded on demand. As long as you keep these up to date (patched and fixed), this is an attractive solution.

# Incident Handling

As a reminder, an incident is an event that results in an actual or threatened violation of security policy. When an incident occurs, an organization needs to respond. The incident-handling process includes the following steps:

+   • Preparation
+   • Identification
+   • Notification

# TIP

Remember that minimizing downtime is often about avoiding downtime. Often the simplest way to avoid downtime is to ensure that all computers and devices are patched with the latest security fixes. Patching makes your systems more resistant to many types of attacks and less reliant on redundancy and other fault-tolerance techniques.
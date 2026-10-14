# Figure 9-3 Shadow Copies in Windows Server 2019

![](bbox=[0.11, 0.11, 0.42, 0.47])

# Figure 9-4 Recoverable Versions of My Documents Folder Using Shadow Copies

![](bbox=[0.48, 0.11, 0.81, 0.47])

# Full versus Incremental Backups

In file/directory data backup, full backups, which record all the data on the computer, can take a long time. Consequently, most companies do a full backup only once a week or so. They also do daily incremental backups, which only save the data changed since the most recent backup (either full or incremental). For instance, if the full backup takes place on Sunday, Monday’s incremental backup will only save information changed since Sunday’s full backup. Tuesday’s backup, in turn, will only save data changed since Monday’s incremental backup. Wednesday’s incremental backup will save data changed since Tuesday’s incremental backup. On the following Sunday, a full backup will be done again.

> Full backups record all of the data on the computer. Incremental backups only save the data changed since the most recent backup (either full or incremental).

The advantage of doing periodic full backups and then more frequent incremental backups is simply that incremental backups take less time to do. For large hard drives with many data directories, daily backup speed is very important. Therefore, almost all companies mix full and incremental backups.

However, with incremental backups, restoration must be done carefully. In the example discussed earlier, suppose that the hard drive fails on a Wednesday. The restorer must first restore Sunday’s full backup, then Monday’s incremental backup, and then Tuesday’s incremental backup. In other words, backups must be restored in the order in which they were created. Otherwise, newer files may be overwritten by older files.
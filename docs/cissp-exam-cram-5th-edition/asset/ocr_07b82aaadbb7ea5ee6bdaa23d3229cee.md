Software itself can be vulnerable, even when good backup policies are followed, because sometimes software vendors go out of business or no longer support needed applications. In these instances, _escrow agreements_ can help. Escrow agreements allow an organization to obtain access to the source code of business-critical software if the software vendor goes bankrupt or otherwise fails to perform as required. Given the myriad compilers and operating systems, source code escrow agreements now address everything required to build a product, including operating systems, tools, and compilers.

Each backup method has benefits and drawbacks. Full backups are the most comprehensive but take the longest time to create. So, even though it might seem best to do a full backup every day, it might not be possible due to the time and expense.

**Tip**

Two basic methods can be used to back up data: automated and on-demand backups. Automated backups are scheduled to occur at a predetermined time. On-demand backups can be scheduled at any time.

# Full Backups

During a full backup, all data is backed up, and no files are skipped or bypassed; you simply designate which server to back up. A full backup takes the longest to perform and the least time to restore because only one backup data set is required.

# Differential Backups

With a differential backup, a full backup is typically done once a week, and a differential backup, which involves backing up all files that have changed since the last full backup, is done more frequently, typically daily. If you need to restore, you need the last full backup and the most recent differential backup.
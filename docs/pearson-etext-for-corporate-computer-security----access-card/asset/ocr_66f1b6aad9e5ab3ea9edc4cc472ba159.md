+   **Full Backups**
+   All files and directories
+   Slow, so it is typically done weekly
+   **Incremental Backups**
+   Only records changes since the last backup
+   Fast, so usually done daily
+   Do incremental backups until the next full backup
+   **Restoration Order**
+   Restore the full backup first
+   Then restore incremental backups in the order created
+   (Otherwise, newer files will be overwritten)
+   **Generations**
+   Save several generations of full backups
+   Usually do not save incremental backups after the next full backup

# Figure 9-6 Full versus Incremental Backup (Study Figure)

**CENTRALIZED BACKUP** To avoid these problems, many firms use **centralized backup**. As Figure 9-8 shows, backup is done over the network, from a central **backup console**. This console usually is a PC. The central backup console has magnetic tape or other storage hardware.

+   **Local Backup**
+   On individual computers
+   No way to enforce backup policies
+   Difficult to audit backup compliance
+   **Centralized Backup**
+   Central backup console collects data from each device over the network
+   Stores on console's backup hardware
+   It is economical to use expensive backup hardware on a single console compared to giving each host a backup device
+   Easy to audit compliance
+   Generally results in a well-maintained repository of backup media
+   **Continuous Data Protection (CDP)**
+   Used when a firm has two server locations
+   Each location backs up the other in real time
+   Other site can take over very quickly in case of a disaster, with little data loss
+   Requires expensive high-speed transmission link between the sites
+   **Internet Backup Services**
+   Backup to a commercial backup service's site, over the Internet
+   Convenient but very slow
+   Lose security over data
+   **Mesh Backup**
+   Peer-to-peer backup onto other client computers
+   Sends backup data in parcels to many other client PCs
+   Stores data redundantly so if a PC is off-line, all data are still available
+   Security must be considered carefully

# Figure 9-7 Backup Technologies (Study Figure)
# NETWORK DEVICE BACKUP/RESTORE

Backups are an essential fault tolerance element of any network, whatever the size. The type of backup medium for a network depends on the amount of data that needs protection and the amount of time available to perform the backups.

The traditional medium for backups is magnetic tape, but tape backups are slow, and the technology up hard disks is increasingly popular because it is faster and provides random access to files without searching through a tape. Cloud backups provide an offsite data storage solution, which might or not be practical depending on the amount of data involved and the speed of the network's connection.

While backups are important, a high availability plan should also include backups of device configurations and states. In a disaster recovery situation, servers, routers, switches, and other devices must be installed and configured before any data is restored. This can be a lengthy process that extends the time needed to restore the network to its full functionality.

The configuration of a device can often be saved as a simple text file in the case of a router or switch. Many router and switch include some mechanism for backing up the configuration file to a server or removable storage device. Without this file, administrators replacing the switch might have to reconfigure each port individually.

In the case of a server, network backups can preserve the data, but replacing the server in the event of a disaster by restoring the data from a backup can be problematic. The data, as preserved in the backup, expects the server to have a specific hardware configuration, which might not be exactly the same in a replacement computer. For this reason, many backup products are able to back up the full system state, which makes it possible to perform a complete restoration without having to reinstall and reconfigure the operating system and the applications.

# CERMIKE EXAM ESSENTIALS

+   High availability extends into the data center infrastructure, which must include a properly conditioned power supply, HVAC environmental support, and adequate fire suppression capabilities.
Redundant systems can typically operate in an active-active mode, in which both devices are always operating and balancing the load, or an active-passive mode, in which one device operates while the other remains in a standby state until needed.
Redundant data centers can exist in different states, depending on the organization's operational requirements and budget. Hot sites are ready for use in minutes, warm sites in days, and cold sites in weeks or months.
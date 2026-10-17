

# 备份策略与存储方案

## 恢复处理能力的前提

To recover an organization’s processing capabilities, the organization must ensure that its data is backed up prior to any adverse event that requires data restoration. There are several backup storage strategies an organization can use; the decision regarding which one (or combination of several) to use depends on a few factors, including

• How much data the organization can afford to lose in the event of a disaster

• How much data the organization requires to restore its processing capability to an acceptable level

• How fast the organization requires the data to be restored

• How much the backup method or system and media cost

• How efficient the organization’s network and Internet connections are in terms of speed and bandwidth

In the next few sections we will discuss various backup strategies that vary in cost, speed, recoverability, and efficiency.

## 传统备份策略

Traditional backup strategies involve backing up individual servers to a tape array or even to separate disk arrays. Because these backup methods are often expensive and time consuming, a system of using backup strategies such as full, incremental, and differential backups was developed to deal with these issues. Briefly, the strategies are executed as follows:

• **Full backup** The entire hard disk of a system is backed up, including its operating systems, applications, and data files. This type of backup typically takes a much longer amount of time and requires a great deal of storage space.

• **Incremental backup** This strategy backs up only the amount of data that has changed since the last full backup. It requires less storage space and is somewhat faster, but the data restore time can take much longer. The last full backup and each incremental backup since the last full backup have to be restored one at a time, in the order in which they occurred. Incremental backups reset the archive bit on a backup file, showing that the data has been backed up. If the archive bit is set to “on,” as happens when a file changes, this means it has not been backed up.

• **Differential backup** This backup strategy involves backing up only data that has changed since the last full or incremental backup; the difference between this type of backup and an incremental backup is that the archive bit for the backup files is *not* turned off. In the event of a restore, only the last full backup and the last differential backup have to be restored, since each subsequent differential backup includes all the previous changed data. However, as differential backups are run, they became larger and larger, since they include all data that has changed since the last full backup.

Again, these strategies were devised during the days when backup solutions were highly expensive, backup media was slow and unreliable, and backups were very time-consuming and tedious. Although there are still some valid uses of these strategies today, they have largely become obsolete due to the much lower cost of other backup media, high-speed networking, and both the availability and inexpensive nature of technologies such as cloud storage, all of which are discussed in the following sections.

## 直接连接存储

Direct-attached storage is the simplest form of backup. It also may be the least dependable, since it is an external storage media, such as a large-capacity USB drive, directly attached to the computing system. While direct-attached storage may be fast enough for the organization’s current requirements, it is unreliable in that a physical disaster that damages a system may also damage the attached storage. This type of storage is also susceptible to accidents, intentional damage, and theft. Direct-attached storage should never be used as the only form of backup for critical or sensitive data, but it may be effective as a secondary means of backup for individual user workstations or small datasets.

## 网络连接存储

A network-attached storage (NAS) system is the next step up from direct-attached storage. It is simply a network-enabled storage device that is accessible to network hosts. It may be managed by a dedicated backup server running enterprise-level backup software. It may also double as a file server. Over a high-speed network, NAS can be quite efficient, but suffers from some of the same reliability issues as direct-attached storage. Any disaster that occurs causing damage to the infrastructure may also damage the NAS system. NAS may be sufficient for small to medium-sized businesses and may or may not offer any redundancy capabilities.

## 存储区域网络

A storage area network (SAN) is larger and more robust than a simple network-attached storage device. A SAN is designed to be a significant component of a mature data center supporting large organizations. It may have its own cluster of management servers and even security devices to protect it. A SAN is often built for redundancy by having multiple storage devices that fail over to each other. Components are connected to each other and to the rest of the network with high-speed fiber connections. While designed for high availability and efficiency, a SAN still suffers from the possibility that a catastrophic event damaging the facility can also damage the SAN.

## 云存储

Cloud-based storage is becoming more of the norm than on-premises storage. While on-premises storage is still necessary for short-term or smaller-level data recovery, the remote storage capabilities of the cloud support large-scale data recovery that is fast and reliable. Even if a facility is entirely destroyed, data that is backed up over high-speed Internet connections to the cloud is easily available for restoration. The only limiting factors an organization may face when using cloud-based storage as a disaster recovery solution are the associated costs of cloud storage space, which may increase if the amount of data increases over time, as well as the availability of high-speed bandwidth from the organization to the cloud provider.

## 离线存储

*Offline storage* simply means that data is backed up and stored off of the network and/or at a remote location away from the physical facility. The methods for creating and using offline storage may be manual or electronic; even cloud-based storage is considered offline since it is not part of the same organizational infrastructure and is not housed in the same physical facility. Traditionally, organizations manually transported backup media, such as tapes, optical discs, and hard drive arrays, to a geographically separated site so that if a disaster damaged or destroyed the primary processing facility, the backup media would still be available. Another benefit of offline storage is that a malware infection, ransomware, or other malicious attack that impacts the primary processing facility is far less likely to impact the offline storage.

## 电子备份与远程日志

Contrary to traditional thinking, backups don’t always have to be on a full, incremental, or differential basis. Backups can also be performed on individual files and even individual transactions. They can also be captured electronically either on a very frequent basis or in real time. *Electronic vaulting* is a backup method where entire data files are transmitted in batch mode (possibly several at a time). This may happen two or three times a day or only during off-peak hours, for instance. Contrast this to *remote journaling*, which only sends changes to files, sometimes in the form of individual transactions, in either near or actual real time.

Both methods require a stable, consistent, and sometimes high-bandwidth network or Internet connection, depending on if the backup mechanism is local within the network or located at a geographically separated site.

![Images](exam.jpg)


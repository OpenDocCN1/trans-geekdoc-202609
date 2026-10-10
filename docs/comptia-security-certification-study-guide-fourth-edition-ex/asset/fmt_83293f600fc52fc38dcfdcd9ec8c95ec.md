
# Warm site

A **warm site** occupies the middle ground between a hot site and a cold site. It is an alternative location with office space and spare networking equipment such as a server and backup devices so that you can quickly restore your organization’s network in an emergency.

![Image](exam.jpg)

> **Be sure to know the difference between hot, warm, and cold alternative site locations for the Security+ exam. Also note that these sites could be rented from a third party, or they could be sites owned by your company.**

Not only do you need to understand that there are hot, warm, and cold alternative sites for the Security+ exam, but you also should understand the two major types of these sites:

## Exclusive site

With an **exclusive site**, your company pays the full fee to have the site available when needed, and the site is dedicated to your company. It is critical that you ensure the provider is not offering the site to anyone else in case you both need it at the same time.

## Time-shared

With a **shared alternative site**, you decide to split the cost of an alternative site with another business, and if either company needs the site, it is there to be used. The problem with a shared alternative site is that you need to ensure the site can handle both businesses in case you both need it at the same time.

![Image](exam.jpg)

> **Remember that if a company expects a system to be available 30 minutes after a failure, that is the RTO. However, if they expect the data restored to the point of failure, that is the RPO.**

# INSIDE THE EXAM

## BCP and DRP Terminology

For the Security+ certification exam, it is critical that you understand `BCP` and `DRP` concepts such as business impact analysis, alternative sites, and having a functional recovery plan, but the Security+ certification exam also expects you to know a few other terms related to business impact assessment:

- **Succession planning** is the process of ensuring that you have employees within the organization who can fill key leadership roles to ensure that the business can continue if you lose key personnel.
- **IT contingency planning** is the preparation of a recovery plan for when something goes wrong with the IT systems and infrastructure.
- **Mean time to repair (MTTR)**, also known as mean time to recovery, is the average time for a system or device to recover from a failure.
- **Mean time between failures (MTBF)** is the amount of time between failures of a system or device.
- **Mean time to failure (MTTF)** is the amount of time a device is expected to last in production before it fails. `MTTF` is usually a value reported by the manufacturer on hardware, which you can use as evaluation criteria when selecting hardware. The difference between `MTBF` and `MTTF` is that a device such as a RAID array may have a `MTBF` that indicates how frequently you can expect the RAID array to fail, but due to the redundancy you most likely will not lose data (it is considered repairable). The `MTTF` is a rating typically on hardware such as hard drives and is a time specified that the drive may fail. This failure is permanent and unrecoverable, so you put the drive in the RAID array, which is a recoverable/repairable technology.
- **Recovery time objective (RTO)** is a `BCP` term for the amount of time allowable before a business function must be restored to a functional state after a failure.
- **Recovery point objective (RPO)** is a `BCP` term to represent how much of a system is expected to be recovered. For example, your company may expect that when a system fails, you should be able to restore up to the point of failure, whereas another company may only expect recovery of data up to 24 hours prior to the point of failure.

You are sure to get some questions on `RPO`, `RTO`, `MTTR`, `MTTF`, and `MTBF` on the Security+ exam, so know those terms well.

# CERTIFICATION OBJECTIVE 18.02

# Backing Up and Restoring Data: Backup Concepts

A critical task to help maintain the network and to ensure that users have access to their data is to regularly back up data on the network to another location. You can back up the data to tape drives, a backup file on another server, or to the cloud. A common backup strategy is to back up the data to a file on a hard disk and then later back that file up to tape. The reason this is common is that backing up to tape is much slower than backing up to disk, so you want to ensure the backup that is backing up files that users are using is as quick as possible. Cloud backup means your data is stored on the cloud provider’s storage hardware. As mentioned in [Chapter 17](#ch17.xhtml#ch17), storing data in the cloud may not be acceptable for some businesses due to privacy concerns or regulations.

## Backup Destination Media

Before discussing the different types of backups, it is important to note the different types of media, or backup destinations for a backup operation. The following outlines the different destinations you can have a backup sent to:

- **Tape** For years, servers contained tape drives that would be used to store the backed up data. The benefit of storing on tape was that you had the flexibility to back up lots of data and then decide where you wanted to store the tapes.
- **Disk** Many companies today are backing up to drives instead of tapes. Backing up to disk is typically faster than backing up to tape, and you can even use removable drives in order to store the backup at a different location. In this scenario the backup software may back up to “virtual tapes,” which are files on a disk on `NAS` or a `SAN`.
- **Network-attached storage (NAS)** `NAS` is an enclosure that contains multiple hard drives, and typically one or two Ethernet ports to connect the `NAS` device to the regular network. If you have a `NAS` device available, you can easily back up the data across the network to it.
- **Storage area network (SAN)** A `SAN` is a high-speed network designed for storage traffic that connects your servers to a storage array of drives. You can use the `SAN` as a backup destination similar to `NAS`, but with faster access to the storage.
- **Cloud** If you want to back up offsite, you could look to backing up to the cloud as a backup destination. The benefit of backing up to the cloud is you get high availability of the storage located in the cloud.
- **Image** You can back up an entire image of a system. For example, in Windows 10, the backup software has an option to do a full system backup, which backs up the entire system to an image. You can restore the system by restoring the system image.
- **Online vs. offline** When looking at your backup destinations, you should consider whether you want a backup destination to be available online or offline. *Online* means you have access to it at all times, whereas *offline* means the backup destination is not available at all times and is typically located offsite somewhere.

## Security Considerations with Tapes

Before we dive into the different backup types, it is important to understand some of the security considerations regarding the tapes or the backup destination:

- **Tape rotation** Be sure to create a rotation cycle for your tapes so that you can send a copy of the data offsite for use in case of a site disaster such as a fire. Tapes should go offsite as soon as possible after a backup, and old tapes should cycle back to onsite. For example, last night’s tapes leave at the end of the day, and tapes that are one week or one month old are returned back onsite to be used within the rotation. Remember to test restore operations occasionally, as an overused tape may be unreliable when you go to restore data from it.

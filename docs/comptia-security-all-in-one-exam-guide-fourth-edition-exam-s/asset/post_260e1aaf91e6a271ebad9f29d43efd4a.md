
environments, regulatory issues may prescribe a specific frequency and retention period, so it is important to know these requirements when determining how often you will create a backup and how long you will keep it.

If you are not in an environment for which regulatory issues dictate the frequency and retention for backups, your goal will be to optimize the frequency. In determining the optimal backup frequency, two major costs need to be considered: the cost of the backup strategy you choose and the cost of recovery if you do not implement this backup strategy (if no backups were created). You must also factor into the equation the probability that the backup will be needed on any given day.

When calculating the cost of the backup strategy, consider the following elements:

- The cost of the backup media required for a single backup
- The storage costs for the backup media and the retention policy
- The labor costs associated with performing a single backup
- The frequency with which backups are created

All these considerations can be used to arrive at an annual cost for implementing your chosen backup strategy, and this figure can then be used as previously described.

Related to the location of backup storage is where the restoration services will be located. If the organization has suffered physical damage to its facility, having offsite data storage is only part of the solution. This data will need to be processed somewhere, which means that computing facilities similar to those used in normal operations are required. This problem can be approached in a number of ways, including hot sites, warm sites, and cold sites.

## Cold Site

A cold site will have the basic environmental controls necessary to operate but few of the computing components necessary for processing. Getting a cold site operational may take weeks.

## Hot Site

A hot site is a fully configured environment, similar to the normal operating environment, that can be operational immediately or within a few hours depending on its configuration and the needs of the organization.

## Warm Site

A warm site is partially configured, usually having the peripherals and software but perhaps not the more expensive main processing computer. It is designed to be operational within a few days.

![](img/922567202a944c5e8d3ba016d2ad3a5_168_0.png)

> **EXAM TIP**  Alternate sites are highly tested on the CompTIA Security+ exam. It is also important to know whether the data is available or not at each location. For example, a hot site has duplicate data or a near-ready backup of the original site. A cold site has no current or backup copies of the original site data. A warm site has backups, but they are typically several days or weeks old.

## Chapter Review

In this chapter, you became acquainted with the principles of risk mitigation strategies. The chapter first presented the concepts of change management, incident management, user rights and permissions, and routine audits. It then covered the use of security controls to prevent data loss or theft, including technical solutions such as DLP.

Next you were introduced to the topic of business continuity and the critical elements associated with accomplishing this activity. Fault tolerance and high availability concepts were covered, followed by the use of policies and procedures to enable disaster recovery, including backup strategies. The chapter closed with an examination of alternate sites and their capabilities.

## Questions

To help you prepare further for the CompTIA Security+ exam, and to test your level of preparedness, answer the following questions and then check your answers against the correct answers at the end of the chapter.

1. Which of the following is not a type of backup?
A. Incremental
B. Partial
C. Differential
D. Delta

2. To achieve reliability and speed improvements through the use of RAID, which form would you use?
A. RAID 0
B. RAID 1
C. RAID 5
D. RAID 10

3. Which of the following defines differential backup?
A. Only the files and software that have changed since the last full backup are backed up.
B. All files and software are copied to storage media.
C. Only the files and software that have changed since the last full or incremental backup are backed up.
D. Only portions of files changed are backed up.

4. Which of the following describes a warm site?
A. A fully configured environment that can be operational immediately or within a few hours
B. A reciprocal site where similar organizations agree to assume processing for the other party should a disaster occur
C. A site with basic environmental controls but few of the computing components necessary
D. A partially configured site designed to be operational within a few days

5. What is the purpose of high availability?
A. Distributing processing load over two or more systems
B. Providing the ability to maintain availability of data and operational processing despite a disrupting event
C. Mirroring of data and systems to avoid interruption in service to the user
D. Linking a group of systems to work together and function as a single system

6. Which of the following can be a single point of failure?
A. High availability
B. Load balancing
C. A cluster
D. A process

7. Which of the following accurately describes IT contingency planning?
A. One of the most important aspects of business continuity planning
B. Details related to the long-term recovery of the organization
C. Used to ensure that company operations continue in the face of whatever event has occurred
D. Focused on recovery and rebuilding of the organization after a disaster has occurred

8. Which of the following defines RAID 1?
A. Spreads data out to increase the speed of data access
B. Spreads data across disks and adds parity
C. Stripes data at the bit level
D. An exact copy so that all data is mirrored on another drive

9. What is the correct description of a Computer Incident Response Team (CIRT)?
A. Exercises that provide the opportunity for all parties to practice incident response procedures
B. Personnel, processes, and plans to handle business interruptions
C. A team test to identify planning flaws before an actual incident occurs
D. A checklist walkthrough used to ensure all team members understand their role in a DRP

## Answers

## PART II

- 1. B. Full, incremental, differential, and delta are types of backups.
- 2. C. RAID 5 offers both performance and reliability increases.
- 3. A. A differential backup copies all files and software that have changed since the last full backup.
- 4. D. A warm site is a partially configured site designed to be operational within a few days.
- 5. B. High availability refers to the ability to maintain availability of data and operational processing despite a disrupting event.
- 6. D. A single point of failure can be a special piece of hardware, a process, a specific piece of data, or an essential utility.
- 7. A. Because most organizations rely heavily on computing resources, IT contingency planning is one of the most important aspects of business continuity planning.
- 8. D. RAID 1 implements exact copies of disks so that all data is mirrored on another drive, providing complete redundancy.
- 9. B. A Computer Incident Response Team (CIRT) is personnel, processes, and plans to handle business interruptions.
- 10. A. Change management ensures proper procedures are followed when modifying the IT infrastructure.
- 11. First identify all critical functions, and then answer the following questions:
  - Who is responsible for the operation of this function?
  - What do these individuals need to perform that function?
  - When should this function be accomplished relative to other functions?
  - Where will this function be performed?
  - How is this function performed (what is the process)?
  - Why is this function so important or critical to the organization?
- 12. The focus of business continuity planning is on continued operation of a business, albeit at a reduced level or through different means during some period of time. Disaster recovery planning is focused specifically on recovering from a disaster.
- 13. D. The cost of not having backups is (probability the backup is needed) × (cost of restoring with no backup). 20% × $100,000 = $20,000.

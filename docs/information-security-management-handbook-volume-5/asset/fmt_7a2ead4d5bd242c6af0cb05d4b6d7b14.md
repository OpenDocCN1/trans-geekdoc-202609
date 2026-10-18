
![](OEBPS/images/box.jpg) Are any pieces of software customized or can the enterprise use CD-ROM media for software (not data) recovery?

![](OEBPS/images/box.jpg) How much will the information grow over the next three to five years for determining storage capacity and budget planning?

![](OEBPS/images/box.jpg) What is our backup scheduling and archiving? Daily differentials or incrementals and a weekly full backup? Grandfather, father, son tape rotations?

![](OEBPS/images/box.jpg) What does the enterprise want to do about remote locations?

![](OEBPS/images/box.jpg) Does the enterprise also want the desktops and laptops backed up?

![](OEBPS/images/box.jpg) Can the backups run unattended to reduce administrative costs? If so, how will the tapes be taken off-site?

![](OEBPS/images/box.jpg) What is the rotation and capacity of the off-site tape storage facility?

![](OEBPS/images/box.jpg) What is the tape return time from the off-site tape storage facility?

The enterprise has implemented a tape backup system, selected an off-site tape storage supplier, ordered the backup and replacement tapes, and is ready to start developing the formal processes for information backup and recovery. The following are the topics that should be required for documenting the information backup and recovery:

![](OEBPS/images/box.jpg) Who is responsible for the information backups and restores?

![](OEBPS/images/box.jpg) Who has the authority to request an information backup or restore?

![](OEBPS/images/box.jpg) What is the step-by-step process for the information backup and restore?

![](OEBPS/images/box.jpg) Per regulatory requirements, does the enterprise have to encrypt all or some of the backed up information on the tape?

![](OEBPS/images/box.jpg) Are we going to compress the data on tapes to store more information per tape?

![](OEBPS/images/box.jpg) Is the server environment virtualized? If so, besides the virtual servers, will the underlying operating system or applications be backed up?

![](OEBPS/images/box.jpg) What is the tape retention standard for the information backed up and who owns the information that is backed up?

![](OEBPS/images/box.jpg) What happens when an information backup or restore fails or is successful?

![](OEBPS/images/box.jpg) How are the information backups and restores monitored and tracked?

![](OEBPS/images/box.jpg) Which databases are backed up—production, test, development, human resources, manufacturing, and/or finance?

![](OEBPS/images/box.jpg) Are database backups handled differently from regular file backups, e.g., are databases backed up to a flat file and the flat file backed up to tape?

![](OEBPS/images/box.jpg) Are the database schemas backed up with the database data or separately?

![](OEBPS/images/box.jpg) How do users back up their assigned desktop or laptop systems?

The enterprise has defined the above topics into standards, practices, guidelines, and procedures, but how do they validate that the backup tapes are still valid? If the enterprise has a business continuity and disaster recovery plan, then the backup tapes are tested on a regular basis. But what happens if the enterprise has not put the time, staff, and money into an enterprise business continuity and disaster recovery plan? The following are standards and procedures that can be put into place in the enterprise environment to validate that backup tapes contain valid and good information:

![](OEBPS/images/box.jpg) Ensure backups are successful and checked on a daily basis.

![](OEBPS/images/box.jpg) Document the criteria for a successful or failed back up. For example, on a full backup, if less than 20 files failed to back up, then the backup is successful, or on a full backup, if one database fails to backup, then the backup has failed.

![](OEBPS/images/box.jpg) If incremental backups fail the first day, then do not rerun.

![](OEBPS/images/box.jpg) If incremental backups fail two days in a row, then correct, rerun, and validate they are successful.

![](OEBPS/images/box.jpg) If the weekly backups fail, then correct, rerun, and validate they are successful.

![](OEBPS/images/box.jpg) As backup tapes come back onsite on a quarterly basis, perform a full system restore on a system or two that contain mission critical data, such as a financial or payroll system.

Then as the enterprise develops the business continuity and disaster recovery plans, the enterprise will want to include these tips when performing a test or performing a live disaster recovery:

![](OEBPS/images/box.jpg) Does the disaster recovery site have the hardware and software that matches your backups and backup tapes?

![](OEBPS/images/box.jpg) If the disaster recovery site has the tape hardware, does the enterprise disaster recovery plan contain a set of the tape backup software?

![](OEBPS/images/box.jpg) Does the disaster recovery plan include a copy of the procedures for system and information recovery?

![](OEBPS/images/box.jpg) Consider taking two sets of backup tapes to the event, just in case the primary set of tapes are corrupt.

![](OEBPS/images/box.jpg) Consider taking one set of tapes on one mode of transportation and another set of tapes on another mode of transportation to the disaster recovery site.

While many of the above considerations are geared toward tape backups, the same considerations can also be used for other backup media. The table below represents a sample table backup plan template.

| Purpose | The purpose of the backup plan is to establish and implement procedures to create and maintain retrievable exact copies of electronic information and related technology components that are necessary for recovery activities. This document will define the following standards for organization backup processing: to provide a standard operating procedure for backup of organization data; to provide a standard for labeling backup media; to provide a standard for data retention; to provide a standard for off-site storage and retrieval of backup media; the data backup plan enables the organization to meet the availability requirements for regulatory compliance |

| --- | --- |

| Table of contents | Confidentiality statement and compliancePlan maintenance (change history)IntroductionPurposeScopeResponsibilitiesData backup requirementsProceduresBackup processingDaily incremental backupsWeekly full backupsMonthly full backupsQuarter-end full backupsFailed backupsRestoration processingRequest for restoreAuthorization for restoreTesting for successful restoreFailed restorationBackup tape testingQuarterlyRegulatoryRegular validationsAnnual: off-site contractsAnnual: software maintenance renewalsAnnual: hardware maintenance renewalsQuarterly: tape access authorizationsQuarterly: tape inventoryTapesScheduling backup media rotationSending tapes off-siteRecalling tapes back onsiteTape labelingRetention cycleTape drive cleaningContactsBackup software supplierBackup hardware supplierOff-site storage supplierAuthorized staff to recall and send tapesAppendix (forms/logs/schedules)Tape labeling logData backup scheduleBackup job logTape cleaning log |

If an enterprise cannot completely implement business continuity and disaster recovery plans, strong backup controls need to be part of every enterprise environment. Without strong backup controls, an enterprise may not know that backups and backup media are good and can be used to recover operational data. In the future, the enterprise may also want to consider moving to remote backups off-site as a service.

# About the Author


a disaster. Other examples include fire, earthquake, the telecom provider being down, a labor strike affecting shipping to and from your business, and a hacker deleting critical files. Any event that can significantly disrupt an organization’s operations is a disaster.

## Disaster Recovery Plan

A disaster recovery plan (DRP) is a plan you have in place to return business to normal operations after a disaster occurs. A DRP must include a number of items. It must address personnel issues, including being able to find temporary personnel, if needed, and being able to contact the personnel you have employed. It also includes having specific people assigned to specific tasks. Your DRP needs to address who in your organization is tasked with the following:

- Locating alternative facilities
- Getting equipment to those facilities
- Installing and configuring software
- Setting up the network at the new facility
- Contacting staff, vendors, and customers

These are just a few areas that a disaster recovery plan must address.

## Business Continuity Plan

A business continuity plan (BCP) is similar to a DRP but with a different focus. A DRP is designed to get the organization back to full functionality as quickly as possible. A BCP is designed to get minimal business functions back up and running at least at some level so you can conduct some type of business. An example would be a retail store whose credit card processing system is down. Disaster recovery is concerned with getting the system back up and running, and business continuity is concerned with simply getting a temporary solution, such as processing credit cards manually.

To successfully formulate a BCP, you must consider those systems that are most critical for your business and have an alternative plan in case those systems are down. The alternative plan need not be perfect, just functional.

## Impact Analysis

Before you can create a realistic DRP or BCP, you have to do an impact analysis of what damage to your organization a given disaster might cause. This is called a business impact analysis or business impact assessment (BIA). Consider a web server crash. If your organization is an e-commerce business, then a web server crash is a very serious disaster. However, if your business is an accounting firm and the website is just a way for new customers to find you, then a web server crash is less critical; you can still do business and earn revenue while the web server is down. You should make a spreadsheet of various likely or plausible disasters and do a basic BIA for each.

One item to consider for a BIA is the maximum tolerable downtime (MTD). How long can a given system be down before the effect is catastrophic and the business is unlikely to recover? Another item to consider is the mean time to repair (MTTR). How long is it likely to take to repair a given system if it is down? These factors help you determine the business impact of a given disaster.

## Disaster Recovery and Business Continuity Standards

Several standards might be useful to you in forming a BCP and a DRP. Familiarizing yourself with existing standards can aid you in forming your own DRP and BCP:

- ISO 27035: This standard is about incident response. It requires a structured, planned approach to detecting and reporting incidents, as well as responding.
- NIST 800-61: This standard is concerned with establishing incident response policies. It provides guidance on incident response teams, response procedures, and related items.

Both of these are good, general disaster recovery standards. Either can provide a basis for your own disaster recovery planning.

## Fault Tolerance

The fact is that at some point, all equipment fails. So fault tolerance is important. At the most basic level, fault tolerance for a server means a backup. If the server fails, did you back up the data so you can restore it? While database administrators may use a number of different types of data backups, from a security point of view, there are three primary backup types to be concerned with:

- Full: All data
- Differential: All changes since last full backup
- Incremental: All changes since last backup of any type

Consider a scenario in which you do a full backup at 2 a.m. each morning. But you are concerned about the possibility of a server crash before the next full backup, so you want to do a backup every 2 hours. Well, the type of backup you choose will determine the efficiency of doing those frequent backups and the time needed to restore. So let's consider each scenario and what would happen if the system crashed at 10:05 a.m.:

- Full: Say that you do full backups at 4 a.m., 6 a.m., ..., 10 a.m., and then the system crashes. Well, to restore, you just have to restore the last full backup, which was done at 10 a.m. This makes restoration much simpler. However, running a full backup every 2 hours is very time-consuming and resource intensive, and it will have a significant negative impact on your server's performance.
- Differential: Say that you do differential backups at 4 a.m., 6 a.m., ..., 10 a.m., and then the system crashes. To restore, you will need to restore the last full backup, which was done at 2 a.m., and the most recent differential backup, which was done at 10 a.m. This is just a little more complicated than the full backup strategy. However, those differential backups are

information is interspersed across the drive array. The storage capacity of the array is a function of the number of drives minus the space needed to store parity.

- RAID 6 (striped disks with dual parity): RAID 6 combines four or more disks in a way that protects data against loss of any two disks.
- RAID 1+0 (or 10): RAID 1+0 is a mirrored data set (RAID 1) that is then striped (RAID 0), hence the “1+0” name. A RAID 1+0 array requires a minimum of four drives: two mirrored drives to hold half of the striped data, plus another two mirrored for the other half of the data.

A server without at least RAID 1 is gross negligence on the part of the network administrator. RAID 5 is actually very popular with servers.

While RAID and backup strategies are the fundamental issues of fault tolerance, any backup system provides additional fault tolerance. This can include uninterruptible power supplies, backup generators, and redundant Internet connections.

## Important Laws

There are a number of computer laws in various countries, states, and provinces. It is important to be familiar with the laws that are relevant to your jurisdiction. However, there are a few laws that are most critical in the United States. We will discuss each of them here.

### HIPAA

The Health Insurance Portability and Accountability Act (HIPAA) is a regulation that mandates national standards and procedures for the storage, use, and transmission of personal medical information. Passed into law in 1996, HIPAA has caused a great deal of change in healthcare record keeping.

HIPAA covers three areas—confidentiality, privacy, and security of patient records—and was implemented in phases to ease the transition. Confidentiality and privacy of patient records had to be implemented by a set date, followed by security of patient records. Standards for transaction codes in medical record transmissions had to be completed by a given date as well.

The penalties for HIPAA violations are very stiff: They can be as high as $250,000, depending on the circumstances. A medical practice is required to appoint a security officer. All related parties, such as billing agencies and medical records storage facilities, are required to comply with these regulations.

### Sarbanes-Oxley

The Sarbanes-Oxley Act is legislation that came into force in 2002, introducing major changes to the regulation of financial practice and corporate governance. Named after Senator Paul Sarbanes and Representative Michael Oxley, this law is designed to make publicly traded corporations more accountable.

The legislation focuses primarily on financial issues, but it also affects the IT departments whose job it is to store a corporation's electronic records. The Sarbanes-Oxley Act states that all business records, including electronic records and electronic messages, must be saved for “not less than five years.” The consequences for noncompliance are fines, imprisonment, or both.

### Payment Card Industry Data Security Standards

While not a law, the Payment Card Industry Data Security Standards (PCI DSS) are certainly something any IT security professional who works for a company that handles credit cards and debit cards should be familiar with. PCI DSS is a proprietary information security standard for organizations that handle branded credit cards from the major companies, including Visa, MasterCard, American Express, and Discover.

## Summary

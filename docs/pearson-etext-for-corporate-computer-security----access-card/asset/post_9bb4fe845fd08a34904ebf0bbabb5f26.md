
and air-conditioning), hardware, installed software, and up-to-date data. As soon as people can move in, the hot site can take over the full operation of the damaged site. With a skeleton crew, basic operation can begin even earlier.

Hot sites are attractive when processes have little downtime tolerance. They can be back in operation rapidly, and there rarely are the major delays that can occur when software is difficult to install on the computers used in other types of backup facilities. However, hot sites also are extremely expensive, and ensuring that the software at the backup site is configured in the same way as the original software is difficult.

## COLD SITES

Cold sites, in turn, offer physical facilities, electrical power, and HVAC, but they are empty rooms with connections to the outside world. To use a cold site, the company has to procure, bring in, and set up hardware; install software; and mount data. By the time all of this happens, the company could be bankrupt. Cold sites are less expensive than hot sites, but companies must assess realistically how useful they would be in practice.

## CLOUD-BASED HOSTING

Although hot sites are attractive, they are expensive to keep open and require time to become operational. A more cost-effective option is to store data with a cloud-based provider. Over the past decade most companies have moved their data and applications to a cloud-based provider as a cost-savings measure. The cost savings of cloud-based hosting relative to running a traditional data center are substantial.

In fact, most people don’t realize how quickly organizations have shifted to the cloud. Amazon launched Amazon Web Services (AWS) in 2006 largely as an experiment. Most industry analysts saw it as a cost center that probably wouldn’t generate revenue for many years, if ever. By the first quarter of 2019, revenue from AWS was $7.7B, and annual revenue was expected to be $30B.⁸ AWS generated more than half of the operating income for Amazon as a whole and was growing twice as fast as its e-commerce counterpart.

Several factors have pushed organizations toward cloud-based hosting, including lower costs, better disaster recovery, increased reliability, ubiquitous access to data, improved scalability, and elasticity. However, placing data and applications outside the organization has its downsides. Companies lose control over the exact location of their data and become dependent on the cloud provider. Companies also have to trust that the cloud provider is adequately protecting their data. As companies increase their use of cloud providers, they also inadvertently make their data potentially less secure. As a result, some companies have chosen to keep especially sensitive data located in in-house data centers.

Most companies using cloud-based hosting have their data continuously backed up, so recovery is nearly instantaneous. It’s rare to lose cloud-hosted data due to a natural disaster. Backup sites are spread across the globe, so redundant backups mitigate damage from a local disaster.

## Test Your Understanding

- 28. a. What are the main alternatives for backup sites?
- b. What is the strength of each?
- c. What problem or problems does each raise?
- d. Why is cloud-based hosting beneficial?
- e. What might be the downside to cloud-based hosting?
- f. How does cloud-based hosting limit the damage from a local disaster?

⁸ Beth Kindig, “Best Bet for Tech Stocks in 2019? Secular IaaS Cloud,” SeekingAlpha.com, February 20, 2019. https://seekingalpha.com/article/4242423-best-bet-tech-stocks-2019-secular-iaas-cloud.

## Office PCs

Although servers are critical, office PCs probably hold most of a firm’s business information and analysis capabilities. A fire is as likely to destroy an office area or several office areas as it is to destroy a server room.

### DATA BACKUP
In a disaster, there often is no way to move many desktop PCs out of harm’s way. For instance, even if a firm only uses laptops, which are easily moved, this will be ineffective in a building fire in the middle of the night. The only real solution is to have centralized backup for PC files and to enforce up-to-date file synchronization.

### NEW COMPUTERS
If most PCs are lost, a company will need new computers and will need them very quickly. Prior arrangements with the firm’s equipment vendors can smooth this process.

A new computer is not enough. It must have application software, so it is important for firms to keep their installation media or, if they have standard configurations, to have disk images of these standard configurations accessible after a disaster.

### WORK ENVIRONMENT
Another issue is finding a place for people to work. A common option is to secure rooms in a hotel that has good Internet access. Work at home is another option, but this eliminates the human interactions that are especially critical in the fluid and uncertain environment after a disaster. People may also do better emotionally in an environment with their familiar coworkers.

## Test Your Understanding

29. What three things should a firm do about disaster recovery planning for office PCs?

## Restoration of Data and Programs

Earlier in this chapter, we looked at the archival backup of program and data files. The companies must restore these files at the backup computer site.

Restoration from backup tapes is one way to move files to the backup site. If this is the goal, then the backup site must have the proper equipment to do the restoration. In addition, companies must deliver backup tapes to the backup site rapidly and securely. This can be difficult to do during natural disasters or if the backup site is far from the storage site for backup tapes.

Of course, if the company uses continuous data protection, discussed earlier, then no recovery is necessary. The backup system is immediately ready to go to take over.

## Test Your Understanding

30. a. What must be done to restore data at a backup site via tapes?
b. How does this change if a firm uses continuous data protection?

## Testing the IT Disaster Recovery Plan

Just as business continuity plans need testing, companies also need to test IT disaster recovery plans in as realistic a way as possible. In addition, companies must test rehearse their IT disaster recovery procedures to improve response speed and accuracy.

## 10.6 Conclusion

This book has been organized around the plan–protect–respond cycle. Most chapters dealt with the protect phase. This final chapter completes the cycle by discussing response to both traditional security incidents and disasters.

The chapter began with a discussion of some basic incident and disaster response terminology and concepts. We focused on a four-level severity scale for incidents—false alarms, minor incidents that can be handled by the on-duty IT staff, major incidents that require the convening of the firm’s CSIRT, and disasters that affect IT alone or threaten business continuity for the entire firm. For all incidents and disasters, speed and accuracy are critical. These require extensive planning and rehearsals.

We then looked at response for major security incidents. We discussed a number of stages, including detection, analysis, escalation, containment, recovery, apology, punishment, and postmortem evaluation. We also discussed the organization of the CSIRT. For punishment, we discussed the difficulty of criminal prosecution, compared to the (relative) simplicity of disciplining employees.

This was followed by a discussion about legal considerations, which began with the difference between criminal and civil law. It then discussed jurisdictions in the United States at the federal and state levels and international cybercrime law. It also discussed rules of evidence and computer forensics. This section ended with a discussion of federal laws dealing with hacking, denial-of-service attacks, malware attacks, and the interception of electronic messages in transit and in storage.

The next section dealt with IDSs. We looked at the four functions of IDSs. We also looked at distributed IDSs using HIDSs and NIDSs. We looked at aggregated log files and the difficulty of event correlation. We discussed the problems of tuning and the difficulties of doing event correlation across multiple saved log files.

The chapter ended with a discussion of business continuity planning and IT disaster response. For IT disaster response, it is important to restore server functionality at other sites. Many companies have moved to cloud-based hosting to protect their data and systems. The benefits of using data centers were also discussed. Business continuity response in disasters that threaten the operation of the business is a far more complex task. A great deal of planning is needed for success.

## Security @ Work

## Largest! Data! Breach! Ever!

If you think back to your earliest experiences with the World Wide Web, you may recall the atmosphere of a Web 1.0 world. Web 1.0 was an extremely stripped-down version of the web that we know and love today. At the time, a majority of web content was static text. Fancy animations, embedded videos, and rich graphics were not even possible due to a variety of constraints (e.g., limited bandwidth). Additionally, the vast majority of people accessing the web at that time were content consumers, not content creators. The blogs, wikis, and social media platforms that

are the juggernauts of the Internet today did not exist, and the search engines in use at that time were precursors to Google.

One of the core sites that attracted heavy usage at that time was Yahoo!. Developed in 1994 by David Filo and Jerry Yang, Yahoo! was essentially a portal for accessing a variety of different types of content on the web.⁹ This included topics like arts, business, entertainment, news, recreation and sports, and science. Within 2 years, the company was worth more than $800 million, and at the peak of the dot-com

(continued)

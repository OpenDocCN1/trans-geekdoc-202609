
Antispyware, as discussed earlier in this book, scans your computer to see whether there is spyware running on your machine. This is an important element of computer security software that was at one time largely ignored. Even today, not enough people take spyware seriously or guard against it. Most antispyware works by checking your system for known spyware files. Each application must simply be checked against a list of known spyware. This means that you must maintain some sort of subscription service so that you can obtain routine updates to your spyware definition list. Most antivirus solutions now also check for spyware.

In today’s Internet climate, running antispyware is as essential as running antivirus software. Failing to do so can lead to serious consequences. Personal data, and perhaps sensitive business data, could easily be leaking out of your organization without your knowledge. And, as was pointed out earlier in this book, it is entirely possible for spyware to be the vehicle for purposeful industrial espionage.

Barring the use of antispyware, or even in conjunction with such software, you can protect yourself via your browser’s security settings, as discussed in a previous chapter. Additionally, several times throughout this book, you have been warned to be cautious about attachments and Internet downloads. You would also be well advised to avoid downloading various Internet “enhancements,” such as skins and toolbars. If you are in an organization, prohibiting such downloads should be a matter of company policy. Unfortunately, many websites today require some sort of add-in such as Flash in order to function properly. The best advice for this situation is to only allow add-ins on trusted, well-known sites.

### IDSs

IDSs have become much more widely used in the past few years. Essentially, an IDS inspects all inbound and outbound port activity on a machine/firewall/system, looking for patterns that might indicate break-in attempts. For example, if an IDS finds that a series of ICMP packets were sent to each port in sequence, this probably indicates that the system is being scanned by network-scanning software, such as Cerberus. This type of scan is often a prelude to an attempt to breach system security, and it can be very important to know that someone is performing preparatory steps to infiltrate your system.

Entire volumes have been written on how IDSs work. This chapter cannot hope to cover that much information. However, it is important that you have a basic idea of how these systems work.

The sections that follow will first examine the broad categories in which IDSs tend to be viewed and then look at some specific approaches to IDSs. While this information is not all inclusive, the following sections do address the most common terminology used.

#### IDS Categorization

There are a number of ways in which IDSs can be categorized. The most common IDS categorizations are as follows:

*   Passive IDSs

*   Active IDSs (also called intrusion prevention systems, or IPSs)

##### Passive IDSs

A passive IDS just monitors suspicious activity and logs it. In some cases, an IDS may notify the administrator of the activity in question. This is the most basic type of IDS. Any modern system should have, at a minimum, a passive IDS along with the firewall, antivirus, and other basic security measures.

##### Active IDSs

An active IDS, also called an IPS, takes the added step of shutting down the suspect communication. Whether one uses an IDS or IPS is a decision that must be made after a thorough risk analysis.

Just as with antivirus software, it is possible for an IDS to have a false positive. It might suspect that something is an attack when in fact it is legitimate traffic. Imagine that an active IDS is looking at threshold monitoring to determine if an attack is occurring. A particular user normally works between the hours of 8 a.m. and 5 p.m. and uses a relatively small amount of bandwidth. If the IDS detects the user at 10 p.m. using 10 times his normal bandwidth, it might perceive that this is an attack and shut down the offending traffic. However, it may be found later that this was a legitimate user working late on a critical project that was due to a client the next day, and the IPS prevented that from happening. This is a false positive.

This is an excellent place to consider risk analysis. You have to weigh the hazards of false positives against the risk of allowing an attack to proceed undetected before deciding whether a passive IDS or an IPS is appropriate for your organization. It is often the case that different network segments will have different risk profiles. You may find that a passive IDS is appropriate for most of your network but that an IPS is needed for the most sensitive network segments.

#### Identifying an Intrusion

There are really two ways of identifying an intrusion. The first method is signature based. This is similar to the signatures used by antivirus. However, IDS signatures cover issues beyond malware. For example, certain DoS attacks have specific signatures that can be recognized.

The second method is statistical anomaly. Essentially, any activity that seems outside normal parameters and far enough outside the given parameters to be a likely attack is identified as a probable attack. Any number of activities can trigger this type of alert, such as a sudden increase in bandwidth utilization or user accounts accessing resources they have never accessed before.

Most IDSs use both forms of attack identification. The two real issues for selecting an IDS are its ease of use and its signature database. There are certainly other considerations, such as price, but ease of use and its signature database are the most important in deciding on an IDS.

#### IDS Elements

Whether it is an active IDS or a passive IDS, and regardless of whether it is commercial or open source, certain elements/terms are common to all IDSs:

*   A `sensor` is the IDS component that collects data and passes it to the analyzer for analysis.

*   The `analyzer` is the component or process that analyzes the data collected by the sensor.

*   The `manager` is the IDS interface used for management. It is a software component of the IDS.

*   The `operator` is the person primarily responsible for the IDS.

*   `Notification` is the process or method by which the IDS manager makes the operator aware of an alert.

*   An `activity` is an element of a data source that is of interest to the operator. It may or may not be a possible attack.

*   An `event` is any activity that is deemed to be suspicious and a possible attack.

*   An `alert` is a message from the analyzer indicating that an event has occurred.

*   The `data source` is raw information that the IDS is analyzing to determine if there has been an event.

All these elements are part of an IDS and function together to capture traffic, analyze that traffic, and report anomalous activity to the operator of the IDS. An IPS has additional elements that enable it to shut down offending traffic.

#### Snort

A number of vendors supply IDSs, and each has unique strengths and weaknesses. Which system is best for your environment depends on many factors, including the network environment, security level required, budget constraints, and skill level of the person who will be working directly with the IDS. One popular open-source IDS is Snort, which can be downloaded for free from [www.snort.org](http://www.snort.org).

We will examine Snort briefly in this section. While it is not the only IDS available, it is free, and that makes it an attractive option for many people. We will walk through the basic configuration of Snort for Windows.

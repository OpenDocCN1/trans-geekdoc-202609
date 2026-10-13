

# Firewall Bastion Host Operating Systems and Monitoring and Logging

The bastion host operating system of a firewall device supports only firewall functionality. The bastion host operating system of an ISP connection device supports firewall services and connection services. The bastion host operating system of a wireless access point supports firewall services, wired connection services, wireless connection services, and possibly other services (such as `802.1x`).

General-purpose operating systems include `Windows`, `Linux`, `Mac OS`, `UNIX`, and so on. These operating systems support various purposes and functions, including acting as client or server host operating systems. When used as a bastion host operating system, each system must be hardened and locked down. Otherwise, an insecure host operating system renders the security provided by the firewall worthless. If an attacker can crash the firewall host or bypass the firewall filtering, the firewall cannot provide effective security protection.

General-purpose operating systems can be reasonably hardened for use as bastion host operating systems, but this requires specific and detailed modifications. Most software firewall products include a guide for performing operating system hardening to improve bastion host security and reduce vulnerabilities and backdoors that could lead to firewall compromise.

Some firewalls include pre-hardened versions of general-purpose operating systems as the bastion host operating system. Many Linux-based firewalls (such as `pfSense`) fall into this category.

The benefit of using a general-purpose operating system as a bastion host operating system is that such operating systems are widely available. Some of them (primarily `Linux` variants) are free. Additionally, you can leverage existing general-purpose operating system knowledge and skills to manage the bastion host. However, remember that general-purpose operating systems have a wider attack surface and a higher risk of new exploits.

The advantage of a proprietary operating system as a bastion host operating system is fewer known attacks and a lower risk of future exploits. However, a proprietary operating system may differ significantly from other operating systems in the environment, potentially requiring system administrators to learn an entirely new system to properly and securely manage the firewall. Furthermore, most proprietary operating systems are released only on bastion host hardware. This makes acquisition more difficult and, in most cases, more expensive (at least compared to free open-source alternatives).

## Monitoring and Logging

[Monitoring](#30_glossary.xhtml#gloss304) and [logging](#30_glossary.xhtml#gloss283) are the observation and recording of events and traffic that occur on or traverse the firewall. Theoretically, you can log every packet that traverses the firewall; however, this is usually impractical because the required storage space would be enormous. Some products can maintain a sliding window of recorded traffic, using multiple terabytes of storage to cover hours of communication. However, these devices are used for advanced security management and are beyond the scope of this chapter.

Firewall monitoring and logging are intended to record events that occur on or traverse the firewall (**Figure 7-6**). You can use various logging methods. You can log everything, or you can log only events that appear significant. Typically, you will fine-tune logging over time through practical experience. Most security professionals recommend capturing everything initially. Later, after determining that specific types of information, traffic, or events lack forensic, evidentiary, or historical value, you can adjust logging and reduce the volume of records.

![Figure 7-6 Example of a pfSense firewall log display interface. ¶ © pfSense](Images/9781284183658_CH07_FIGF06.png)

**Figure 7-6** Example of a pfSense firewall log display interface. ¶ © pfSense

Firewall logging ensures that defined filters or rules are adequate and functioning as intended. By monitoring traffic traversing the firewall filtering scheme, you can discover traffic that the firewall should have blocked but allowed due to a lack of valid rule definition (or improper rule definition).

> **Note**
>
> An example of a device capable of logging all traffic within a sliding window is the `Solera DS` series of network forensics appliances (owned by `Symantec`). For more information on such advanced network monitoring products, visit the `Symantec` website: [https://www.symantec.com/products/network-forensics-security-analytics](https://www.symantec.com/products/network-forensics-security-analytics).

Generally, every connection allowed by the firewall should be logged, as well as every packet dropped or blocked. This "log and monitor everything" stance ensures that nothing slips through the cracks and that future investigation of log file contents will reveal complete data. You can always discard extraneous and unnecessary data later, but you cannot recover critical data that was not recorded during the actual event.

Firewall logging can be performed on the firewall or offloaded to a dedicated logging system. In either case, the firewall collects the events and/or packets you want to log. The difference lies in whether the information is stored in a log file local to the firewall or transmitted via a network connection to a dedicated log server.

A famous and widely used [centralized logging system](#30_glossary.xhtml#gloss72) is `syslog`. [Syslog](#30_glossary.xhtml#gloss490) is a standard for forwarding log messages from client devices (in this case, the firewall) to a centralized server. `Linux` and `Unix` systems have supported `syslog` functionality for decades. `Windows` systems prior to `Windows 7` required third-party products to interact with `syslog` services. Most network devices (including firewalls, switches, proxies, etc.) natively support `syslog` (i.e., can be used without third-party media).

Firewall logging:

*   Creates an activity history for traffic and trend analysis and growth forecasting
*   Tracks usage levels and times for load balancing, billing, and even chargeback to users
*   Discovers new attack methods or techniques, especially those based on network packet manipulation
*   Detects intrusions or security breach attempts
*   Creates legally admissible evidence usable for prosecution

Firewall logs recording all events generate a large volume of recorded information. Always track available remaining storage capacity to ensure sufficient space for storing new recorded events. As current storage devices approach capacity limits, back up records and move them to long-term archival storage. You never know how far back you may need to look in a future investigation to uncover evidence of a security breach. Your organization's written retention policy should define how long logs are kept.

In addition to addressing storage needs, you must be able to analyze the recorded data. Log file analysis is typically not an exciting task for most people. It is long and tedious, even maddeningly boring. Fortunately, the evolving field of automated analysis tools can reduce the time and burden of log file investigation. Firsthand knowledge, understanding, and experience remain the best tools for interpreting and comprehending firewall log contents.

One of the final steps taken by most experienced hackers after penetrating your network is to erase all evidence of their activity. They typically accomplish this by deleting log files or using specialized tools to surgically edit log files. For example, `SolarWinds Event Log Consolidator` is a tool for editing `Windows` log files that deletes only entries matching keywords (such as IP addresses or usernames). To counter this potential threat, use [Write Once, Read Many (WORM)](#30_glossary.xhtml#gloss557) storage devices to preserve all log files. Using `WORM` means logs can be written once and subsequently accessed read-only many times. Intruders cannot edit data written to a `WORM` device.

If you decide not to log everything traversing the firewall, here is a brief list of the essential items that must be logged:


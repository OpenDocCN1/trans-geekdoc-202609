
# Understanding and Interpreting Firewall Logs and Alerts

## Events to Log

*   All connection attempts rejected by the firewall
*   All traffic directed at the firewall
*   Any access to internal resources by external hosts
*   Any access to external resources by internal hosts
*   Any modification or disabling of firewall rules and filters
*   All firewall reboots, storage device shortages, or other abnormal operational events

Every firewall management interface is different. Thus, the methods and mechanisms you employ to configure your specific logging and monitoring will be different, as well. Always be sure to consult the firewall’s documentation about the type of logging and what types of events are logged before deploying a firewall.

Define firewall logging in the firewall security policy included in your organization’s network security policy. The logging and monitoring features of a firewall are as essential as the rule and filter mechanism you use to allow or deny traffic. Configuring and recording logs is important, but understanding how to interpret firewall logs is more important.

## Understanding and Interpreting Firewall Logs and Alerts

Enabling firewall logging is often a fairly simple task. Recording traffic and events into a file is not really a complex task. But deciding which events warrant the triggering of an alert and what the contents of a log file actually mean is not always so straightforward.

An [alert](#30_glossary.xhtml#gloss11) is the automated notification to an administrator when a specific event affects the firewall. Some software host firewalls are preconfigured with a wide number of pop-up messages triggered each time one of the all-too-common activities occurs. For example, each time a new application attempts to communicate with the network, a firewall pop-up alert might notify the user of this event and prompt an action ([FIGURE 7-7](#17_chapter07_08.xhtml#fig7-7)).

![FIGURE 7-7 An example of a Windows Defender Firewall pop-up alert. ¶ © Microsoft Corporation](Images/9781284183658_CH07_FIGF07.png)

**FIGURE 7-7** An example of a Windows Defender Firewall pop-up alert. ¶ Microsoft Corporation

Appliance firewalls and those generally designed to protect a network rather than a single host are not as commonly configured with preset default alerts. Instead, the firewall administrator makes choices about which events actually need alerts. Some common events that usually warrant alerts include:

*   A firewall reboot
*   A connection attempt with the firewall host
*   Communications to or from a pre-identified IP address or subnet
*   Detection of some or all attack attempts
*   Detection of any successful intrusion or security breach

Ultimately, the organization’s security stance and the level of risk determine which events require alerts, as opposed to simply recording each in a log file. A common recommendation is to alert only on those events likely to require an administrator’s immediate response or action. Everything—or nearly everything—should go into a log, but not everything warrants an alert.

With or without alerts, a firewall’s logging system creates a massive amount of raw data that is not useful. You can perform analysis of a log file either in real-time or in periodic batches. You can hire a large staff of professionals whose primary task is to perform real-time log file analysis, or you can use an automated analysis or intrusion detection/intrusion prevention (IDS/IPS) tool. In most cases, automated log file analysis tools both reduce the strain on manpower and leverage the power of high-speed computing against the massive volumes of information collected by network firewalls.

Through careful analysis of firewall logs, you can detect several different types of unwanted or malicious activities, including worms, Trojan horses, remote control tools, port scans, and directed intrusion attempts. When you perform manual log analysis, the first hurdle is to gain access to the log file content.

Many firewalls record the log files in binary or obfuscated form so that they are difficult for external or unauthorized users to access. Such log files require administrators to access the log contents through a log reading interface. Some third-party products function as alternative management interfaces and can also interpret the log file format for viewing.

Once you obtain access to the log contents, either directly or through an interpretation interface, the next hurdle is to ensure that you are viewing the correct log. Several different types of log files can operate on your system, including traffic logs, audit logs, alert logs, console logs, and even a host device’s OS logs for software host firewalls. Another nuance is that the firewall device, a management host, or a centralized logging server might store its own logs. Finally, several dated versions of a log might exist. Be sure to open or access the most recent log—or whatever date range is of relevance to a specific investigation.

Of course, the key to interpreting and understanding the contents of a firewall log lies in understanding how network communications function. Every communication session involves two hosts, each with an IP address and port number. Some forms of communications have less information, such as blocked connection attempts, connectionless traffic, and Layer 3 protocols such as ICMP and IGMP.

By examining each established session to evaluate the source and destination IP addresses and the port numbers in use, you can quickly determine whether the transaction was valid or invalid. If the addresses are known—or at least not known to be malicious—and the ports are for acceptable services, then the communication is most likely benign. However, if an address is a known malicious host or an invalid address (such as an unassigned internal address) or you discover a known malware port, these are signs of unwanted and potentially malicious communications (or at least attempts to communicate).

The Internet Assigned Numbers Authority (IANA) and some security vendors maintain lists of well-known port numbers and the associated applications. They often list known malicious software and their commonly used port numbers. Search for “malicious ports” or “Trojan ports” to find current lists.

To examine and interpret firewall logs, you might:

*   Identify and discard all packets involved in benign sessions between valid hosts and valid ports.
*   Identify and discard all valid UDP transmissions to and from valid hosts and ports.
*   Identify and discard all valid ICMP (and other authorized protocols) to and from valid hosts.
*   Identify any communication from known malicious addresses. (This is a symptom of communications from known malicious hosts.)
*   Identify any communication from unauthorized or unassigned internal addresses. (This is a symptom of rogue internal hosts.)
*   Identify any communication to an unknown or unauthorized port on an internal host. (This is a symptom of rogue internal services.)
*   Identify any patterns of serial communication attempts across a sequential or randomized set of addresses and/or ports. (This is a symptom of scanning or probing.)
*   Identify significant volumes of nonsession traffic of the same or similar construction to one or a small group of internal addresses. (This is a symptom of flooding.)
*   Identify any packet of invalid size or invalid header construction. (This is a symptom of scanning, probing, or an exploitation attempt.)
*   Identify any packet with configured source routing. (This is a symptom of attempted intrusion or traffic shaping.)
*   Identify packets destined to nonresource-sharing systems, such as firewalls or routers. (This is a symptom of probing, network scanning, or an exploitation attempt.)

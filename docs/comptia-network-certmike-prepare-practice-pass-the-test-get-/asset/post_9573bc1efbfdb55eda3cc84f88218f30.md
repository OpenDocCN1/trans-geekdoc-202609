
When bandwidth utilization values are high, it can indicate a temporary traffic condition, but when they are consistently high, the connection might be overloaded with traffic. When this occurs, administrators can take any of the following actions:

- Increase the available bandwidth by upgrading the network hardware.
- Move servers or other devices to a less-trafficked network segment.
- Move applications or services that generate large amounts of traffic to servers on another network segment.

# EXAM TIP

The abbreviations Mb and Gb, with a lowercase b, stand for megabytes and gigabytes, which are typically used to measure network speeds. MB and GB, with a capital B, stand for megabytes and gigabytes, which are used to measure storage transfer rates. Network+ exam candidates should be aware of the differences in the abbreviations and how they are used.

# Latency

Latency is the delay that is incurred between the transmission of a packet and its receipt at the destination. Typically measured in milliseconds, latency and its value as a metric depending on the location of the destination being measured. There are many reasons packets can be delayed, including excessive traffic on the network, an overloaded switch, a malfunctioning network adapter, or any number of other causes.

The effect of latency is different depending on the type of traffic on the network. A brief delay in accessing a file from a server is not a big problem, but for real-time protocols such as VoIP or iSCSI, even a slight amount of additional latency can affect the quality of a voice call or data transfer.

# Jitter

The latency of a network is usually a relatively stable condition. Metric values can vary over time, but they tend to remain consistent from second to second. If they don't, and there are different latency measurements for successive packets transmitted to the same destination, this is called jitter.

The value of the jitter metric is a calculation of the difference between latency values for successive packets, usually expressed in milliseconds.
Networks can tolerate latency far better than they can tolerate jitter. In particular, jitter can interfere with real-time data transmissions such as those for VoIP.

# SNMP

There are many tools that can monitor performance metrics. Operating systems typically have some means of gathering metric values, such as the Windows Performance Monitor, for example, but one of the oldest and most comprehensive network-based tools of this kind is the Simple Monitoring Protocol (SNMP). SNMP is a centralized monitoring tool that can gather information from devices all over the network—including servers, workstations, switches, routers, and printers—and display it to administrators of the central management console.

SNMP consists of three basic components, as follows:

- **SNMP Agents** Software components that run on a managed device and gather data they send to the EMS (next item). Some agents are built into devices such as switches and routers, whereas others have to be installed by users.

- **Network Management System (NMS)** The NMS is the central console that receives all the information from the SNMP agents.

- **Information Management Base (MIB)** An MIB is a database of components on a managed device called identifiers (OIDs), which are capable of supplying performance metrics and other information to the NMS. The OIDs store information about the components as variables. The NMS can modify variables within the OIDs to remotely reconfigure the device.

- SNMP agents communicate with the NMS using message types, including GetRequest messages that an NMS sends to an agent, requesting the values of specific OID variables; SetRequest messages that supply revised values for specific OID variables; traps, unsolicited messages sent by an agent to the NMS containing information about an important event.

# NETWORK DEVICE LOGS

Most network devices generate logs of their activity, and in some cases many different types of logs. Monitoring logs is an important part of maintaining a network. Some of the log types are described in this section.

## Traffic Logs

Many devices can monitor traffic of their experiences, and in some cases, administrators can specify exactly what traffic should be logged. For example, a firewall can handle a great deal of traffic, and the vast majority of log entries will be for traffic that is successfully admitted through the firewall. However, it is also possible, in the case of firewalls, to adjust the logging levels to retain only the exceptions—that is, the packets that are blocked by the firewall because they do not conform to its rules.

## Audit Logs

Auditing is a feature provided in many operating systems and network devices that allows administrators to specify what information should be captured by the device's audit logs. Auditing generally provides administrators with more granularity in what components to monitor and what activities to. For example, an administrator can opt to audit user logins to a server. Selecting all of the logins will produce a log of log entries, including successful logins. Administrators might have reason to monitor all of the logins, and it is also possible to select just the failed logins to let administrators know when someone attempts a brute-force password attack.

Auditing can also be centralized on the network. One way to do this is to use an authentication, authorization, and accounting (AAA) server such as Remote Authentication Dial-In Service (RADIUS).

# Syslog

One of the problems with monitoring logs is that devices typically store their logs locally, and the prospect of examining the logs on every network device individually can be daunting to administrators. *Syslog* is a mechanism for sending log entries from a network device to a central server, where they are added to a single log covering all of the devices in one.

Syslog consists of the following elements:

- A syslog server
- Client applications on the individual network devices
- A syslog message format

Syslog messages, in addition to the actual log information generated by the device, include a timestamp to indicate when the event occurred. Though not required by the standard, many network devices include a Facility code that indicates the type of message and a Severity code that indicates the nature of the event. The Severity level used in syslog messages are shown in Table 13.1.

### 13.1 Syslog severity

| Code | Severity | Keyword | Description |
| :--- | :--- | :--- | :--- |
| 0 | Emergency | emer | System is unusable |
| 1 | Alert | alert | Action must be taken |
| 2 | Critical | crit | Critical conditions |
| 3 | Error | err | Error conditions |
| 4 | Warning | warning | Warning conditions |
| 5 | Notice | notice | Normal but significant |
| 6 | Informational | info | Informational messages |
| 7 | Debug | debug | Debug messages |

# Log Reviews

Log reviews are an important part of monitoring network and device performance. However, the biggest problem with reviewing logs is the sheer amount of data they contain. For example, the logs maintained by a web server typically have entries for every user that connects to it. A busy website might handle thousands or millions of hits each day, resulting in massive logs that administrators cannot easily read. Instead, use tools that read and interpret the logs for them, so they can concentrate on the most important data.

# INTERFACE ERRORS OR ALERTS

Operating systems maintain statistics for every network interface, such as how many bytes and packets it has transmitted and received. The means of accessing this information differs on the device, but in many cases, there are Get-NetAdapterStatistics cmdlet in Windows PowerShell or the ifstat command in Linux.

NetFlow is a proprietary tool that administrators use to gather statistical data about the IP traffic that routers and switches receive and send through each of their ports. Routers and switches periodically send the NetFlow data they gather to a central server. That server, called a NetFlow collector, collates the data from all the devices into a single. Some of the most important statistics are as follows:

- **Link State (Up/Down)** Specifies whether the interface is physically connected to the network. A down state could be the result of an issue with the interface itself, a configuration setting on the device, a hardware problem with the network, or a problem with the device at the end of the connection.
- **Speed/Duplex** Specifies the interface's available bandwidth and whether it is functioning in full-duplex or half-duplex mode. Mismatched duplex settings at end of a connection prevents the device from accessing the network.

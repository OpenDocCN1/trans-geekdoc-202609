
# Cloud Encryption Solutions

Cloud encryption solutions can encrypt information as it moves in and out of applications and into storage with strong key-based encryption. Most reputable cloud service providers offer cloud encryption options. The most used type of cloud data in transit encryption is the `HTTPS` protocol. When using the more modern and secure version of Secure Sockets Layer (`SSL`) called Transport Layer Security (`TLS`), all traffic is encoded so only authorized users can access the data. If an unauthorized third party sees the data, it remains unreadable because the digital keys to lock and unlock it are at the user and destination layers. Keys should be generated and issued using an asymmetrical algorithm between trusted entities, while certificates are certified during the original connection.

## Logs

Every device on a modern cloud network generates logs. Some logs are human readable, and some logs look like gibberish. Some logs are more useful than others, and we should understand which cloud logs need to be preserved for future analysis and for how long. You don't need to log everything, but what you do log should be purposely collected and managed because the logs can show you who did what activity and how the systems they touched responded.

The Center for Internet Security (`CIS`) Critical Security Controls Version 8 focuses on the collection, maintenance, monitoring, and analysis of audit logs. Our organizations are evolving quickly, and we have to learn to deal with log data in the big data cloud era. Analyzing audit logs is a vital part of security, not just for system security but for processes and compliance. Part of the process of log analysis is reconciling logs from different sources and correlation even if those devices are in different time zones. Network Time Protocol (`NTP`) will help synchronize devices using the cloud. Google Cloud has its own `NTP` protocol called Google Public `NTP`.

In a basic network topology, you will have many types of devices, including routers, switches, firewalls, servers, and workstations. Each of these devices that helps connect you to the rest of the world will generate logs based on its operating system, configuration, and software. Examining logs is one of the most effective ways of looking for issues and investigating problems happening on a system or in an application.

Synchronization and the ability to correlate the data between these devices are vital to a healthy environment. Attackers can hide their activities on assets if logging is not done correctly; therefore, you need a strategic method of consolidating and auditing all your logs. Without solid audit log analysis, an attack can go unnoticed for a long time. According to the 2021 Verizon Data Breach Investigations Report, The Verizon Threat Research Advisory Center intelligence collections in both 2019 and 2020 began with cyber espionage targeting cloud environments by the Chinese menuPass threat actor. Among the ongoing threats were attacks on remote access. The full report was based on detailed analysis of more than 79,600 security incidents, including 5,258 data breaches. You can download the full details at `www.verizon.com/business/resources/reports/dbir/2021/year-in-review-2021`.

Logging involves collecting data from a large number of data sources, which has its own challenges including collection, storage, encryption, and parsing. Key considerations when configuring logs for collection include normalization, alerting, security, correlation, availability, monitoring, and analysis.

Normalization or parsing logs enables analysis of the data. Parsing the logs into specific fields allows for easier reading, correlation, and analysis. Correlation means that you are able to connect the dots to identify a sequence of events that have the potential to be a breach. Monitoring and alerting for specific events, or after analysis has been done on several scenarios that are being monitored for security incidents, is important because it is a more proactive approach. To be able to go back into storage requires availability. The logging solution chosen must make sure that the logs are not only secure but provide data compression and other procedures to address the high volume.

Without logging, a threat actor can be in an environment and fly completely under the radar. There are many solutions for logging for audit and centralization, including Elasticsearch, Logstash, and Kibana (`ELK`), which is the most common open-source solution used. There are some security information and event management (`SIEM`) tools that are customizable for security analytics. `SIEM` tools centralize information gathering and analysis and provide detailed dashboards and reporting that allow critical information to be seen through visualization, and they offer manual analysis as well as automated analysis capabilities. They work with logging infrastructures using tools such as `syslog`, `syslog-ng`, or others that gather and centralize logs, building logging infrastructures that capture evidence used for incident analysis and creating an audit trail. At the same time, additional information captured such as network flows and traffic information, file and system metadata, and other artifacts are used by responders who need to analyze what occurred on a system or network.

Gartner's Magic Quadrant report for 2021 includes `Splunk`, `Rapid7 InsightIDR`, `LogRhythm`, and `Exabeam`. These `SIEM` tools work by taking a baseline of two to four weeks of log ingestion to learn the normal state of an organization and then can start monitoring and alerting for anomalies.

## Monitoring Configurations

The cloud is not a single object. There are many moving parts that affect performance and availability, with each part needing to work well with other parts. When looking at monitoring a cloud environment, you have to watch the network, the individual `VMs`, the databases, the websites, and storage. With the network, cloud administrators have to watch for connectivity to make sure they are not overwhelmed with traffic. The `VMs` will have to be monitored for access and status to make sure they are operating as intended. Database monitoring is incredibly important because of what is in the database, usually sensitive organizational data. Databases will need to be monitored for queries, access requests, integrity, and backups. Proactively monitoring websites will allow for optimal uptime, and storage is costly, so making sure performance and analytics are kept within proper ranges will keep expenses down.

Some cloud monitoring best practices may include the following:

*   Decide the most important metrics and events
*   Choose the right cloud monitoring software
*   Monitor all your cloud infrastructure from one platform
*   Automate monitoring tasks
*   Track end-user experience
*   Test for cloud failure
*   Monitor services and costs

It is difficult to keep up with shifting policies and compliance, but with automation open-source software like `Puppet` or other tooling such as `SolarWinds`, the organization must be able to monitor the cloud ecosystem for changes and revert as needed. It can be time-consuming and tedious to manually do audit inspections to prepare for an auditor. `Puppet` is mostly used on Linux and Windows, but it's capable of managing infrastructure through continuous monitoring using policy as code. For more information, visit `puppet.com/use-cases/continuous-compliance`.

## Key Ownership and Location

[Chapter 6](#c06.xhtml), “Cryptography and PKI,” covered public key infrastructure, which allows two parties to communicate securely even if they were previously unknown to one another. This chapter covers the certificate authority (`CA`), registration authority (`RA`), certificate revocation lists (`CRLs`), digital certificates, and how they are distributed. The question this chapter covers is how this process can be different in a cloud-based ecosystem.

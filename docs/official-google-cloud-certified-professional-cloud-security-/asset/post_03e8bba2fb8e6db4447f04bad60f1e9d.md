
# Platform logs

Next, we will look at examples of platform logs:

- **VPC logs**: VPC flow logs contain granular VM flow-level network telemetry from Google Cloud. VPC flow logs provide insights into VPC traffic, traffic planning, a better understanding of networking costs, and forensics in the case of security-related incidents. VPC logs are aggregated collections of packets for an interval and for a given connection. These are default retained for 30 days and they do not lead to any performance degradation. The VPC flow log includes a 5-tuple—for the source IP address, destination IP address, source port number, destination port number, and protocol (TCP or UDP)—and the timestamp. The metrics includes packets, bytes (throughput), RTT for TCP flows, VPC annotations (region, zone, and VM name), and geographic annotations (country, region, and city). Logs are collected on each VM connection and aggregated at 5-second intervals. Google samples about out of every 10 packets.
- **Firewall logs**: You can enable firewall rule logging individually for each firewall rule. Firewall rule logging only records TCP and UDP connections. Log entries are written from the perspective of VM instances.
- **NAT logs**: You can enable NAT logging on a NAT gateway instance. You can choose to generate logs for the creation of NAT connections and when packets are dropped because no port was available for NAT. Cloud NAT logs both TCP and UDP, including dropped egress packets. Dropped ingress packets (for example, if an inbound reply to an egress request was dropped) are not logged.

We have covered the different types of logs and their relevant examples. We will now consider the retention of logs. Defining a retention period gives you the ability to change the log period to match your compliance or regulatory requirement. Let's take a look at the key log types and their associated log retention periods in the following section.

# Log retention

Cloud Logging retention is critical for many organizations due to compliance requirements. The default retention period is often not sufficient; therefore, many customers configure custom retention periods for their logs. Longer retention periods come at a higher cost.

| Retention | Cost |
|---|---|---|
| Admin audit logs | 13 months (400 days) | Free |
| System Event audit logs | 13 months (400 days) | Free |
| Access Transparency logs | 13 months (400 days) | Free |
| Data access logs | 30 days | $0.50 per GB over 50GB/Month |
| All other logs | 30 days | $0.50 per GB over 50GB/Month |
| Workspace admin console logs | 6 months | Free |
| Log sink | Indefinite | Based on service option (GCS, BQ, Pub/Sub) |

Figure 12.4 - Cloud Logging default retention periods and costs

12.4 shows the default retention periods and the associated costs for the different types of logs that we have covered. The costs are correct at the time of writing and may change.

Next, we'll explore the topic of log management. We will learn about log producers and consumers and understand how a log router works. We will also discuss exporting logs and creating log sinks in detail.

# Log management

A key component of logging is the ability to export logs so they can be consumed by a service running on the cloud or by a third-party solution. You will also learn how to aggregate logs, build log pipelines, perform log analysis, and deliver logs to SIEM solutions.

# Log producers

All resources that generate logs, such as products, services, and applications, whether they are in the cloud or a hybrid environment, are classified as log producers. Google Cloud services or services running in your on-premises data center or a third-party cloud service provide

# Log consumers

Log consumers are services such as centralized logging solutions and SIEM solutions. Any service that has the ability to consume logs and provide functions such as alerting, troubleshooting applications, and business intelligence is considered a log consumer. Cloud Logging on Google Cloud is an example of such a service.

# Log Router

The term Log Router has been used a few times in the chapter; we will now look at the workings of the Log Router in more detail to understand what it is and how it works. A Log Router ensures that logs are collected from producers and delivered to the consumer.

![](img/f681dfc12450e3a4c257352b70dbceca_349_0.png)

Figure 12.5 shows how a Log Router works. Logs are transmitted to the Cloud Logging API, where they are processed by the Log Router. These logs include audit logs, platform logs, and user-written logs. The Log Router compares each log entry to the rules that are already in place to determine which log entries should be ingested and stored, which log entries should be included in exports, and which log entries should be discarded.

To export logs, create a filter that selects the relevant log entries to export, and then select a destination. You can choose from these options:

- JSON files can be created in Google Cloud Storage buckets.
- Tables can be created in BigQuery datasets.
- JSON messages can also be delivered via Pub/Sub topics. This option also supports third-party integrations, such as Splunk.

Alternatively, you can create another Google Cloud project and have the log entries stored in Cloud Logging buckets.

Sinks are used to store the filter and the final destination. Google Cloud projects, organizations, files, and billing accounts can all be used as sinks. We covered sinks earlier in this chapter. We will look at them in more detail when we look at log exports in the following section.

# Log sinks and exports

Before we look at exporting logs, it's important to understand log sinks and inclusion/exclusion filters. Sinks tell Cloud Logging where to send logs. With sinks, you can send some or all of your logs to destinations that can handle them. Sinks are part of a specific Google Cloud resource, such as a project, billing account, folder, or organization. When a resource gets a log entry, the Log Router sends the log entry to the appropriate sinks and, if enabled, the Log Router forwards it to any ancestral sinks that belong to the resource hierarchy. The log entry is ultimately sent to the destination associated with the sink.

# Log management

- Log Search – Analysis
- Log-based metrics
- Alerting on Logs
- Dashboards

![](img/f681dfc12450e3a4c257352b70dbceca_351_0.png)

Figure 12.6 – Log exports and sinks

Figure 12.6 shows the relationships between sinks, filters, and exports. By defining one or more sinks that have a log query and an export destination, you can easily export logs from a database. New log entries are compared to each sink as they are received by Cloud Logging. When an entry matches a sink filter, it is written to the sink's destination.

If no filters are attached to a sink, all logs will match and be forwarded to the destination. The inclusion filter can be used to choose specific logs for the sink. Alternatively, you can use exclusion filters to keep unwanted logs out of the sink. Filters are defined using the Logging query language.

Log buckets are used by Cloud Logging to store and organize data in your Cloud projects, billing accounts, folders, and groups. Using Cloud Logging, you can study your logs in real time by having them indexed, optimized, and provided to you. Log buckets are distinct from Cloud Storage buckets, despite the similarity of their names. Log buckets should be considered a local resource. You can pinpoint the location of the servers and storage facilities that handle your logs.

Next, we will look at the steps for how to create a log export.

# Cloud Logging

# Creating a log export

In this section, you will learn how to create a log export sink. You will build a centralized logging solution by creating log buckets that are bound to specified regions with retention policies.

You can create 100 log buckets per project. Follow these steps to create user-defined log buckets:

- From the Logging menu, select Logs Storage.
Click Create Log Buckets.
- Fill out Name and Description for your bucket.
- (Optional) To set the region in which you want your logs to be stored, click the Select log bucket drop-down menu and select a region. If you don't select a region, the global region is used, which means the log could be physically located in any of the regions. In our demonstration, Figure 12.6, we have used a region in Australia.

> Note
You can't change the region of your log bucket once you have created it. You can, however, create an additional log bucket in a different region, reroute the associated sinks to the new log bucket, and delete the log bucket.

![](img/f681dfc12450e3a4c257352b70dbceca_352_0.png)

Figure 12.7 – Create log bucket

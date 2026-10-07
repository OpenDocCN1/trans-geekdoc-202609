# Log retention

Cloud Logging retention is critical for many organizations due to compliance requirements. The default retention period is often not sufficient; therefore, many customers configure custom retention periods for their logs. Longer retention periods come at a higher cost.

| Retention | Cost |
|---|--|
| Admin audit logs | 13 months (400 days) | Free |
| System Event audit logs | 13 months (400 days) | Free |
| Access Transparency logs | 13 months (400 days) | Free |
| Data access logs | 30 days | $0.50 per GB over 50GB/Month |
| All other logs | 30 days | $0.50 per GB over 50GB/Month |
| Workspace admin console logs | 6 months | Free |
| Log sink | Indefinite | Based on service option (GCS, BQ, Pub/Sub)

Figure 12.4 - Cloud Logging default retention periods and costs

12.4 shows the default retention periods and the associated costs for the different types of logs that we have covered. The costs are correct at the time of writing and may change.

Next, we'll explore the topic of log management. We will learn about log producers and consumers and understand how a log router works. We will also discuss exporting logs and creating log sinks in detail.

# Log management

A key component of logging is the ability to export logs so they can be consumed by a service running on the cloud or by a third-party solution. You will also learn how to aggregate logs, build log pipelines, perform log analysis, and deliver logs to SIEM solutions.

# Log producers

All resources that generate logs, such as products, services, and applications, whether they are in the cloud or a hybrid environment, are classified as log producers. Google Cloud services or services running in your on-premises data center or a third-party cloud service provide
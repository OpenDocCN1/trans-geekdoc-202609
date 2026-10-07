# Real-time log analysis and streaming

As mentioned earlier, Cloud Logging is a collection of different components. We have the Cloud Logging API, where all the logs are delivered. We also have the Log Router, where you can create your inclusion and exclusion filter to redirect the logs to a log sink. We also looked at several choices for logs after they've been removed from a log sink. With Google Cloud Storage, you can store the logs and apply lifecycle management rules based on your retention policy. If you wish to analyze the collected logs, you can do so with BigQuery.

In this section we will look at storing logs in BigQuery for analytics. At the time of writing, there is a built-in feature that Google Cloud has called Log Analytics. This feature is still in preview, will not feature in the exam. In addition to Log Analytics, you can also create a pipeline that streams to BigQuery.

![](bbox=[0.132, 0.355, 0.836, 0.467])

Figure 12.12 – Log streaming pipeline

Figure 12.12 illustrates a log streaming pipeline using Cloud Logging, Pub/Sub, and a DataFlow pipeline that triggers a Cloud Data Loss Prevention (DLP) template. DLP inspects sensitive data as personally identifiable information (PII) to remove sensitive data before storing it for analytics in BigQuery. In our example, we are exporting through Pub/Sub, then through Dataflow, and lastly to BigQuery. Dataflow is very useful for processing logs in real time and at scale. However, we don't need to stream logs; we can simply create a log sink and deliver to BigQuery.

BigQuery enables you to store data in a cost and effective manner. Its easy-to-use SQL interface can provide a solid foundation for creating AI models and simplifying data operations. Data Studio and Looker are two tools that can be used to visualize BigQuery results. Visualization is out of scope for our discussion. BigQuery offers an easy-to-use and powerful capability to run queries to help you with analytics that you can use for troubleshooting and security incident response. In the next section, we will discuss an example of exporting logs to address compliance requirements. We will also cover the configuration aspects of the log pipeline described here.

The Logs Dashboard displays the severity and error data for resources in your Cloud project. The Logs Dashboard allows you to spot patterns in your systems' activity, keep track of your workloads, and diagnose address issues. All the log-based metrics are preconfigured and cannot be modified. The Logs Dashboard only shows statistics for resources that generate log data.
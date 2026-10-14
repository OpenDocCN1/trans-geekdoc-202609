
# Amazon RDS

As a managed service, Amazon RDS handles database management tasks for you, such as provisioning, patching, backup, recovery, failure detection, and repair.

Amazon RDS offers three different deployment environments, including deploying in the cloud with Amazon Aurora or Amazon RDS, deploying hybrid workloads with Amazon RDS on AWS Outposts, and deploying with privileged access with Amazon RDS Custom.

As with all AWS services, there are no up-front investments required, and you pay only for the resources you use.

## Use Cases

Typical use cases for Amazon RDS include the following:

*   **Modern web and mobile applications.** Amazon RDS is an excellent choice to build well-architected applications, because it offers a secure storage solution with high availability, performance, and scalability with limited administration. Additionally, its pay-per-use pricing model allows you to effectively manage the cost of persisting your data in a relational database running in AWS.
*   **Legacy database migration.** Migrating on-premises legacy databases to Amazon RDS is the natural choice for organizations that look to modernize their workloads during their digital transformation journey. In addition to improved scalability and reliability, cost reduction is a critical factor to consider due to a significant saving in license fees as well as the benefit of the pay-per-use pricing model.

# Amazon DynamoDB

Amazon DynamoDB is a serverless NoSQL database service with consistent single-digit-millisecond performance at any scale.

Its serverless feature means you don’t need to provision any infrastructure, or patch, manage, install, maintain, or operate any software. DynamoDB also comes with zero-downtime maintenance.

As a NoSQL database, DynamoDB is designed and built to deliver high performance, scalability, manageability, and flexibility compared to relational databases. To support a broad spectrum of use cases, with DynamoDB you can use both key-value and document data models. To help you build enterprise-grade applications, Amazon DynamoDB provides strong read consistency and ACID (atomicity, consistency, isolation, and durability) transactions support.

To achieve consistent single-digit-millisecond performance, DynamoDB is optimized for high-performance workloads and provides APIs that encourage efficient database usage. It omits features that are inefficient and nonperforming at scale: for example, `JOIN` operations. DynamoDB delivers consistent single-digit-millisecond performance for your applications, whether there are 100 or 100 million users.

## Use Cases

DynamoDB is ideal for use cases that require consistent performance at any scale with minimal operational overhead, including but not limited to the following:

*   **Financial service applications.** Amazon DynamoDB transactions can be used to achieve ACID across one or more tables with a single request. ACID transactions are ideal for workloads that process financial transactions or fulfill orders. Amazon DynamoDB instantly adjusts to workloads as they spike up and down, enabling you to efficiently scale your database for market conditions, such as trading hours.
*   **Gaming applications.** Because of its ability to scale in and scale out, its consistent performance, and the ease of operations provided by its serverless architecture, Amazon DynamoDB can be used to efficiently persist all data element of any game platforms, such as game state, player data, session history, and leaderboards. This scalability optimizes your architecture’s efficiency whether you’re scaling out for peak traffic or scaling in when gameplay usage is low.
*   **Data streaming applications.** Amazon DynamoDB is widely used by media and entertainment companies as a metadata index for content management services or to serve near-real-time sports statistics. Amazon DynamoDB is also used to perform user watchlist and bookmarking services and to process billions of daily customer events for recommendations generation. These customers benefit from DynamoDB’s scalability, performance, and resilience. DynamoDB’s built-in elasticity enables streaming media use cases that can support any levels of demand.

# Troubleshooting

Troubleshooting and debugging data ingestion and storage issues related to capacity and scalability in AWS involves several steps and best practices. Here are some key strategies you need to know for the exam:

*   **Monitoring and logging.** Use `CloudWatch` to monitor your AWS resources and applications. Set up alarms to notify your data operations team of any anomalies in metrics such as CPU usage, memory usage, and I/O operations. Enable `CloudTrail` to log API calls and track changes to your AWS resources. This helps in identifying the root cause of issues.
*   **Scaling and performance optimization.** Implement auto scaling for your `EC2` instances and other scalable resources to automatically adjust capacity based on demand. Use read replicas and Aurora’s auto-scaling capabilities to handle increased read traffic and improve performance.
*   **Data ingestion optimization.** To optimize the performance of your data pipelines, use techniques such as data partitioning, caching, and parallel processing. For real-time data ingestion, leverage `Amazon MSK`, `Amazon Managed Service for Apache Flink`, `Amazon Kinesis Data Streams`, or `Amazon Data Firehose` to handle large volumes of streaming data. Additionally, consider supplementing these services with `AWS Lambda` functions to process data in real time and scale automatically based on the volume of ingested data.
*   **Storage management.** Use `Amazon S3` for enterprise-scale object storage. Implement lifecycle policies to move data to different storage classes based on data access patterns. Monitor `Amazon EBS` volumes for performance and adjust volume types or sizes as needed to meet capacity and performance requirements.
*   **Database optimization.** Ensure your database queries are optimized and indexes are properly configured to improve performance. Consider sharding your database to distribute the load across multiple instances. With `Amazon DynamoDB`, refrain from using `scan` operations whenever possible, due to their inefficient performance compared to other query operations.
*   **Cost management.** Use `AWS Cost Explorer` to monitor and analyze your AWS spending. Identify areas where you can optimize costs by adjusting resource usage. Consider purchasing reserved instances or savings plans for predictable workloads to reduce costs. Leverage spot instances for elastic ephemeral workloads to minimize costs.

By implementing these strategies, you can effectively troubleshoot and debug data ingestion and storage issues related to capacity and scalability in AWS.

# Summary

In this chapter, we covered data ingestion and data storage, which are the two key components of the collection phase of the machine learning lifecycle.

With ingestion, you aggregate the data for your ML solution from different sources and push it into AWS in its raw format. Data ingestion can occur in batches or in real time. `Amazon Data Firehose`, `Amazon Kinesis Data Streams`, `Amazon MSK`, and `Amazon Managed Service for Apache Flink` are used to ingest real-time data. `AWS DataSync` and `AWS Glue` are used to ingest batch data.

With storage, you persist the ingested data in a suitable AWS data store, where it will remain until it’s ready for processing. Storage comes in three different types: object, file, and block. `Amazon S3` is used to store object data, `Amazon EBS` is used to store block data, and `Amazon EFS` and the `Amazon FSx` family of services are used to store file data.

The drivers to select the appropriate ingestion and storage service depend on the specifics of your use case and include scalability, resilience, security, and cost.

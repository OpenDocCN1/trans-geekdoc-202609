+   Reliability: The tools need to provide failure recovery capability so critical data is not lost during the ingestion process. If there is no recovery capability, then make sure there is a capability for re-running ingestion jobs from the sources.

+   Support for different data sources and targets: Ingestion tools need to support a wide range of data sources, such as databases, files, and streaming sources. The tool should also provide an API for data ingestion.

+   Manageability: Manageability should be another consideration. Does the tool require self-management, or is it fully managed? Consider the trade-off before cost and operational complexity.

There are are of AWS services for data ingestion into a data lake on AWS. Kinesis Data Streams, Kinesis Firehose, **AWS Managed Streaming for Kafka**, and AWS Glue for streaming data requirements. For batch ingestion, you can have AWS Glue, SFTP, and AWS **Data Migration Service (DMS)**. In the following section, we will discuss how Kinesis Firehose and AWS Glue can be used for data ingestion management.

# Kinesis Firehose

Kinesis Firehose is a fully managed service for loading streaming data into a data lake. By fully **managed**, we mean you don't manage the underlying infrastructure; instead, you interact with the service API for the ingestion, processing, and delivery of the data.

Kinesis Firehose supports the key requirements for scalable data ingestion:

+   Support for different data sources such as websites, IoT devices, and video cameras using an ingestion agent or ingestion API.

+   Support for different delivery targets, including Amazon S3, **Amazon Redshift** (an AWS data warehouse service), **Amazon ElasticSearch** (a managed search engine), and **Splunk** (a log aggregation and analysis product).
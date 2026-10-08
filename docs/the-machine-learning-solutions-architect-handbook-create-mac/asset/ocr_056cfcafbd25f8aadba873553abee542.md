# Data ingestion

The data ingestion component is responsible for taking data of different formats (for example, structured, semi-structured, and unstructured) from different sources (for example, databases, social media, file storage or IoT devices) and persisting data in storage, such as object data storage (for example, Amazon S3), data warehouses, or other data stores. The ingestion patterns should include both real-time streaming as well as batch ingestion to support different sources.

There are different data ingestion technologies and tools for the different kinds of ingestion patterns. **Apache Kafka, Apache Spark Streaming, and Amazon Kinesis-Firehose** are some of the common tools for streaming ingestion. Tools such as **Secure File Transfer (SFTP)** and AWS Glue can be used for batch-ordered data ingestion. AWS Glue supports different sources and targets (for example, **Amazon RDS, MongoDB, Kafka, Amazon DocumentDB, S3**, and any databases that use JDBC connections.

When deciding which tools to use for data ingestion, it is important to assess the tools and technologies based on practical needs. The following are some of the considerations when deciding on data ingestion:

+   **Data format, size, and scalability:** Consider the needs for varying data formats, data size, and data velocity. ML projects could be using data from different sources and different formats (for example, tabular data such as **CSV** and **Parquet**, semi-structured data such as JSON/XML, and unstructured data such as documents or image/audio/video files). Do you need to scale the infrastructure to handle large data ingestion volume when needed, and do you need to scale it down to reduce costs when the volume is low?

+   **Ingestion patterns:** Consider the different data ingestion patterns you need to support. The tool or combination of several tools needs to support batch ingestion patterns (in other words, moving bulk data at different time intervals) and real-time streaming (moving data as sensor data or clickstreams in real time).

+   **Data preprocessing capability:** The ingested data might need to be preprocessed before it lands in the target store. So, consider tools with either built-in processing capability or those that integrate with external processing capability.

+   **Security:** The tools need to provide security mechanisms for both authentication and authorization.
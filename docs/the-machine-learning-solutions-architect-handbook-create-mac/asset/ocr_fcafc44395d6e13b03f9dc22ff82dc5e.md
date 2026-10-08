# Data serving for client consumption

The central data management platform needs to provide different methods, such as APIs or Hive metastore-based methods, for online access of the data. Also, consider data transfer tools to support data movement from the central data management platform to other data-consuming environments for different data consumption patterns. Consider tools that have built-in data serving capabilities or that can be easily integrated with external data serving tools.

There are several serving patterns for supplying data to data science environments. Let's discuss the following two data access patterns.

# Consumption via API

With this pattern, the consumption environments/applications can pull data directly from the data lake using Hive metastore-compliant tools or through direct access to S3. Amazon services such as Amazon Athena (a big data query tool), Amazon EMR (a big data processing tool), and Amazon Athena Redshift Spectrum (a feature of Amazon Redshift are used for querying data lake data indexed in Glue catalogs). This pattern is good when you don't need to make a copy of the data and only need to select a subset of the data as part of the downstream data processing tasks.

# Consumption via data copy

With this pattern, a subset of the data in the data lake is copied to the storage of the consumption environment for different processing and consumption needs. The more recent data can be loaded into Amazon Redshift in an analytics environment or delivered to S3 buckets owned by a data science environment.

# Data pipeline

Data pipelines automate the process of data movement and transformation. For example, you might need to build a data pipeline that ingests data from the source, performs validation and cleansing, enriches the dataset with new data and transformation, and then performs feature engineering and creates the training/validation/testing dataset for the ML model training and validation tasks. There are various workflow for building data pipelines, and many data management tools come with built-in data pipeline features.
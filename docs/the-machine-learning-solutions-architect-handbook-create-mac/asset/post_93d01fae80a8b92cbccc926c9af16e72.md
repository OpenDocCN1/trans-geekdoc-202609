
Specifically, we will have the following main sections in the chapter:

- Data management considerations for ML
- Data management architecture for ML
- Hands-on exercise - data management for ML

## Technical requirements

In this chapter, you will need access to an AWS account and AWS services such as Amazon S3, Amazon Lake Formation, AWS Glue, and AWS Lambda. If you do not have an AWS account, follow the official AWS website's instructions to create an account.

## Data management considerations for ML

Data management is a broad and complex topic. Many organizations have dedicated data management teams and organizations to manage and govern the various aspects of a data platform. Traditionally, the main focus of data management has been meeting the needs of transactional systems or analytics systems. With the growing adoption of ML solutions, there are new business and technology considerations for data management platforms.

To understand where data management intersects with the ML workflow, let's bring back the ML life cycle, as shown in the following figure:

![](img/bd21298357d8484151447cff0b2f138b_112_0.png)

Figure 4.1 – Intersection of data management and the ML life cycle

Data management considerations intersects with the ML life cycle in three stages: data understanding and preparation, model training and evaluation, and model deployment.

During the data understanding and preparation stage, data scientists will need to identify data sources that contain datasets for the tasks to perform exploratory data analyses, such as data statistics, the correlation between the different features, and distribution of data samples, to understand the dataset. You also need to prepare the data for model training and validation, which would normally include the following:

- Data validation to detect errors and verify the data quality (for example, data range, data distribution, data types, or missing/null values)
- Data cleaning to fix the data errors
- Data enrichment to generate new signals through the joining of different datasets and data transformation

The data management capabilities required during this stage mainly include the following:

- The ability to search for curated data using various metadata such as dataset name, dataset description, field name, and data owner
- The ability to access both raw and processed datasets for exploratory data analysis.
- The ability to run queries against the selected dataset to get details, such as statistical details, data quality, and data samples
- The ability to retrieve data from the data management platform to a data science experimentation or model building environment for further processing and engineering
- The ability to run data processing against a large dataset

During the model training and validation stage, data scientists will need to create a training and validation dataset for formal model training. The data management capabilities required for this stage include the following:

- Data processing capabilities and an automated workflow to process raw/curated datasets into training/validation datasets of different formats for model training
- A data repository for storing and managing the training/validation datasets and their versioning
- The ability to serve the training/validation dataset to the model training infrastructure to train models

During the model deployment stage, the trained models will be used to serve predictions. The data management capabilities required for this stage include the following:

- Serving data needed for the feature processing as part of the input data when invoking the deployed models
- Serving pre-computed features as part of the inputs when invoking the deployed models

Unlike traditional data access patterns for building transactional or business intelligence (BI) solutions where developers can work with non-production data in lower environments for development purposes, data scientists need access to production data for model developments.

Now, we have discussed the considerations for ML data management. Next, let's deep dive into the data management architecture for ML.

## Data management architecture for ML

Depending on the scope of your ML initiatives, you may want to consider different data management architecture patterns to support them.

For small-scale ML projects with limited data scope, team size, and cross-functional dependencies, consider purpose-built data pipelines that meet the project's specific needs. For example, suppose you only need to work with structured data from an existing data warehouse and a dataset from the public domain. In that case, you want to consider building a simple data pipeline that extracts the required data from the data warehouse and the public domain to a storage location owned by the project team as a needed schedule for further analysis and processing. The following figure shows a simple data management flow to support a small-scope ML project:

![](img/bd21298357d8484151447cff0b2f138b_115_0.png)

Figure 4.2 – Data architecture for ML project with limited scope

For large-scale ML initiatives, the data management architecture is very similar to analytics. A data lake is usually adopted where data management works with structured, semi-structured, and unstructured data for different ML tasks, where data lake is usually the core. The main purpose of the data lake is to bring different data silos into a single central repository for central data management and data access. The following figure shows a logical data management architecture which consists of several key components: data ingestion, data storage, data processing, data catalog, data security, and data access:

![](img/bd21298357d8484151447cff0b2f138b_115_1.png)

Figure Enterprise data management

Next, let's discuss each of the key components in detail and what data management architecture looks like when built with native services.

## Data storage and management

ML workloads require data of different formats from many sources, and the size of the dataset can be very large, especially when dealing with unstructured data. Cloud object storage, such as Amazon S3 or Hadoop Distributed File System (HDFS) on Hadoop cluster, is usually used as the storage medium for data. Functionally, you can think of cloud object storage as a file system where different formats can be stored. The files can also be organized by folder-like prefixes inside the object to help with the organization. Also, note that prefixes are not physical folder structures. It is called object storage because each file is an independent object. Each object is bundled with metadata, and it is assigned with a unique identifier. Object storage is usually known for unlimited storage capacity, API-based access, and low cost.

To effectively manage large volumes of data in cloud object storage medium, a data lake architecture backed by cloud object storage is the recommended way to centralize data management and data access. Depending on the scope, the data lake can be scoped for the entire enterprise or individual line of business. A data lake is meant to store unlimited amounts of data and manage them in different lifecycle stages, such as raw data, transformed data, curated data, and ML features. The data lake should be organized by different zones. For example, a landing zone should be established for the initial data ingestion from different sources. After data pre-processing and data quality management, the data can be moved to the raw data zone. Data in the raw data zone can be further transformed and processed to meet different business and downstream consumption needs. To further ensure the reliability of the dataset for usage, the data can be curated and stored in the curate data zone. For ML tasks, ML features often need to be pre-computed and stored in an ML feature zone for reuse purposes.

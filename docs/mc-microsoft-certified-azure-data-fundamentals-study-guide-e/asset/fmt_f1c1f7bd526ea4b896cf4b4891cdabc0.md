
# Azure Databricks

Azure Databricks is a fully managed, cloud-based data platform that allows data engineers to build enterprise-grade Spark-powered applications. Databricks was built by the same team that built Apache Spark and provides a highly optimized version of the open-source version of the Spark runtime. Azure Databricks is a specific implementation of Databricks that includes native integration with a variety of Azure-based storage such as ADLS, Azure Blob Storage, Azure Synapse Analytics, Azure SQL Database, and Azure Cosmos DB. Azure Databricks provides a similar mechanism to decoupling compute from storage as Azure HDInsight but has a few key advantages. For one, Azure Databricks provides native integration with Azure Active Directory for identity and access management. Azure Databricks also provides easier ways to manage clusters by letting data engineers manually pause clusters or set an auto-shutdown after being idle for a fixed amount of time. Clusters can also be set to auto-scale to support different workload sizes.

# Azure Synapse Analytics

Azure Synapse Analytics is a comprehensive data analytics platform that includes tools for data ingestion, transformation, exploration, and presentation. For the purposes of this section, we will focus on the three tools that can be used for the load and transform phases: dedicated SQL pools, serverless SQL pools, and Apache Spark pools.

## Dedicated SQL pools

Dedicated SQL pools, formerly known as Azure SQL Data Warehouse, store data in relational tables with columnar storage. A dedicated SQL pool can scale up or down depending on how large the workload is and can be paused when it's not being used. Data engineers can choose to virtualize data that is stored in object storage with either PolyBase or the `COPY` statement. PolyBase uses external tables to define and access the data in Azure object storage. PolyBase requires the creation of a few external objects to be able to read data. These include an external data source that points to the data's location in either ADLS or Azure Blob Storage, an external file format that defines how the data is formatted, and finally the actual external table definition. The `COPY` statement is a newer command for loading data into a dedicated SQL pool. It simplifies the load process by requiring only a single T-SQL statement that needs to be run instead of needing to create multiple database objects. It also includes some additional features to what PolyBase offers. Going forward, the `COPY` statement should be used to load data from ADLS and Azure Blob Storage to a dedicated SQL pool.

## Serverless SQL pool

Serverless SQL pool is an interactive service that allows developers to query data in ADLS or Azure Blob Storage. It is a distributed data processing system, built for large-scale data explorations. There is no infrastructure to set up or clusters to maintain since it is serverless. A default endpoint for a serverless SQL pool is provisioned for every Azure Synapse Analytics workspace that is deployed. Data engineers and data analysts can use the `OPENROWSET` function to query files in Azure object storage and can create external tables or views to maintain the structure of the data for later usage. Serverless SQL pools support T-SQL for users querying and processing data.

## Apache Spark pools

Apache Spark pools allow data engineers to deploy Spark clusters using the open-source version of Spark to process large volumes of data.

Each of these technologies is an MPP system and is designed to handle big data scenarios. The key advantage of using an MPP technology like the ones just discussed for big data scenarios is that once the data is loaded, they will break the data down into smaller partitions and distribute the processing of the partitions across multiple machines in parallel. Instead of one job processing a mammoth sized dataset, transformations can occur in parallel on smaller subsets of the data, resulting in more efficient processing of the data. For more information on Azure HDInsight, Azure Databricks, and Azure Synapse Analytics and to better understand when to use which one or how to use them in tandem, see [Chapter 5](#c05.xhtml).

# Describe Analytics Techniques

While it is important to spend considerable time planning and developing data processing pipelines, it is vital not to forget about the questions that drove the solution to be built in the first place. Being able to answer questions like the following is critical to the success of a business: What has happened? Why did certain events happen? What will happen? What should we do? and What might happen if different variables change?. Knowing how to answer these questions can help businesses understand their past successes and failures and predict what actions they should take in the future. These questions can be answered using the five types of analytics techniques, telling the story of a business's past, present, and future.

The five types of analytics include descriptive, diagnostic, predictive, prescriptive, and cognitive analytics. Each type of analytics represents a different stage of an organization's analytics maturity. For example, descriptive analytics techniques are based on decades of best practices that are easier to implement than prescriptive analytics but do not provide as much value. The relationship between the value provided by an analytics technique and its implementation complexity is known as the Analytics Maturity Model. This is illustrated in [Figure 1.17](#c01.xhtml#c01-fig-0017).

![FIGURE 1.17 Analytics Maturity Model](images/c01f017.png)

[FIGURE 1.17](#c01.xhtml#R_c01-fig-0017) Analytics Maturity Model

## Descriptive

Descriptive analytics use historical data to answer questions about what has happened to the business. This is a great first step for conducting statistical analysis as it informs decision makers of any trends, data distribution, and if there are any outliers in the data. Key performance indicators (KPIs) allow analysts to summarize large datasets to track the success and failure of key objectives. This type of analysis is reactive and is typically the first analysis technique used by organizations making decisions based on data.

Data used for descriptive analytics is typically gathered and persisted in a central repository, such as a data warehouse. Well-designed data warehouses make it easy for OLAP models and BI tools to analyze performance metrics against a variety of scenarios. An example of descriptive analytics is generating reports to provide a view of an organization's sales data.

## Diagnostic

Diagnostic analytics use historical data to answer questions about why different events have happened. While descriptive analytics use historical data to display past results, diagnostic analytics take this a step further by determining the root cause behind those results. This is the first technique that leverages machine learning to provide insights. Examples of diagnostic analytics include drilling down to focus on a particular facet of data, anomaly detection, data mining to get information from a massive set of data, and correlation analysis to pinpoint cause-and-effect relationships.

## Predictive

Predictive analytics use historical data to build statistical and machine learning models to forecast what will happen in the future. This is the first type of analytics in the Analytics Maturity Model that answers questions regarding a business's future. Techniques such as neural networks, decision trees, and regression models allow predictive analytics solutions to make recommendations on the following scenarios:

*   Whether or not a customer will leave for a competitor. Customer churn models use past trends to make predictions on the risk of a customer leaving. These models can help organizations make decisions on how to preemptively maintain high-risk customers' business.

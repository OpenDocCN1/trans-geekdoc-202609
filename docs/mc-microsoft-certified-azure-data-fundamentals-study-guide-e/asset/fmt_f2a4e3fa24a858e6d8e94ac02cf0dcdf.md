
# Mapping Data Flows

ADF gives data engineers the option to build no-code transformation pipelines with the use of mapping data flows. These are very similar to data flow activities in SSIS, giving data engineers the ability to create transformation activities with a GUI. The benefit of a no-code solution like this is that the code performing the transformations and the compute running the code is obfuscated from the data engineer. This can greatly improve operational productivity by allowing engineers to purely focus on implementing business logic instead of optimizing code and compute infrastructure. Just as with transformation activities that are hosted on external compute services, ADF can pass static parameters or results from previously executed activities as parameters to mapping data flows to dynamically transform data.

# Power Query

Previously known as wrangling data flows, ADF allows data engineers to perform no-code transformations on data using Power Query. Power Query is a native component of Power BI and gives analysts the ability to perform transformation activities in a scalable manner. Power Query in ADF enables citizen data analysts to create their own pipelines in ADF without needing to know how to build sophisticated data engineering pipelines.

# SSIS

Organizations have been building BI solutions for many years now, and if their solution involved SQL Server, then there is probably an SSIS component involved. Rebuilding existing SSIS with ADF pipelines could be very time consuming if the existing SSIS footprint is sophisticated. This can be a blocker for organizations migrating to Azure. To alleviate these concerns, customers can choose to migrate their SSIS projects to ADF. Data engineers can use the `Execute SSIS Package` activity in their data pipelines as singleton activities or chained to other ADF native activities. Running an SSIS project in ADF requires the use of a special compute infrastructure known as the Azure-SSIS integration runtime to run them. [Chapter 5](#c05.xhtml) will discuss the Azure-SSIS integration runtime and other types of runtimes in further detail.

# Load

The last phase of an ETL process involves loading the transformed data to a destination data model. This data model can be a data warehouse such as Azure Synapse Analytics or Azure SQL Database, a database such as Azure Cosmos DB that serves highly distributed web applications, or an object store such as ADLS that is used as the golden copy of data for machine learning activities. This phase can also be handled by GUI-based tools such as ADF or custom code solutions.

Data can be loaded to a destination data store using a few different loading patterns. Incremental or differential loads involve adding new data or updating existing data with new values. This can reduce the amount of time it takes to load newly transformed data to the destination data store, allowing consumers of the data to analyze the new data as quickly as possible. Sometimes there is a need to load the destination data store with the entire dataset, requiring an erasure of the existing data store's data. For these use cases, it can be useful to have a staging table in the destination data store to serve as an intermediary between the final transformed copy of the data and production tables being analyzed. Since the staging tables are the tables being truncated, consumers would not experience any downtime from missing data. New records can be added to the production table through a process called partition switching.

Relational database tables that are loaded with data processed by an ETL pipeline must have their schemas prebuilt. Not considering the structure of a table's existing schema can result in load errors stemming from mismatched data types and incorrect column names. This requirement to shape data so that it conforms to a predefined schema is known as `schema-on-write`.

# Control Flows and Data Flows

Many ETL tools employ two methods for orchestrating data pipelines. Tasks that ensure the orderly processing of data processing activities are known as `control flows`. Data processing activities are referred to as `data flows` and can be executed in sequence from a control flow. Data engineers that use ADF to orchestrate their data pipelines can use control flows to manage the processing sequence of their data flows.

Control flows are used to enforce the correct processing order of data movement and data transformation activities. Using precedence constraints, control flows can dictate how pipelines proceed if a task succeeds or fails. Subsequent tasks do not begin processing until their predecessors complete. Examples of control flow operations in ADF include Filter, ForEach, If Condition, Set Variable, Until, Web, and Wait activities. ADF also allows engineers to run entire pipelines within a pipeline after an activity has finished with the `Execute Pipeline` control flow activity. [Figure 1.12](#c01.xhtml#c01-fig-0012) shows a simple control flow in ADF, where the Lookup task is retrieving table metadata from a SQL Server database that will be passed to a set of Copy activities to migrate those tables to a data warehouse hosted in Azure Synapse Analytics.

![FIGURE 1.12 ADF control flow](images/c01f012.png)

[FIGURE 1.12](#c01.xhtml#R_c01-fig-0012) ADF control flow

This control flow includes outcomes for successful lookups of table metadata and failures. If metadata is retrieved successfully, then the next step will be a ForEach loop that includes data movement tasks that will migrate each SQL Server table successfully retrieved to Azure Synapse Analytics. If the Lookup task fails for whatever reason, then the next step will be a Web activity that will send an email alerting an administrator of the failure.

Another example of a control flow is the order in which different mapping data flows are executed. Using the `Data Flow` activity, data engineers can chain together multiple mapping data flows to process data in the correct order. [Figure 1.13](#c01.xhtml#c01-fig-0013) illustrates an example of a control flow that executes a series of data flows sequentially and in parallel.

![FIGURE 1.13 Ordering data flow processing with a control flow](images/c01f013.png)

[FIGURE 1.13](#c01.xhtml#R_c01-fig-0013) Ordering data flow processing with a control flow

This pipeline begins by inserting new State fields followed by new geography fields in the State and geography destination tables, all the while inserting new specialty fields in parallel. Once these data flows are complete, the control flow will run a final data flow that inserts new detail fields into the destination detail table. Of course, these tasks only control what order ETL activities run in, not the underlying data transformation steps. ADF allows developers to build or edit specific mapping data flows by double-clicking their corresponding `Data Flow` control flow activity.

While control flows manage the order of operations for ETL pipelines, data flows are where the ETL magic happens. Data flows are specific tasks in a control flow and are responsible for extracting data from its source, transforming it, and loading the transformed data into the appropriate destination data stores. The output of one data flow task can be the input to the next one, and data flows without a dependency on each other can run in parallel. As mentioned in the section “Transform” earlier in this chapter, ADF can execute four types of transformation activities that can serve as data flows. This section will focus on two of those types: mapping data flows and external compute services that host custom code.

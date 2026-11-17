
## Cluster permissions (optional)

Your cluster needs permissions to access other AWS services on your behalf. For the required permissions, add "redshift.amazonaws.com". You can associate up to 10 IAM roles with this cluster. Learn more

| Available IAM roles | AWSServiceRoleForRedshift |
| Attached IAM roles | |
| Status | No IAM roles associated with this resource |

Figure 3.4 – A screenshot of an Amazon Redshift cluster's Cluster permissions section

- 13. Scroll down and click on Create Cluster. It will take a minute or two to get the cluster in the available state.

Next, you will create an IAM role.

- 14. Navigate to the AWS IAM console and select Roles in the Access Management section on the screen.

- 15. Click on the Create role button and choose Glue from the services. Click on the Next: permissions button to navigate to the next page.

- 16. Search for **AmazonS3FullAccess** and select it. Then, search for **AWSGlueServiceRole** and select it. As you are writing your data to Redshift as part of this example, select **AmazonRedshiftFullAccess**. Click on Next: Tags, followed by the Next: Review button.

- 17. Provide a name, **Glue-IAM-Role**, and then click on the **Create role** button. The role appears as shown in Figure 3.5 below and review this role before you create it.

| Role name* | Glue-IAM-Role |
| Role description | Allows Glue to call AWS services on your behalf. |
| Trusted entities | AWS service: glue.amazonaws.com |
| Policies | AmazonRedshiftFullAccess AWSGlueServiceRole AmazonS3FullAccess |

Figure 3.5 – A screenshot of the IAM role

Now, you have the input data source and the output data storage handy. The next step is to create the Glue crawler from the AWS Glue console.

- 18. Select Connections under Databases. Click on the Add connection button and complete the fields as shown here:
  - A. Connection name: glue-redshift-connection
  - B. Connection type: Amazon Redshift

- 19. Click on Next and then fill in the fields as shown here:
  - A. Cluster: redshift-glue-example
  - B. Database name: glue-dev
  - C. Username: awsuser
  - D. Password: ******** (enter the value chosen in step 10)

- 20. Click on Next and then Finish. To verify that it's working, click on Test Connection, select Glue-IAM-Role in the IAM role section, and then click Test Connection.

- 21. Go to Crawler and select Add Crawler. Provide a name for the crawler, S3-glue-crawler, and then click Next. On the Specify crawler source type page, leave everything as their default settings and then click Next.

- 22. On the Add a data store page, choose Include path option and enter s3://aws-glue-example-01/input-data/sales-records.csv.

- 23. Click Next.

- 24. Set Add another datastore to No. Click Next.

- 25. For Choose an existing IAM Role, set Glue-IAM-Role. Then, click Next.

- 26. Set Frequency to Run on demand. Click Next.

- 27. No database has been created, so click on Add database, provide a name, s3-data, click Next, and then click Finish.

- 28. Select the crawler, S3-glue-crawler, and then click on Run Crawler. Once the run is complete, you can see that there is a 1 in the Tables Added column. This means that a database, s3-data, has been created, as mentioned in the previous step, and a table has been added. Click on Tables and select the newly created table, sales_records_csv. You can see that the schema has been discovered now. You can change the data type if the inferred data type does not meet your requirements.

In this hands-on section, you learned about database tables, database connections, crawlers in S3, and the creation of a Redshift cluster. In the next hands-on section, you will learn about creating ETL jobs using Glue.

## Getting hands-on with AWS Glue ETL components

In this section, you will use the Data Catalog components created earlier to build a job. You will start by creating a job:

- 1. Navigate to the AWS Glue console and click on Jobs under the ETL section.

- 2. Click on the Add Job button and complete the fields as shown here:
  - Name: s3-glue-redshift
  - IAM role: Glue-IAM-Role (this is the same role you created in the previous section)
  - Type: Spark
  - Glue version: Spark 2.4, Python 3 with improved job start up times (Glue version 2.0)

- 3. Leave the other fields as they are and then click on Next.

- 4. Select sales_records_csv and click on Next.

- 5. Select Change Schema by default and then click Next (at the time of writing this book, machine learning transformations are not supported for Glue 2.0).

- 6. Select Create tables in your data target. Choose JDBC as the data store and glue-redshift-connection as the connection. Provide glue-dev as the database name (as created in the previous section) and then click Next.

- 7. Next comes the Output Schema Definition page, where you can choose the desired columns to be removed from the target schema. Scroll down and click on Save job and edit script.

- 8. You can now see the pipeline being created on the left-hand side of the screen and the suggested code on the right-hand side, as shown in Figure 3.6. You can modify the code based on your requirements. Click on the Run job button. A pop-up window appears, asking you to edit any details that you wish to change.

This is optional. Then, click on the Run job button:

![](img/87c29232224b00f5a8bba6a66a391700_79_0.png)

Figure 3.6 – A screenshot of the AWS Glue ETL job

- 9. Once the job is successful, navigate to Amazon Redshift and click on Query editor.

- 10. Set the database name as glue-dev and then provide the username and password to create a connection.

- 11. Select the **public** schema, and now you can query the table to see the records, as shown in Figure 3.7:

![](img/87c29232224b00f5a8bba6a66a391700_80_0.png)

Figure 3.7 – A screenshot of Amazon Redshift’s Query editor

You now understand how to create an ETL job using AWS Glue to copy the data from an S3 bucket to Amazon Redshift. You also queried data in Amazon Redshift using the query editor from the UI console. It is recommended to delete the Redshift cluster and AWS Glue job once you have completed the steps successfully. AWS creates two buckets in your account to store AWS Glue scripts and temporary results from AWS Glue. Delete these as well to save costs. You will use the data catalog created on S3 data in the next section.

In the following section, you will learn about querying S3 data using Athena.

## Querying S3 data using Athena

Athena is a serverless service designed for querying data stored in S3. It is serverless because the client doesn’t manage the servers that are used for computation:

- Athena uses a schema to present the results against a query on the data stored in S3. You define how (the way or the structure) you want your data to appear in the form of a schema and Athena reads the raw data from S3 to show the results as per the defined schema.
- The output can be used by other services for visualization, storage, or various analytics purposes. The source data in S3 can be in any of the following structured, semi-structured, or unstructured data formats: XML, JSON, CSV/TSV, AVRO, Parquet, or ORC (as well as others). CloudTrail, ELB logs, and VPC flow logs can also be stored in S3 and analyzed by Athena.
- This follows the schema-on-read technique. Unlike traditional techniques, tables are defined in advance in a data catalog, and the data’s structure is validated against the table’s schema while reading the data from the tables. SQL-like queries can be carried out on data without transforming the source data.

Now, to help you understand this, here’s an example, where you will use AWSDatacatalog created in AWS Glue on the S3 data and query them using Athena:

1. Navigate to the AWS Athena console. Select **AWSDataCatalog** from **Data source** (if you are doing this for the first time, then a **sampledb** database will be created with a table, **elb_logs**, in the AWS Glue Data Catalog).

2. Select **s3-data** as the database.

3. Click on **Settings** in the top-right corner and fill in the details as shown in **Figure 3.8** (I have used the same bucket as in the previous example and a different folder):

![](img/87c29232224b00f5a8bba6a66a391700_81_0.png)

Figure 3.8 – A screenshot of Amazon Athena's settings

4. The next step is to write your query in the query editor and execute it. Once your execution is complete, please delete your S3 buckets and AWS Glue data catalogs. This will save you money.

In this section, you learned how to query S3 data using Amazon Athena through the AWS Glue Data Catalog. You also learned how to create a schema and query data from S3. In the next section, you will learn about Amazon Kinesis Data Streams.

## Processing real-time data using Kinesis Data Streams

Kinesis is Amazon’s streaming service and can be scaled based on requirements. It has a level of persistence that retains data for 24 hours by default or optionally up to 365 days. Kinesis Data Streams is used for large-scale data ingestion, analytics, and monitoring:

- Kinesis streams can be ingested by multiple producers and multiple consumers can also read data from the streams. The following is an example to help you understand this. Suppose you have a producer ingesting data to a Kinesis stream and the default retention period is 24 hours, which means data ingested at 05:00:00 A.M. today will be available in the stream until 04:59:59 A.M. tomorrow. This data won’t be available beyond that point, and ideally, it should be consumed before it expires; otherwise, it can be stored somewhere if it’s critical. The retention period can be extended to a maximum of 365 days, at an extra cost.
- Kinesis can be used for real-time analytics or dashboard visualization. Producers can be imagined as a piece of code pushing data into the Kinesis stream, and it can be an EC2 instance, a Lambda function, an IoT device, on-premises servers, mobile applications or devices, and so on running the code.
- Similarly, the consumer can also be a piece of code running on an EC2 instance, Lambda function, or on-premises servers that know how to connect to a Kinesis stream, read the data, and apply some action to the data. AWS provides triggers to invoke a

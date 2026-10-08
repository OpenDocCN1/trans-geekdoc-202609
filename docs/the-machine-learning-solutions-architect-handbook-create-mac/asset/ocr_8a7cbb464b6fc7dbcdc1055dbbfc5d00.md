# Creating a data ingestion pipeline

With the database ready, we can now ingest data to the new database. As discussed in the previous section, there could be many different data sources as other S3 buckets, such as databases (for example, Amazon RDS), streaming (for example, social media feeds), and logs (CloudTrail). There are also many different services for building a data ingestion pipeline, such as AWS Glue, Amazon Kinesis, and AWS Lambda. In this part of the exercise, we will build an Amazon Lambda function job that will ingest data from other S3 buckets to this new database:

+   1. Create a source S3 bucket and download data files:

Let’s create another S3 bucket, called customer-data-source, to represent the data source where we will ingest the data. Now, download the sample data files from the following link:

https://github.com/PacktPublishing/The-Machine-Learning-Solutions-Architect-Handbook/tree/main/Chapter04/Archive.

Then, save it to your local machine. Extract the archived files and upload them to the customer-data-source bucket. There should be two files (customer_data.csv and churn_list.csv).

+   2. Create Lambda function:

Now, we will create the Lambda function that will ingest data from the customer-data-source bucket to the MLSA-DataLake-<your initials> bucket:

+   I. To get started, navigate to the AWS Lambda management console, click on the **Functions** link in the left pane, and click on the **Create Function** button in the right pane. Choose **Author from scratch**, then enter datalake-s3-ingest for the function name, and select **Python 3.8** as the runtime.

+   II. On the next screen, click on **Add trigger**, select **S3** as the trigger, and select the **customer-data-source** bucket as the source. For **Event Type**, choose the **Put** event and click on the **Add** button to complete the step. This trigger will allow the Lambda function to be invoked when there is an S3 bucket event, as saving a file into the bucket.
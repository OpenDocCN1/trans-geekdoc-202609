
- Data can be generated from several devices, including mobile devices or IoT, weblogs, social media, transactional data, and online games.
- This huge amount of generated data can be collected by using polling services, through API gateways integrated with AWS Lambda to collect the data, or via streams such as AWS Kinesis, AWS-managed Kafka, or Kinesis Firehose. If you have an on-premises database and you want to bring that data to AWS, then you would choose AWS DMS for that. You can sync your on-premises data to Amazon S3, Amazon EFS, or Amazon FSx via AWS DataSync. AWS Snowball is used to collect/transfer data into and out of AWS.
- The next step involves storing data. You learned about some of the services to do this in the previous chapter, such as S3, EBS, EFS, RDS, Redshift, and DynamoDB.
- Once you know your data storage requirements, an ETL job can be designed to extract-transform-load or extract-load-transform your structured or unstructured data into the format you desire for further analysis. For example, you can use AWS Lambda to transform the data on the fly and store the transformed data in S3, or you can run a Spark application on an EMR cluster to transform the data and store it in S3 or Redshift or RDS.
- There are many services available in AWS for performing an analysis on transformed data, for example, EMR, Athena, Redshift, Redshift Spectrum, and Kinesis Analytics.
- Once the data is analyzed, you can visualize it using AWS QuickSight to understand the patterns or trends. Data scientists or machine learning professionals would want to apply statistical analysis to understand data distribution in a better way. Business users use statistical analysis to prepare reports. You will learn and explore various ways to present and visualize data in Chapter 5, Data Understanding and Visualization.

What you understood from the traditional data pipeline is that ETL is all about coding and maintaining code on the servers so that everything runs smoothly. If the data format changes in any way, then the code needs to be changed, and that results in a change to the target schema. If the data source changes, then the code must be able to handle that too, and it’s an overhead. Should you write code to recognize these changes in data sources? Do you need a system to adapt to the change and discover the data for you? The answer to these questions is yes, and to do so, you can use AWS Glue. Now, you will learn why AWS Glue is so popular.

## Features of AWS Glue

AWS Glue is a completely managed serverless ETL service on AWS. It has the following features:

- It automatically discovers and categorizes your data by connecting to the data sources and generates a data catalog.
- Services such as Amazon Athena, Amazon Redshift, and Amazon EMR can use the data catalog to query the data.
- AWS Glue generates the ETL code, which is an extension to Spark in Python or Scala, which can be modified, too.
- It scales out automatically to match your Spark application requirements for running the ETL job and loading the data into the destination.

AWS Glue has the Data Catalog, and that’s the secret to its success. It helps with discovering data from data sources and understanding a bit about it:

- The Data Catalog automatically discovers new data and extracts schema definitions. It detects schema changes and version tables. It detects Apache Hive-style partitions on Amazon S3.
- The Data Catalog comes with built-in classifiers for popular data types. Custom classifiers can be written using Grok expressions. The classifiers help to detect the schema.
- Glue crawlers can be run ad hoc or in a scheduled fashion to update the metadata in the Glue Data Catalog. Glue crawlers must be associated with an IAM role with sufficient access to read the data sources, such as Amazon RDS, Redshift, and S3.

As you now have a brief idea of what AWS Glue is used for, move on to run the following example to get your hands dirty.

### Getting hands-on with AWS Glue Data Catalog components

In this example, you will create a job to copy data from S3 to Redshift by using AWS Glue. All my components were created in the us-east-1 region. Start by creating a bucket:

1. Navigate to the AWS S3 console and create a bucket. I have named the bucket aws-glue-example-01.
2. Click on Create Folder and name it input-data.
3. Navigate inside the folder and click on the Upload button to upload the sales-records.csv dataset. The data is available in the following GitHub location: https://github.com/PacktPublishing/AWS-Certified-Machine-Learning-Specialty-MLS-C01-Certification-Guide-Second-Edition/tree/main/Chapter03/AWS-Glue-Demo/input-data.

As you have the data uploaded in the S3 bucket, now create a VPC in which you will create your Redshift cluster.

4. Navigate to the VPC console by accessing the https://console.aws.amazon.com/vpc/home?region=us-east-1# URL and click on Endpoints on the left-hand side menu. Click on Create Endpoint and then fill in the fields as shown here:
   - Service Category: AWS services
   - Select a service: com.amazonaws.us-east-1.s3 (gateway type)
   - VPC: Select the Default VPC (use this default VPC in which your Redshift cluster will be created)
5. Leave the other fields as is and click on Create Endpoint.
6. Click on Security Groups from the VPC console. Give a name to your security group, such as redshift-self, and choose the default VPC drop-down menu. Provide an appropriate description, such as Redshift Security Group. Click on Create security group.
7. Click on the Actions dropdown and select Edit Inbound rules. Click on Add rule and complete the fields as shown here:
   - Type: All traffic
   - Source: Custom
   - In the search field, select the same security group (redshift-self)

8. Click on Save Rules.

Now, create your Redshift cluster.

9. Navigate to the Amazon Redshift console. Click on **Create Cluster** and complete the highlighted fields, as shown in *Figure 3.1*:

![](img/87c29232224b00f5a8bba6a66a391700_74_0.png)

Figure 3.1 – A screenshot of Amazon Redshift’s Create cluster screen

10. Scroll down and fill in the highlighted fields shown in *Figure 3.2* with your own values:

#### Database configurations

Database name (optional)
Specify a database name to create an additional database.
glue-dev
The name must be 1-64 alphanumeric characters (lowercase only), and it can't be a reserved word.

Database port (optional)
Port number where the database accepts inbound connections. You can't change the port after the cluster has been created.
5439
The port must be numeric (1150-65535).

Master user name
Enter a login ID for the master user of your DB instance.
awsuser
The name must be 1-128 alphanumeric characters, and it can't be a reserved word.

Master user password
******
☐ Show password
● The master password must be 8 - 64 characters. ● The value must contain at least one uppercase letter.
● The value must contain at least one lowercase letter. ● The value must contain at least one number.
● The master password can only contain ASCII characters (ASCII codes 33-126), except ' (single quotation mark), " (double quotation mark), /, \, or @.

Figure 3.2 – A screenshot of an Amazon Redshift cluster's Database configurations section

11. Scroll down and change the Additional configurations settings, as shown in Figure 3.3:

#### Additional configurations

These configurations are optional, and default settings have been defined to help you get started with your cluster. Turn off "Use defaults" to modify these settings now.

#### Network and security

Virtual private cloud (VPC)
This VPC defines the virtual networking environment for this cluster. Choose a VPC that has a subnet group. Only valid VPCs are enabled in the list.
Default VPC
vpc-140d146e

ℹ You can't change the VPC associated with this cluster after the cluster has been created. Learn more ↗ ×

VPC security groups
This VPC security group defines which subnets and IP ranges the cluster can use in the VPC.
Choose one or more security groups
redshift-self ×
sg-059c2134eb1a29141

Figure 3.3 – A screenshot of an Amazon Redshift cluster's Additional configurations section

12. Change the IAM permissions too, as shown in Figure 3.4:

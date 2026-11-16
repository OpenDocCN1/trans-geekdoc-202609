**NOTE** Use Amazon SageMaker Autopilot to automatically build, train, and deploy machine learning models for fraud detection.

![](bbox=[0.125, 0.165, 0.875, 0.47])

# **FIGURE 13.11:** Fraud detection architecture

To build the fraud detection architecture using AWS components shown in Figure 13.12, you must first use the Amazon CloudFormation template to instantiate an instance of Amazon SageMaker with the sample dataset and train models using that dataset.

The solution also contains an Amazon Lambda function that invokes the two Amazon SageMaker endpoints for classification and anomaly detection using the sample data.

The Amazon Kinesis Data Firehose loads the transactions into the Amazon S3, which is used to make predictions and generate new insights.
+   2. Select Roles from the left-hand menu.

+   3. Select Create role.

+   4. Select Lambda as the trusted entity.

+   5. Add the following managed policies:
+   * AmazonS3FullAccess
+   * AmazonPollyFullAccess
+   * CloudWatchFullAccess

+   6. Save the role as polly-lambda-role.

Next, you will create a Lambda function:

+   7. Navigate to Lambda > Functions > Create Function.
+   * Name the function polly-lambda
+   * Set the runtime to python 3.6.
+   * Use an existing role; that is, polly-lambda-role.

+   8. Paste the code at https://github.com/PacktPublishing/AWS-Certified-Machine-Learning-Specialty-MLS-C01-Certification-Guide-Second-Edition/tree/main/Chapter08/Amazon%20Rekognition%20Demo/lambda_code into your Lambda function and check its progress in the CloudWatch console. You will be using the start_speech_synthesis_task API from Amazon Polly for this code; it is an asynchronous synthesis task.

+   9. Scroll down and in the Basic Settings section, change Timeout to 59 sec, as shown in Figure 8.6, and click Save:

# IMPORTANT NOTE

The default is 3 seconds. Since this is an asynchronous operation, any retried attempts will create more files.
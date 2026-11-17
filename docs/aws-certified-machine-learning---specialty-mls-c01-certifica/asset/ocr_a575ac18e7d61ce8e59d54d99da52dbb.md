+   - The Labels API's response will identify real-world entities within an image through the DetectLabels API. These labels include city, town, table, home, garden, animal, pets, food, drink, electronics, flowers, and more. The entities are classified based on their confidence score, which indicates the probability that a given prediction is correct — the higher the score, the better. Similarly, you can use the DetectText API to extract the text in an image. Amazon Rekognition may detect multiple lines based on the gap between words. Periods do not represent the end of a line.
+   
+   - Amazon Rekognition can be integrated with AWS Kinesis Video Stream, AWS S3, and AWS Lambda for seamless and affordable image and video analysis. With the AWS IAM service, Amazon Rekognition API calls can easily be secured and controlled.
+   
+   - Low cost: you only pay for the images and videos that are analyzed.
+   
+   - Through AWS CloudTrail, all the API calls for Amazon Rekognition can be captured as events. It captures all calls made from the console, the CLI, or code calls for APIs, which further enables the user to create Amazon SNS notifications based on CloudTrail events.
+   
+   - You can create a VPC endpoint policy for specific API calls to establish a private connection between your VPC and Amazon Rekognition. This helps you leverage enhanced security. As per the AWS Shared Responsibility Model, AWS takes care of the security of the infrastructure and software, and you have to take care of the security of your content in the cloud.

# Getting hands-on with Amazon Rekognition

In this section, you will learn how to integrate AWS Lambda with Amazon Rekognition to detect the labels in our image (uploaded at https://github.com/PacktPublishing/AWS-Certified-Machine-Learning-Specialty-MLS-C01-Certification-Guide-Second-Edition/tree/main/Chapter08/Amazon%20Rekognition%20Demo/images) and print the detected objects in the CloudWatch console. You will use the `detect_labels` API from Amazon Rekognition in the code.

You will begin by creating an IAM role for Lambda:

+   1. Navigate to the IAM console page.
+   
+   2. Select Roles from the left-hand menu.
+   
+   3. Select Create role.
+   
+   4. Select Lambda from the Choose a use case section.
+   
+   5. Add the following managed policies:
+   
+      - AmazonS3ReadOnlyAccess
+   
+      - AmazonRekognitionFullAccess
+   
+      - CloudWatchLogsFullAccess
+   
+   6. Name the role rekognition-lambda-role:

## AWS Application Services for AI/ML

In this chapter, you will learn about the AWS AI services for building chatbots, advanced text analysis, document analysis, transcription, and so on. This chapter has been designed in such a way that you can solve different use cases by integrating AWS AI services and get an idea of how they work. AWS is growing every day, and they are adding new AI services regularly.

In this chapter, you will approach different use cases programmatically or from the console. This will help you understand different APIs and how to use them. You will use S3 for storage and AWS Lambda to execute any code. The examples in this chapter are in Python, but you can use other supported languages such as Java, Node.js, .NET, PowerShell, Ruby, and so on.

You will cover the following topics:

- Analyzing images and videos with Amazon Rekognition
- Text to speech with Amazon Polly
- Speech to text with Amazon Transcribe
- Implementing natural language processing with Amazon Comprehend
- Translating documents with Amazon Translate
- Extracting text from documents with Amazon Textract
- Creating chatbots on Amazon Lex
- Time series forecasting with Amazon Forecast

## Technical requirements

All you need for this chapter is an AWS account.

You can download the code examples for this chapter from GitHub at

https://github.com/PacktPublishing/AWS-Certified-Machine-Learning-Specialty-MLS-C01-Certification-Guide-Second-Edition/tree/main/Chapter08.

## Analyzing images and videos with Amazon Rekognition

If you need to add powerful visual analysis to your applications, then Amazon Rekognition is the service to choose. Rekognition Image lets you easily build powerful applications to search, verify, and organize millions of images. It lets you extract motion-based context from stored or live stream videos, and helps you analyze them. Rekognition Video also allows you to index metadata such as objects, activities, scenes, celebrities, and faces, making video searches easy. Rekognition Image uses deep neural network models to detect and label numerous objects and scenes in your images. It helps you capture text in an image, a bit like **Optical Character Recognition (OCR)**. A perfect example is a T-shirt with quotes on it. If you were to take a picture of one and ask Amazon Rekognition to extract the text from it, it would be able to tell you what the text says. You can also perform celebrity recognition using Amazon Rekognition. Somebody who is not a celebrity won’t use the celebrity recognition API for their face; instead, they will use the face comparison API.

The official documentation, available at [https://aws.amazon.com/rekognition/faqs/](https://aws.amazon.com/rekognition/faqs/), states the following:

> "With Rekognition Image, you only pay for the images you analyze and the face metadata you store. You will not be charged for the compute resources if, at any point of time, your training fails."

Some common uses of Amazon Rekognition include the following:

- Image and video analysis
- Searchable image library
- Face-based user verification
- Sentiment analysis
- Text in image
- Facial recognition
- Image moderation
- Search index for video archives
- Easy filtering of explicit and suggestive content in videos
- Examples of explicit nudity – sexual activity, graphical nudity, adult toys, and so on
- Examples of suggestive content – partial nudity, swimwear or underwear, and so on

## Exploring the benefits of Amazon Rekognition

Here are some of the benefits of using Amazon Rekognition:

- AWS manages the infrastructure it runs on. In short, just use the API for your image analysis. You need to only focus on building and managing your deep learning pipelines.

With or without knowledge of image processing, you can perform image and video analysis just by using the APIs provided in Amazon Rekognition, which can be used for any application or service on several platforms.

- The Labels API's response will identify real-world entities within an image through the DetectLabels API. These labels include city, town, table, home, garden, animal, pets, food, drink, electronics, flowers, and more. The entities are classified based on their confidence score, which indicates the probability that a given prediction is correct — the higher the score, the better. Similarly, you can use the DetectText API to extract the text in an image. Amazon Rekognition may detect multiple lines based on the gap between words. Periods do not represent the end of a line.

- Amazon Rekognition can be integrated with AWS Kinesis Video Stream, AWS S3, and AWS Lambda for seamless and affordable image and video analysis. With the AWS IAM service, Amazon Rekognition API calls can easily be secured and controlled.

- Low cost: you only pay for the images and videos that are analyzed.

- Through AWS CloudTrail, all the API calls for Amazon Rekognition can be captured as events. It captures all calls made from the console, the CLI, or code calls for APIs, which further enables the user to create Amazon SNS notifications based on CloudTrail events.

- You can create a VPC endpoint policy for specific API calls to establish a private connection between your VPC and Amazon Rekognition. This helps you leverage enhanced security. As per the AWS Shared Responsibility Model, AWS takes care of the security of the infrastructure and software, and you have to take care of the security of your content in the cloud.

## Getting hands-on with Amazon Rekognition

In this section, you will learn how to integrate AWS Lambda with Amazon Rekognition to detect the labels in our image (uploaded at https://github.com/PacktPublishing/AWS-Certified-Machine-Learning-Specialty-MLS-C01-Certification-Guide-Second-Edition/tree/main/Chapter08/Amazon%20Rekognition%20Demo/images) and print the detected objects in the CloudWatch console. You will use the `detect_labels` API from Amazon Rekognition in the code.

You will begin by creating an IAM role for Lambda:

1. Navigate to the IAM console page.
2. Select Roles from the left-hand menu.
3. Select Create role.
4. Select Lambda from the Choose a use case section.
5. Add the following managed policies:
   - AmazonS3ReadOnlyAccess
   - AmazonRekognitionFullAccess
   - CloudWatchLogsFullAccess
6. Name the role rekognition-lambda-role:

![](img/87c29232224b00f5a8bba6a66a391700_203_0.png)

### Figure 8.1 – The Create role dialog

Next, you will create a Lambda function.

7. Navigate to the AWS Lambda console page.
8. Select **Create function**.
9. Create a function:
   - Select **Author from scratch**.
   - Give the function a name, such as `lambda-rekognition`.
   - Choose **Python 3.6** from the **Runtime** dropdown.
   - Select **Use an existing role**. Add the name of the role you created previously; that is, `rekognition-lambda-role`:

### Basic information

### Figure 8.2 – Creating the Lambda function

10. Enter the following code in lambda_function.py:

```
from __future__ import print_function
import boto3
def lambda_handler(event, context):
    print("=======lambda_handler started=======")
    # read the bucket name (key) from the event
    name_of_the_bucket=event['Records'][0]['s3']['bucket']['name']
    # read the object from the event
    name_of_the_photo=event['Records'][0]['s3']['object']['key']
    detect_labels(name_of_the_photo,name_of_the_bucket)
    print("Labels detected Successfully")
def detect_labels(photo, bucket):
    client=boto3.client('rekognition')
    response=client.detect_labels(Image={'S3Object':{'Bucket':bucket,'Name':photo}})
    print('Detected labels for ' + photo)
    print('===================================================')
    for label in response['Labels']:
        print ("Label: " + label['Name'])
        print ("Confidence: " + str(label['Confidence']))
        print ("Instances:")
        for instance in label['Instances']:
            print (" Bounding box")
            print ("Top:" + str(instance['BoundingBox']['Top']))
            print ("Left:" + str(instance['BoundingBox']['Left']))
```


4. Random search is deterministic.

8. How does regularization help in addressing the issue of overfitting in machine learning models?

    1. By increasing the model’s complexity
    2. By adding a penalty to the loss function to constrain model parameters
    3. By removing training data
    4. By increasing the number of training epochs

9. Which of the following is a common method to monitor and debug distributed training jobs in Amazon SageMaker?

    1. Using Jupyter Notebooks
    2. Enabling Spot Instances
    3. Implementing Amazon SageMaker Debugger
    4. Disabling Auto Scaling

10. In model evaluation, what does a high AUC-ROC score indicate for a classification model?

     1. The model has a high number of false positives.
     2. The model has a strong ability to discriminate between classes.
     3. The model is likely overfitting the training data.
     4. The model has a high number of false negatives.

# Chapter 6

Model Deployment and Orchestration

![](images/chaptersquare.png)

## AWS Model Deployment Services

In the previous chapter, you learned how to train and how to evaluate the performance of your model. You learned different training approaches to ensure that your chosen model has sufficient amounts of data to learn patterns and relationships between features and labels for supervised ML problems, as well as how it can uncover hidden structures and patterns in unsupervised ML problems.

Now, it’s time to move forward and explore how to deploy these models effectively. Model deployment is the integration of your model and all its resources into a production environment so it can be used to generate predictions, or *inferences*.

In this chapter, we will delve into the *Deploy Model* and *Derive Inference* phases, as illustrated in [Figure 6.1](#c006.xhtml#c06-fig-1). These phases are essential for delivering the insights and predictions your model is capable of.

![FIGURE 6.1 The machine learning lifecycle.](images/c06f001.png)

[FIGURE 6.1](#c006.xhtml#rc06-fig-1) The machine learning lifecycle.

Throughout the chapter we will use the term “ML app” to denote the application responsible for producing inferences in response to inference requests. This application will receive inference requests as input, will pass this data to the model, and will eventually return inference responses upon receiving an output from the model.

I used the term *eventually* to indicate that the response produced by the ML app (after consuming the model) will be returned to the requestor “one way or the other.” This may happen immediately (in real time), in near real time (with a few seconds delay), or after an undetermined period of time. In the last scenario, the processing of the inferences usually occurs in batches, because the requestor does not expect an immediate response. As a result, the period it takes for the ML app to return inferences depends on—among other factors—the batch size (how many inference requests are being batched?) and the amount of data for each inference request, also referred to as the *payload*.

Depending on your specific use case, you may choose to leverage Amazon AI Services that use pretrained models and obtain inferences by invoking directly their APIs, or you may choose to expose your model with an endpoint provided by Amazon SageMaker, now referred to as Amazon SageMaker AI.

Either way, it is critical that the deployment approach you pursue complies with well-architected best practices. This means ensuring that your organization’s teams support efficient development and workload management, protecting your identities, data, infrastructure, and applications with robust security measures and maintaining the expected levels of reliability metrics. Additionally, it’s essential to use resources efficiently to meet system requirements, minimize costs by avoiding unnecessary expenses, and adopt sustainable practices to reduce your environmental impact. By adhering to these principles of operational excellence, security, reliability, performance efficiency, cost optimization, and sustainability, you can build a performant, robust, secure, and cost-effective model deployment that aligns with your organizational goals and environmental responsibilities.

Let’s start the chapter with deployment techniques for Amazon AI services.

### Deploying AI Services

Although Amazon SageMaker AI is often used to build, train, and deploy custom ML models, it also integrates seamlessly with several fully managed AI services provided by AWS. As you learned in [Chapter 4](#c004.xhtml#c004), these services offer pretrained models that can be easily incorporated into your applications via API calls.

This section explores how these AI services can be effectively deployed with your ML applications.

#### Amazon Rekognition

Amazon Rekognition offers pretrained models for image and video analysis. Deploying Amazon Rekognition involves making API calls to the service to analyze images and videos for objects, faces, text, and scenes. Amazon SageMaker AI can be used to orchestrate these API calls within your ML workflows, ensuring seamless integration with your applications. The orchestration aspect is a key requirement of the exam and will be covered in detail at the end of this chapter. This approach allows for scalable image and video processing without needing direct access to the underlying models.

The following snippet provides an example of how to use Amazon Rekognition:

```
import boto3
        
client = boto3.client('rekognition')
        
response = client.detect_labels(
    Image={'S3Object': {'Bucket': 'your-bucket-name', 'Name': 'your-image.jpg'}},
    MaxLabels=10,
    MinConfidence=75
)
        
for label in response['Labels']:
    print(f"Label: {label['Name']}, Confidence: {label['Confidence']}")
```

To get started with Amazon Rekognition using Python, you’ll first need to set up your environment by installing and configuring the AWS SDK for Python, known as `boto3`. Amazon SageMaker Studio Code Editor comes with `boto3` preinstalled.

Once your environment is ready, import the `boto3` library, and create a client for the Rekognition service using the statement `client = boto3.client('rekognition')`. Next, prepare your data by uploading the images or videos you want to analyze to an Amazon S3 bucket. With your data in place, you can call the `detect_labels` API method to analyze the images and identify objects, scenes, and activities. The `Image` parameter specifies the S3 bucket and file name, whereas the `MaxLabels` and `MinConfidence` parameters define the maximum number of labels to return and the minimum confidence level for the detected labels. The API call returns a `response` object, which includes the identified labels and their corresponding confidence scores (`response['Labels']`), which you can print or use in your application for further processing. With the provided code you learned how to use Amazon Rekognition to analyze an image stored in an S3 bucket and print the detected labels and their confidence scores.

For more information, visit `https://docs.aws.amazon.com/rekognition/latest/APIReference/Welcome.html`.

#### Amazon Textract

Amazon Textract provides pretrained models for extracting text and data from scanned documents. To use Amazon Textract, create a client using the statement `client = boto3.client('textract')`. Key methods include `analyze_document`, `detect_document_text`, and `get_document_analysis` for processing documents. Here’s an example of using the `analyze_document` method:

```
import boto3
        
client = boto3.client('textract')
        
response = client.analyze_document(
    Document={'S3Object': {'Bucket': 'your-bucket-name', 'Name': 'your-document.pdf'}},
    FeatureTypes=['TABLES', 'FORMS']
)
        
for block in response['Blocks']:
    if block['BlockType'] == 'LINE':
        print(block['Text'])
```

For more information, visit:

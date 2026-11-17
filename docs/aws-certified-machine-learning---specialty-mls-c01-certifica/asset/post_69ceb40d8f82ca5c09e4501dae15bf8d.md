
```
'HTTPHeaders': {'x-amzn-requestid': '74ca4afd-5844-47d8-9664-3660a26965e4', 'content-type': 'application/json', 'content-length': '471', 'date': 'Thu, 24 Sep 2020 18:50:57 GMT', 'RetryAttempts': 0},
'SynthesisTask': {'Engine': 'standard', 'TaskId': '57548c6b-d21a-4885-962f-450952569dc7', 'TaskStatus': 'scheduled', 'OutputUri': 'https://s3.us-east-1.amazonaws.com/polly-test-baba/output-audio/.57548c6b-d21a-4885-962f-450952569dc7.mp3',
'CreationTime': datetime.date(2020, 9, 24), 'RequestCharacters': 59, 'OutputFormat': 'mp3', 'TextType': 'text',
'VoiceId': 'Aditi', 'LanguageCode': 'en-GB'}})
```

The logs sample is shown in Figure 8.8:

| Log Entry | Details |
| :--- | :--- |
| 2020-09-24T19:07:04.054+01:0... | Task Status is: scheduled |
| 2020-09-24T19:07:04.094+01:0... | Task Status is: scheduled |
| 2020-09-24T19:07:04.105+01:0... | Task Status is: scheduled |
| 2020-09-24T19:07:04.184+01:0... | Task Status is: scheduled |
| 2020-09-24T19:07:04.254+01:0... | Task Status is: inProgress |
| 2020-09-24T19:07:04.497+01:0... | Task Status is: completed |
| 2020-09-24T19:07:04.534+01:0... | Audio File Saved Successfully |
| 2020-09-24T19:07:04.553+01:0... | END RequestId: 1d57151b-8462-434c-89b4-9b318c2437d8 |
| 2020-09-24T19:07:04.553+01:0... | REPORT RequestId: 1d57151b-8462-434c-89b4-9b318c2437d8 Duration: 15832.73 ms Billed Duration: |
| | No newer events at this moment. Auto retry paused. Resume |

Figure 8.8 – The logs in the CloudWatch console

16. It will create output in MP3 format, as shown in Figure 8.9. Download and listen to it:

![](img/87c29232224b00f5a8bba6a66a391700_212_0.png)

Figure 8.9 – The output file that was created in the S3 bucket

## IMPORTANT NOTE

The most scalable and cost-effective way for your mobile apps or web apps is to generate an AWS pre-signed URL for S3 buckets and provide it to your users. These S3 Put events asynchronously invoke downstream AI workflows to generate results and send a response to the end users. Many users can be served at the same time through this approach, and it may increase performance and throughput.

In this section, you learned how to implement text to speech. In the next section, you will learn about Amazon Transcribe, a speech-to-text AI service.

## Speech to text with Amazon Transcribe

In the previous section, you learned about text to speech. In this section, you will learn about speech to text and the service that provides it: Amazon Transcribe. It is an automatic speech recognition service that uses pre-trained deep learning models, which means that you do not have to train on petabytes of data to produce a model; Amazon does this for us. You just have to use the APIs that are available to transcribe audio files or video files; it supports a number of different languages and custom vocabulary too. Accuracy is the key, and through custom vocabulary, you can enhance it based on the desired domain or industry:

![](img/87c29232224b00f5a8bba6a66a391700_213_0.png)

Figure 8.10 – Block diagram of Amazon Transcribe's input and output

Some common uses of Amazon Transcribe include the following:

- Real-time audio streaming and transcription
- Transcribing pre-recorded audio files
- Enable text searching from a media file by combining AWS Elasticsearch and Amazon Transcribe
- Performing sentiment analysis on recorded audio files for voice helpdesk (contact center analytics)
- Channel identification separation

Next, you will explore the benefits of Amazon Transcribe.

## Exploring the benefits of Amazon Transcribe

Let’s look at some of the benefits of using Amazon Transcribe:

- Content redaction: Customer privacy can be ensured by instructing Amazon Transcribe to identify and redact personally identifiable information (PII) from the language transcripts. You can filter unwanted words from your transcript by supplying a list of unwanted words with VocabularyFilterName and VocabularyFilterMethod, which are provided by the StartTranscriptionJob operation. For example, in financial organizations, this can be used to redact a caller’s details.

- Language identification: It can automatically identify the most used language in an audio file and generate transcriptions. If you have several audio files, then this service will help you classify them by language.

- Streaming transcription: You can send recorded audio files or live audio streams to Amazon Transcribe and output a stream of text in real time.

- Custom vocabulary or customized transcription: You can use your custom vocabulary list as per your custom needs to generate accurate transcriptions.

- Timestamp generation: If you want to build or add subtitles to your videos, then Amazon Transcribe can return the timestamp for each word or phrase from the audio.

- Cost effectiveness: Being a managed service, there is no infrastructure cost.

Now, let’s get hands-on with Amazon Transcribe.

## Getting hands-on with Amazon Transcribe

In this section, you will build a pipeline where you can integrate AWS Lambda with Amazon Transcribe to read an audio file stored in a folder in an S3 bucket, and then store the output JSON file in another S3 bucket. You will monitor the task’s progress in CloudWatch Logs too. You will use the start_transcription_job asynchronous function to start our job and you will constantly monitor the job through get_transcription_job until its status becomes COMPLETED. Let’s get started:

1. First, create an IAM role called transcribe-demo-role for the Lambda function to execute. Ensure that it can read and write from/to S3, use Amazon Transcribe, and print the output in CloudWatch logs. Add the following policies to the IAM role:

   - AmazonS3FullAccess
   - CloudWatchFullAccess
   - AmazonTranscribeFullAccess

2. Now, you will create a Lambda function called transcribe-lambda with our existing IAM role, transcribe-demo-role, and save it.

Please make sure you change the default timeout to a higher value in the **Basic settings** section of your Lambda function. I have set it to 10 min and 20 sec to avoid timeout errors. You will be using an asynchronous API call called start_transcription_job to start the task and monitor it by using the get_transcription_job API.

3. Paste the code available at https://github.com/PacktPublishing/AWS-Certified-Machine-Learning-Specialty-MLS-C01-Certification-Guide-Second-Edition/blob/main/Chapter08/Amazon%20Transcribe%20Demo/lambda_function/lambda_function.py and click on **Deploy**. This should give us the following output:

![](img/87c29232224b00f5a8bba6a66a391700_215_0.png)

Figure 8.11 – The Basic settings section of our created lambda function

4. Next, you will be creating an S3 bucket called **transcribe-demo-101** and a folder called **input**. Create an event by going to the **Properties** tab of the **Create event notification** section. Enter the following details:

   - Name: audio-event
   - Events: All object create events
   - Prefix: input/
   - Destination: Lambda Function
   - Lambda: transcribe-lambda

5. Upload the audio file in .mp4 format to the **input** folder. This will trigger the Lambda function. As per the code, the output will be stored in the S3 bucket in JSON format, which you can then use to read the contents of the file.

6. Navigate to **CloudWatch > CloudWatch Logs > Log groups > aws/lambda/transcribe-lambda**. Choose the latest stream from the list. It will look as follows:

## Log events

| Timestamp | Message |
|---|---|
| 2020-09-28T21:10:47.554+01:0... | START RequestId: b5774cde-e65e-4376-a73d-7cf9944c36d4 Version: $LATEST |
| 2020-09-28T21:10:47.554+01:0... | --- Speech-to-Text --- |
| 2020-09-28T21:10:48.157+01:0... | checking status.... It is not complete |
| 2020-09-28T21:11:08.242+01:0... | checking status.... It is not complete |
| 2020-09-28T21:11:28.330+01:0... | checking status.... It is not complete |
| 2020-09-28T21:11:48.412+01:0... | Check your Output Bucket |
| 2020-09-28T21:11:48.412+01:0... | Speech to text Completed: |
| 2020-09-28T21:11:48.412+01:0... | END RequestId: b5774cde-e65e-4376-a73d-7cf9944c36d4 |
| 2020-09-28T21:11:48.412+01:0... | REPORT RequestId: b5774cde-e65e-4376-a73d-7cf9944c36d4 Duration: 60857.34 ms Billed Duration: 60900 ms |
| | No newer events at this moment. Auto retry paused. Resume |

Figure 8.12 – The logs in a Log Stream for the specified log groups in the CloudWatch console

7. The output is saved to the S3 bucket in JSON format, as per the job name mentioned in your code (you can use the S3 getObject API to download and read it):

![](img/87c29232224b00f5a8bba6a66a391700_216_0.png)

Figure 8.13 – The output JSON file in an S3 bucket

## IMPORTANT NOTE

It is a best practice not to overprovision your function’s timeout settings. Always understand your code performance and set a function timeout accordingly. Overprovisioning a function timeout results in Lambda functions running longer, causing unexpected costs. If you are using asynchronous API calls in your Lambda function, then it is good to write them into SNS topics on success and trigger another Lambda function from that. If it needs human intervention, then it is suggested that you use AWS Step Functions.

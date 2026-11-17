# AWS Application Services for AI/ML

In this chapter, you will learn about the AWS AI services for building chatbots, advanced text analysis, document analysis, transcription, and so on. This chapter has been designed in such a way that you can solve different use cases by integrating AWS AI services and get an idea of how they work. AWS is growing every day, and they are adding new AI services regularly.

In this chapter, you will approach different use cases programmatically or from the console. This will help you understand different APIs and how to use them. You will use S3 for storage and AWS Lambda to execute any code. The examples in this chapter are in Python, but you can use other supported languages such as Java, Node.js, .NET, PowerShell, Ruby, and so on.

You will cover the following topics:

+   * Analyzing images and videos with Amazon Rekognition
+   * Text to speech with Amazon Polly
+   * Speech to text with Amazon Transcribe
+   * Implementing natural language processing with Amazon Comprehend
+   * Translating documents with Amazon Translate
+   * Extracting text from documents with Amazon Textract
+   * Creating chatbots on Amazon Lex
+   * Time series forecasting with Amazon Forecast

# Technical requirements

All you need for this chapter is an AWS account.

You can download the code examples for this chapter from GitHub at

https://github.com/PacktPublishing/AWS-Certified-Machine-Learning-Specialty-MLS-C01-Certification-Guide-Second-Edition/tree/main/Chapter08.

# Analyzing images and videos with Amazon Rekognition

If you need to add powerful visual analysis to your applications, then Amazon Rekognition is the service to choose. Rekognition Image lets you easily build powerful applications to search, verify, and organize millions of images. It lets you extract motion-based context from stored or live stream
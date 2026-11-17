
We also provide a PDF file that has color images of the screenshots/diagrams used in this book. You can download it here: https://packt.link/ky8E8.

## Conventions Used

There are a number of text conventions used throughout this book.

**Code in text**: Indicates code words in text, database table names, folder names, filenames, file extensions, pathnames, dummy URLs, user input, and Twitter handles. Here is an example: “You will use the detect_labels API from Amazon Rekognition in the code.”

A block of code is set as follows:

```
from sagemaker.predictor import Predictor
predictor = Predictor(endpoint_name='your-endpoint-name',
sagemaker_session=sagemaker_session)
predictor.predict('input_data')
```

Any command-line input or output is written as follows:

```
sh-4.2$ cd ~/SageMaker/
sh-4.2$ git clone https://github.com/PacktPublishing/AWS-Certified-Machine-Learning-Specialty-MLS-C01-Certification-Guide-Second-Edition.git
```

**Bold**: Indicates a new term, an important word, or words that you see onscreen. For example, words in menus or dialog boxes appear in the text like this. Here is an example: “In **CloudWatch**, each **Lambda function** will have a **log group** and, inside that log group, many **log streams**.”

## TIPS OR IMPORTANT NOTES

_Appear like this._

## Get in Touch

Feedback from our readers is always welcome.

**General feedback**: If you have questions about any aspect of this book, mention the book title in the subject of your message and email us at customercare@packt.com.

**Errata**: Although we have taken every care to ensure the accuracy of our content, mistakes do happen. If you have found a mistake in this book, we would be grateful if you would report this to us. Please visit www.packtpub.com/support/errata, selecting your book, clicking on the Errata Submission Form link, and entering the details. We ensure that all valid errata are promptly updated in the GitHub repository, with the relevant information available in the Readme.md file. You can access the GitHub repository: https://packt.link/QFk6t.

**Piracy**: If you come across any illegal copies of our works in any form on the Internet, we would be grateful if you would provide us with the location address or website name. Please contact us at copyright@packt.com with a link to the material.

If you are interested in becoming an author: If there is a topic that you have expertise in and you are interested in either writing or contributing to a book, please visit authors.packtpub.com.

## Share Your Thoughts

Once you’ve read AWS Certified Machine Learning - Specialty (MLS-C01) Certification Guide, Second Edition, we’d love to hear your thoughts! Please click here to go straight to the Amazon review page for this book and share your feedback.

Your review is important to us and the tech community and will help us make sure we’re delivering excellent quality content.

## Download a Free PDF Copy of This Book

Thanks for purchasing this book!

Do you like to read on the go but are unable to carry your print books everywhere?

Is your eBook purchase not compatible with the device of your choice?

Don’t worry, now with every Packt book you get a DRM-free PDF version of that book at no cost.

Read anywhere, any place, on any device. Search, copy, and paste code from your favorite technical books directly into your application.

The perks don’t stop there, you can get exclusive access to discounts, newsletters, and great free content in your inbox daily.

Follow these simple steps to get the benefits:

- 1. Scan the QR code or visit the link below:

![](img/87c29232224b00f5a8bba6a66a391700_22_0.png)

https://packt.link/free-ebook/9781835082201

- 2. Submit your proof of purchase.

- 3. That’s it! You’ll send your free PDF and other benefits to your email directly.

## Machine Learning Fundamentals

For many decades, researchers have been trying to simulate human brain activity through the field known as artificial intelligence, or AI for short. In 1956, a group of people met at the Dartmouth Summer Research Project on Artificial Intelligence, an event that is widely accepted as the first group discussion about AI as it’s known today. Researchers were trying to prove that many aspects of the learning process could be precisely described and, therefore, automated and replicated by a machine. Today, you know they were right!

Many other terms appeared in this field, such as machine learning (ML) and deep learning (DL). These sub-areas of AI have also been evolving for many decades (granted, nothing here is new to the science). However, with the natural advance of the information society and, more recently, the advent of big data platforms, AI applications have been reborn with much more applicability – power (because now there are more computational resources to simulate and implement them) and applicability (because now information is everywhere).

Even more recently, cloud service providers have put AI in the cloud. This helps all sizes of companies to reduce their operational costs and even lets them sample AI applications, considering that it could be too costly for a small company to maintain its own data center to scale an AI application.

An incredible journey of building cutting-edge AI applications has emerged with the popularization of big data and cloud services. In June 2020, one specific technology gained significant attention and put AI on the list of the most discussed topics across the technology industry – its name is ChatGPT.

ChatGPT is a popular AI application that uses large language models (more specifically, generative pre-trained transformers) trained on massive amounts of text data to understand and generate human-like language. These models are designed to process and comprehend the complexities of human language, including grammar, context, and semantics.

Large language models utilize DL techniques (for example, deep neural networks based on transformer architecture) to learn patterns and relationships within textual data. They consist of millions of parameters, making them highly complex and capable of capturing very specific language structures.

Such mixing of terms and different classes of use cases might get one stuck on understanding the practical steps of implementing AI applications. That brings you to the goal of this chapter: being able to describe what the terms AI, ML, and DL mean, as well as understanding all the nuances of an ML pipeline. Avoiding confusion about these terms and knowing what exactly an ML pipeline is will allow you to properly select your services, develop your applications, and master the AWS Machine Learning Specialty exam.

## Making the Most Out of this Book – Your Certification and Beyond

This book and its accompanying online resources are designed to be a complete preparation tool for your MLS-C01 Exam.

The book is written in a way that you can apply everything you’ve learned here even after your certification. The online practice resources that come with this book (Figure 1.1) are designed to improve your test-taking skills. They are loaded with timed mock exams, interactive flashcards, and exam tips to help you work on your exam readiness from now till your test day.

## BEFORE YOU PROCEED

To learn how to access these resources, head over to Chapter 11, Accessing the Online Practice Resources, at the end of the book.

![](img/87c29232224b00f5a8bba6a66a391700_25_0.png)

Figure 1.1 – Dashboard interface of the online practice resources

Here are some tips on how to make the most out of this book so that you can clear your certification and retain your knowledge beyond your exam:

- 1. Read each section thoroughly.

- 2. Make ample notes: You can use your favorite online note-taking tool or use a physical notebook. The free online resources also give you access to an online version of this book. Click the BACK TO THE BOOK link from the Dashboard to access the book in Packt Reader. You can highlight specific sections of the book there.

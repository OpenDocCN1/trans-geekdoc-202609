With that, we have discussed the core architecture components of a data science environment in AWS. Next, we will provide a hands-on exercise where you will configure a data science environment and perform some data science experiments and model building.

# Hands-on exercise – building a data science environment using AWS services

In this hands-on exercise, you will create a data science environment using SageMaker with AWS CodeCommit as the source control.

# Problem statement

As an ML Solutions Architect, you have been tasked with building a data science environment on AWS for the data scientists in the Equity Research department have several NLP problems, such as detecting the sentiment of financial phrases. Once you have created the environment for the data scientists, you also need to build a proof of concept to show the data scientists how to build and train an NLP model using the environment.

# Dataset

The data scientists have indicated that they like to use the BERT model to solve sentiment analysis problems, and they plan to use the financial phrase dataset to establish some initial benchmarks for the model: `https://www.kaggle.com/ankurzing/sentiment-analysis-for-financial-news.`

# Lab instructions

Follow these steps to create a data science environment using SageMaker with AWS CodeCommit as the source control.

# Setting up SageMaker Studio

Follow these steps to set up a SageMaker Studio environment:

+   1 To create a SageMaker Studio environment, we need to set up a domain and a user profile in the respective AWS region. Navigate to the SageMaker management console once you've logged into AWS Management Console and click on the **Amazon SageMaker Studio** link on the left.
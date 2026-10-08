
Segmentation is one traditional way to understand the different customer segments to improve marketing campaigns' effectiveness. There are different ways to do segmentations with machine learning, as unsupervised clustering of customers based on data such as basic demographic data. This allows you to group customers into several segments and create unique marketing campaigns for each segment.

A more effective marketing approach is to use highly personalized user-centric marketing campaigns. We work by creating accurate individual profiles using large amounts of individual behavior data such as historical transaction data, responses data to historical campaigns, and alternative textual data such as social media data. Highly personalized campaigns with customized marketing messages can be generated using these profiles for a higher conversion rate. The ML approach to user-centric target marketing predicts the conversion rate, such as the click-through rate (CTR), for different users and sends ads to users with a high conversion rate. This can be a classification or regression problem by learning the relationship between the user features and the probability of conversion.

Contextual advertising is another way to reach the target audience by placing advertisements such as display ads or video ads on web pages that match the advertisement's content. An example of contextual advertising is to place product advertisements on cooking recipe sites. Because the ads are highly relevant to the content, they will likely resonate with the visitors' readers and result in a much higher click-through rate. ML can help with detecting ads from a context so that the ads are placed correctly. For example, computer vision models can detect objects, people, and themes in video ads to extract contextual information and match them to the website's content.

## Sentiment analysis

Retail businesses often need to understand the perception of their brand from their consumers' point of view. Positive and negative sentiments towards a retailer could greatly improve or damage a retail business. As more online platforms are becoming available, it is easier than ever for consumers to voice their feelings towards a product or business from their real-life experiences. Retail businesses are adopting different techniques to assess their customer's feelings and emotions towards their product and by analyzing feedback solicited from their shoppers or analyzing their social media channels. Effective sentiment analysis can help identify areas for improvement, such as operational and product improvement, as well as for gathering intelligence in relation to potentially malicious brand reputation attacks.

Sentiment analysis is mainly a text classification problem that uses labeled text data (for example, a product review is labeled either positive or negative). Many different ML classifier algorithms, including deep learning-based algorithms, can be used to train a model to detect sentiment in a piece of text.

## Product demand forecasting

Retail businesses need to do inventory planning and demand forecasting to optimize retail revenue and manage inventory costs. This helps avoid out-of-stock situations while reducing the cost of stocking inventory. Traditionally, retailers have been using different demand forecasting techniques based on buyer surveys, collective opinions from multiple inputs, and expert opinions.

Statistical and ML techniques such as regression analysis and deep learning-based approaches can produce more accurate and data-driven demand forecasting. In addition to using historical demand and sales data to model future forecasts, learning-based algorithms can also incorporate other related data such as price, holidays, special events, and product attributes to train an ML model that is capable of producing more accurate forecasts. The following diagram shows the concept of building a deep learning model using multiple data sources to generate forecasting models:

![](img/bd21298357d8484151447cff0b2f138b_67_0.png)

Figure 2.19 – Deep learning-based forecasting model

ML-based forecasting models can generate point forecasts (a number) of probabilistic forecasts (a forecast with a confidence score). Many retail businesses use ML to generate baseline forecasts, and professional forecasters review them and make adjustments based on human expertise and other factors.

## ML use case identification exercise

In this exercise, you are going to apply what you have learned in this chapter to your line of business. The goal is to go through a thinking process to business problems that can potentially be solved with machine learning:

- Think about a business operation in your line of business. Create a workflow of the operation and identify any known issues, such as a lack of automation, human errors, and long processing cycles in the workflow.
- List the business impact of these issues in terms of revenue, increased cost, poor customer and employee satisfaction, and potential regulatory and compliance risk exposure. Try to quantify the business impact as much as possible.
- Pick one or two problems with the most significant impact if the problems can be solved. Think about ML approaches (supervised machine learning, unsupervised machine learning, or reinforcement machine learning) to solve the problem.
- List the data that could be helpful for building ML solutions.
- Write a proposal for your idea that includes the problem statement, identified opportunities and business value, data availability, and implementation and adoption challenges.
- List the business and technology stakeholders that you will need to work with to bring your idea to life.

## Summary

In this chapter, we covered several ML use cases across multiple industries. You now should have a basic understanding of some top industries and some of the core business workflows in those industries. You have learned about some of the relevant use cases, the business impact that those use cases have, and the ML approaches for solving them.

The next chapter will cover how machines learn and some of the most commonly used ML algorithms.

## Section 2: The Science, Tools, and Infrastructure Platform for Machine Learning

In Section 2, you will learn about the core sciences and technologies for data science experimentations and ML data science platforms for data scientists.

This section comprises the following chapters:

- Chapter 3, Machine Learning Algorithms
- Chapter 4, Data Management for Machine Learning
- Chapter 5, Open Source Machine Learning Libraries
- Chapter 6, Kubernetes Container Orchestration Infrastructure Management

## 3 Machine Learning Algorithms

Machine learning (ML) algorithm design is usually not the main focus for a practitioner. However, ML architects still need a solid understanding of how ML works and design the appropriate infrastructure to run them.

In this chapter, you will develop a deeper understanding of how ML works. We will cover common ML tasks, such as classification, regression, object detection, recommendation, forecasting, and natural language. You will learn the concepts behind these algorithms, their advantages and disadvantages, and where to apply them. Specifically, we are going to cover the following topics:

- How machines learn
- Overview of ML algorithms
- Hands-on exercise

## Technical requirements

You need a personal computer (Mac or Windows) to complete the hands-on exercise.

You need to download the dataset from https://www.kaggle.com/mathchi/chunk-for-customers. Additional instructions will be provided in the Hands-on section.

## How machines learn

In Chapter 1, Machine Learning and Solutions Architecture, we briefly touch upon how ML algorithms improve themselves by processing data. So, how does an algorithm actually learn? In short, ML algorithms learn by optimizing (for example, minimizing or maximizing) an objective function (also known as a loss function). You can think of an objective function as a business metric, such as the difference between the projected sales of a product and the actual sales, and the goal of optimizing this objective would be to reduce the difference between the actual sales number and the projected sales. To optimize this objective, an ML algorithm would iterate and process large amounts of historical sales data (training data) and adjust its internal model parameters until it minimizes the differences between the projected and actual values. This process of finding the optimal parameters is called optimization, and the mathematical routines for performing the optimization are called optimizers.

To illustrate what optimization means, let's use a simple example of training an ML model to predict the sales of a product using its price as the input variable. Here, we use a linear function for the ML algorithm, shown as follows:

```
sales = W * price + B
```

In this example, we want to minimize the difference between the actual sales and predicted sales, and we use the following mean square error (MSE) as the loss function to optimize. The specific optimization task is to find the optimal values for the W and B parameters that produce the minimal MSE:

```
Error = 1/n Σ_{i=1}^n (predicted_i - actual_i)^2
```

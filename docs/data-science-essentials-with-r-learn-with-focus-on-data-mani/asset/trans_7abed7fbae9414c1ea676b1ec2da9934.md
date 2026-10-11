
# Types of Machine Learning Systems

Machine learning systems can be categorized based on their learning methods, which determine how they make predictions or generate content:

*   Supervised Learning
*   Unsupervised Learning
*   Reinforcement Learning
*   Generative AI

## Supervised Learning

In supervised learning, algorithms are trained on datasets containing input data and corresponding output labels. The goal is for the algorithm to learn the relationship between the input data and the correct output labels, enabling it to make accurate predictions on new, unseen data. It is called "supervised" learning because humans provide labeled data to the algorithm, guiding it toward the correct solution.

Supervised learning encompasses two types of tasks: regression and classification.

### Regression

Regression models predict numerical values based on input features. Their primary objective is to establish a relationship between input features and a target variable, allowing for accurate prediction of numerical outcomes. For example, predicting house prices based on a set of features (location, size, number of bedrooms, etc., known as predictors) (Figure 10.1). To train a model for this task, you need a diverse dataset with many house samples containing both the predictors (features) and their corresponding labels (prices).

![Figure 10.1: Regression task example - predicting house prices based on house size](images/Figure10.1.png)

The table below lists more examples of regression tasks.

| Target | Potential Input Variables | Predicted Numerical Outcome |
| --- | --- | --- |
| Stock Price Prediction | Historical stock prices, trading volume, economic indicators, company financials, news sentiment | Price of a specific stock |
| Energy Consumption Forecasting | Historical energy usage, temperature, day of week, time of day | Energy consumption in kWh |
| Crop Yield Estimation | Soil quality, weather conditions, irrigation levels, historical yield data | Yield in bushels |
| Website Traffic Forecasting | Historical website traffic, marketing campaign data, seasonal trends | Expected website visits |
| Air Quality Prediction | Air pollution levels, meteorological data, historical air quality indices | Air quality index for a specific area |

Table 10.3: Regression Task Examples

### Classification

Classification models are a subset of supervised learning algorithms used to predict the likelihood that an instance belongs to a specific category or class. Unlike regression models, which output numerical values, classification models output values indicating whether an item belongs to a specific category.

Classification models fall into two categories: binary classification and multi-class classification. In binary classification, the model generates a value from a category with only two possibilities. For example, a model might predict whether a transaction is fraudulent or not fraudulent (Figure 10.2). Multi-class classification involves making predictions from multiple categories. For example, classifying weather conditions as sunny, cloudy, rainy, or snowy.

![Figure 10.2: Classification task example - predicting if a transaction is fraudulent](images/Figure10.2.png)

The table below shows several classification task scenarios:

| Target | Potential Input Variables | Predicted Classification Outcome |
| --- | --- | --- |
| Customer Churn Prediction | Customer demographics, purchase history, support interactions, feedback | Churn (Yes/No) |
| Email Spam Classification | Email content, sender information, historical spam data | Spam (Yes/No) |
| Loan Approval Prediction | Applicant credit score, income, debt-to-income ratio, employment status, loan amount requested | Loan Approved (Yes/No) |
| Customer Segment Identification | Purchase history, demographics, website interactions | Customer Segment Category: e.g., Premium, Standard, New |
| Customer Subscription Prediction | Customer activity, usage patterns, engagement with subscription-related features | Subscribed (Yes/No) |

Table 10.4: Classification Task Examples

## Unsupervised Learning

In unsupervised learning, training data lacks explicit labels, requiring the model to learn patterns and structures without explicit guidance. Unlike supervised learning, there are no labeled outputs to guide the model's learning process. This approach is particularly useful when exploring and understanding the inherent complexities and relationships within a dataset, especially when labeled examples are unavailable or difficult to obtain.

A common technique in unsupervised learning is clustering, where the model identifies natural groupings in data by finding data points that share common characteristics or patterns. Figure 10.3 illustrates a clustering schematic:

![Figure 10.3: Clustering - Unsupervised Learning](images/Figure10.3.png)

Besides clustering, there are several other unsupervised learning tasks. One is anomaly detection, which identifies data points that deviate significantly from the majority of the data. Anomaly detection can be used for applications like fraud detection, network intrusion detection, and manufacturing defect identification. Another task is dimensionality reduction, which reduces the number of features in a dataset while retaining the most important information. Dimensionality reduction can also be used for visualizing high-dimensional data.

## Reinforcement Learning

Reinforcement Learning (RL) is a branch of machine learning where algorithms learn by interacting with an environment. RL models learn through exploration, taking actions, and receiving feedback in the form of rewards or penalties. The goal of RL is for the agent to discover a policy—a set of rules dictating the best action to take in different situations—to maximize cumulative reward.

Reinforcement learning has been successfully applied to various tasks, such as training robots to perform manipulation tasks like grasping and pouring, and navigating unknown environments. It is also used to recommend products or content based on user interactions, and to develop AI agents capable of achieving professional-level play in games like poker.

## Generative AI

Generative AI models are deep learning algorithms capable of creating various types of content—such as images, music, articles, and even videos—using user input. A key advantage of generative AI is its ability to handle diverse inputs and outputs. For example, a model can accept text and images as input and generate video as output, or accept an image as input and generate a descriptive text caption.

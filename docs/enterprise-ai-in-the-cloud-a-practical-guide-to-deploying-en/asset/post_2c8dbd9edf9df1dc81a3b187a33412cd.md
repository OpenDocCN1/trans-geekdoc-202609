
Artificial intelligence is a broad, umbrella term that refers to the collection of technologies enabling computers to mimic human intelligence. The dictionary definition of intelligence is “the ability to acquire knowledge and skills and apply them.”

*Artificial intelligence refers to a machine's ability to perform the human mind's cognitive functions, such as perceiving, reasoning, learning, interacting, solving problems, and even showing creativity. Anything that a machine does, for example, listening to someone and responding in human words, such as Alexa, is artificial intelligence. Artificial intelligence is also when a machine looks at the surroundings using computer vision and helps a car navigate. The technologies involve the following:*

- > Radars and sensors
- > Devices that take in all data and feed it to the car so that it can take appropriate action

Artificial intelligence includes those collections of technologies, such as natural language processing, speech recognition, and computer vision. [Figure 16.2]() shows the range of technologies and applications that fall under the broad umbrella of artificial intelligence.

Here's Gartner's definition of AI:

> Artificial intelligence (AI) applies advanced analysis and logic-based techniques, including machine learning, to interpret events, support and automate decisions, and take action.
> (Source: www.gartner.com/en/topics/artificial-intelligence)

## Machine Learning: The Brain Behind Artificial Intelligence

The next question is, then, what is machine learning? *Machine learning* is often used interchangeably with artificial intelligence. An excellent way to answer that question is to take the driverless car example. Again, the sensors, radars, and other systems in the car take in all the data from the environment and move the car around. But, how is the car moving autonomously?

There is a machine learning model that takes in the data and predicts the outcome. The model's output tells the car to go left, right, stop, move fast, and accelerate.

Machine learning is about crunching all the data, processing it, identifying the patterns, and, based on that, returning a prediction.

Artificial intelligence is an umbrella term for all the technologies that try to mimic human intelligence. But the actual process by which large amounts of data are crunched to come up with insights is through machine learning.

![](img/1490b3cf638678afadc8c48abc1698d5_395_0.png)

## FIGURE 16.2: Umbrella of AI technologies

## Features and Weights of Predictive Algorithms

An algorithm has two key components—features and weights. *Features* are parts of a dataset identified as essential to determine an outcome. The features may also be known as columns or attributes in a dataset.

You can think of features as essential attributes to predicting an outcome. For example, if you are trying to predict the price of a home, the features could include the number of bedrooms, square footage, location, and so on.

However, you also need to know the context of the attribute impacting the outcome, in other words, how important that attribute is to predict an outcome. That's where the *weights* come in. These weights are assigned as part of training, and if, say, it is highly influential to the outcome, the system might assign a higher weight, say 0.8. The training process uses the dataset to assign the weights to different factors to predict the outcome with a certain level of accuracy.

## FACTORS TO CONSIDER WHEN CHOOSING A MACHINE LEARNING ALGORITHM

This section walks through an example scenario to understand the steps in choosing a machine learning algorithm. Suppose your company has asked you to use machine learning to increase sales. You have a large amount of data such as customer purchase history, demographic information, website behavior information, and so on.

| FACTOR | DESCRIPTION |
| :--- | :--- |
| Identify the type of problem. | The first thing to do is identify the problem you need to solve. In this case, you're trying to increase sales, which means you're trying to identify customers who are likely to purchase from your site. This is the classification problem because you're trying to identify who will buy and who will not. |
| Assess the size of the dataset. | The next step is to assess the size of the dataset. If you have a large dataset, using complex algorithms such as deep learning is possible. However, if the dataset is smaller, you can use simpler algorithms such as linear regression. |
| Decide on the interpretability of the model. | The algorithm choice also depends on whether the model needs to be *interpretable*, meaning is it required to explain how the model came up with its prediction? If you have to explain how the model predicts the outcome, you cannot use complex algorithms such as deep learning. |
| Decide on the performance metrics. | It is also vital to decide on the metrics you'll use to evaluate the model's performance. In this case, you can use accuracy, precision, and recall, thereby evaluating how well the model predicts which customer will likely make a purchase. |
| Plan for scalability. | It would help if you also planned for the scalability of the model. In this case, given that you have a large dataset, it may be a good idea to plan for a distributed machine learning algorithm such as Apache Spark. |

> **TIP** When choosing a machine learning algorithm, carefully consider the problem type, dataset size, interpretability requirements, appropriate performance metrics, and the need for scalability to ensure an effective and efficient solution.

## HANDS-ON EXERCISE: SELECTING A MACHINE LEARNING ALGORITHM

This is a strategic hands-on exercise focused on choosing the right machine learning algorithm for your project's use case. It is a critical step because choosing the right algorithm will decide the accuracy of the model and therefore drives the outcome of your overall project.

It will help you to think critically about various phases of machine learning such as identifying a problem, assessing data, interpreting models, measuring performance, and considering scalability requirements. This exercise mirrors the thought process that goes into planning a data analysis or modeling project.

**Goal:** Assume that you have been hired as a data scientist for an e-commerce company that has trusted you with the responsibility of leveraging the customer data to gain a competitive advantage to address the stiff competition the company has been facing. The marketing team has told you that they would like to predict which customers are likely to purchase next month so they can plan their marketing campaigns accordingly. They have given you a dataset that contains the customers' past purchases as well as other demographic information such as age, location, browsing behavior, and so on. Now your task is to identify a suitable algorithm to solve the problem.

| STEP | DESCRIPTION |
| :--- | :--- |
| Identify the type of problem. | Decide what type of machine learning problem this is; in this case, this a classification problem as this is trying to identify the customers who are likely to buy vs those who may not. |
| Assess the size of the dataset. | If the dataset is very large, you may need a deep learning algorithm, else a simpler algorithm would suffice. |
| Check whether the model needs to be interpretable. | If the model needs to be interpretable, you will need a simpler model. |
| Choose appropriate performance metrics. | Choose the appropriate performance metrics based on the model; for example, in this case it's a classification problem, so you can choose accuracy, precision, and recall. |
| Check out the scalability requirements. | If the dataset is large and likely to grow, you should explore machine learning algorithms that are compatible with distributed processing such as those offered by Apache Spark. |
| Write a report regarding the finalized algorithm. | Prepare a report with the type of algorithm, how it meets the requirements, as well as the challenges, limitations with this approach, and other alternatives if available. |

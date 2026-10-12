
We will look at the different ways to classify the approaches in the following sections.

### Supervised, Unsupervised, and Semi‐supervised Learning

A common method of classifying machine learning approaches is based on the type of learning. When you have a labeled dataset that you can use to train your model, it is called `supervised learning`. For example, supervised learning would be trying to build a model to classify images of dogs or cats and having the ability to use a dataset of images that have been labeled accordingly.

There are some cases where you have only unlabeled data, such as a set of images (without any labels or tags), and you will be asked to classify or group them. This would be an `unsupervised` ML model. Clustering algorithms are a suite of algorithms that belong to this type and are used to group and/or classify data. Autoencoders are also a family of algorithms that belong to this type. Autoencoders are used to reduce the dimensionality of input data, a preprocessing step in many machine learning models.

Another popular unsupervised ML use case is `topic modeling`, a type of document clustering problem. The algorithm takes documents and classifies them into N number of classes based on the commonality of words and sentences in the texts. Comparing this to how a human being would classify books, say, in a library, you may classify them into fiction, nonfiction, science, history, and so on. In other times, you may classify the books based on languages (for example, English, Chinese, Hindi). Similarly, an unsupervised algorithm may or may not classify in the way you expected. The output of unsupervised learning methods cannot be fully controlled, and it is almost never perfect and so requires careful tuning to get required results. [Table 1.1](#c01.xhtml#c01-tbl-0001) provides the details of some of the popular ML model types that are readily available in Google Cloud.

**TABLE 1.1**  ML problem types

Source: Adapted from Google cloud/ `https://cloud.google.com/vertex-ai/docs/training-overview` last accessed December 16, 2022.

| Name | Data Type | Supervised/Unsupervised |
| --- | --- | --- |
| Regression – Tables | Tabular | Supervised |
| Classification – Tables | Tabular | Supervised |
| Forecasting | Series | Supervised |
| Image classification | Image | Supervised |
| Image segmentation | Image | Supervised |
| Object detection | Image | Supervised |
| Video classification | Video | Supervised |
| Video object tracking | Video | Supervised |
| Video action recognition | Video | Supervised |
| Sentiment analysis | Text | Supervised |
| Entity extraction | Text | Supervised |
| Translation | Text | Supervised |
| K‐means clustering | Tabular | Unsupervised |
| Principal component analysis | Tabular | Unsupervised |
| Topic modeling | Text | Unsupervised |
| Collaborative filtering/recommendations | Mixed | Supervised/Unsupervised |

To solve the problem of uncertainty in unsupervised learning, there is a hybrid solution called `semi‐supervised learning`, where some data is labeled and other data is not. This is like guiding the algorithm toward the clusters that you want to see. While semi‐supervised models are interesting research topics and have some utility, in a majority of use cases, supervised models are used.

There are many other kinds of machine learning models beyond these, including reinforcement learning (where the algorithm is not given data but is given an environment that the agent explores and learns) and active learning algorithm, but they are beyond the scope of the certificate exam.

Another way to classify the machine learning algorithms is based on the type of prediction. The type of data the model will predict determines several aspects of the machine learning algorithm and the method used. We will explore that next.

### Classification, Regression, Forecasting, and Clustering

`Classification` is the process of predicting the “labels” or “classes” or “categories.” Given a picture of a pet, classifying dogs versus cats is a classification problem. If there are just two labels, it is called `binary classification`, and if there are more labels, it is called `multiclass classification`. You could have a classification with thousands of labels; for example, the Cloud Vision API can classify millions of different objects in a picture, which is a more difficult problem to solve. You cannot apply the same model for binary classification, multiclass classification, and classification with thousands of classes.

In `regression`, the ML model predicts a number—for example, prediction of house price (given the number of bedrooms, square footage, zip code), prediction of the amount of rainfall (given temperature, humidity, location). Here the predicted value's range depends on the use case. The ML algorithms used for regression are usually different from classification. Typically, you would find structured data (data in rows and columns), as shown in [Table 1.2](#c01.xhtml#c01-tbl-0002), being used for regression problems.

**TABLE 1.2**  Structured data

| Student ID | Age | Exam Scores (Out of 100) |
| --- | --- | --- |
| 1 | 34 | 75 |
| 2 | 23 | 59 |
| 3 | 36 | 92 |
| 4 | 31 | 67 |

`Forecasting` is another type where the input is time‐series data and the model predicts the future values. In a time‐series dataset ([Table 1.3](#c01.xhtml#c01-tbl-0003)), you get a series of input values that are indexed in time order. For example, you have a series of temperature measurements taken every hour for 10 hours from a sensor. In this case, one temperature reading is related to the previous and next reading because they are from the same sensor, in subsequent hours, and usually only vary to a small extent by the hour, so they are not considered to be “independent” (an important distinction from other types of structured data).

**TABLE 1.3**  Time‐Series Data

| | Temperature |
| --- | --- |
| Series 1 | 29, 30, 40, 39, 23, 20 |
| Series 2 | 10, 11, 13, 23, 43, 34 |
| Series 3 | 19, 18, 19, 20, 38, 20 |
| Series 4 | 14, 17, 34, 34, 12, 43 |

Some forecasting problems can be converted to regression problems by modifying the time‐series data into independent and identically distributed (IID) values. This is done either for convenience or availability of data or for preference for a certain type of ML model. In other cases, regression problems can be converted into classification problems by bucketizing the values. We will look into details in the following chapters. There is an art to fitting an ML model to a use case.

`Clustering` is another type of problem, where the algorithm creates groups in the data based on inherent similarities and differences among the different data points. For example, if we are given the latitude and longitude of every house on Earth, the algorithm might group each of these data points into clusters of cities based on the distances between groups of houses. K‐means is a popular algorithm in this type.

## ML Success Metrics

A business problem can be solved using many different machine learning algorithms, so which one to choose? An `ML metric` (or a suite of metrics) is used to determine if the trained model is accurate enough. After you train the model (supervised learning), you will predict the values (y) for, say, N data points for which you know the actual value (y). We will use a formula to calculate the metric from these N predictions.

There are several metrics with different properties. If so, what is our metric? What is the formula for calculating the metric? Does the metric align with the business success criteria? To answer these questions, let us look at each class of problems, starting with classification.

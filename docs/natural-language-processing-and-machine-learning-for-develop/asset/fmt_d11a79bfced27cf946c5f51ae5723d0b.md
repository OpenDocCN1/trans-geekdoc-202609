
If you are a developer, you’re probably accustomed to using an algorithmic approach to tasks, which often involves executing a sequence of steps in a deterministic manner. However, machine learning involves an approach that is similar to a forensic analysis because `the distribution of data in large datasets is often unknown and might even be impossible to determine with high accuracy`. As a result, it’s difficult to apply a test-driven development (TDD) approach to training models on datasets. Moreover, the accuracy of a model that has been trained on a nontrivial dataset will never be 100%, which means that a lower percentage is the best that can be achieved.

How do you determine what level of accuracy is acceptable? First, you are unlikely to exceed the current SOTA (“state of the art”), unless you are implementing a new algorithm that has proven to be superior to all other existing algorithms for the task at hand. Second, this decision is likely to be a mixture of a technical decision and a business decision. For example, if your model achieves 90% accuracy and the State of the Art (SOTA) is 95%, is it worth investing the additional time and expense to improve the accuracy of your model, or is 90% “good enough” for your business needs?

Despite the variety of machine learning algorithms, the data is arguably more important than the selected algorithm. Many issues can arise with data, such as insufficient data, poor quality of data, incorrect data, missing data, irrelevant data, duplicate data values, and so forth. Later in this chapter you will see techniques that address many of these data-related issues.

If you are unfamiliar with machine learning terminology, a dataset is a collection of data values, which can be in the form of a CSV file or a spreadsheet. Each column is called a feature, and each row is a datapoint that contains a set of specific values for each feature. If a dataset contains information about customers, then each row pertains to a specific customer.

One distinction to keep in mind is that machine learning differs from data mining: the latter is a manual process for making decisions, whereas machine learning involves training models on data sets by means of machine learning algorithms.

### Learning Style of Machine Learning Algorithms

Here are the main types of machine learning (combinations of these are also possible) that you will encounter:

* supervised learning

* unsupervised learning

* semisupervised learning

* active learning

* self-supervised learning

* weakly supervised learning

* reinforcement learning

`Supervised learning` means that the datapoints in a dataset have a label that identifies its contents. For example, the MNIST dataset contains 28×28 PNG files, each of which contains a single hand-drawn digit (i.e., 0 through 9 inclusive). Every image with the digit 0 has the label 0; every image with the digit 1 has the label 1; all other images are labeled according to the digit that is displayed in those images.

As another example, the columns in the Titanic dataset are features about passengers, such as their gender, the cabin class, the price of their ticket, whether or not the passenger survived, and so forth. Each row contains information about a single passenger, including the value 1 if the passenger survived. The MNIST dataset and the Titanic dataset involve `classification` tasks: the goal is to train a model based on a training dataset and then predict the class of each row in a test dataset.

In general, the datasets for classification tasks have a small number of possible values: one of nine digits in the range of 0 through 9, one of four animals (dog, cat, horse, giraffe), one of two values (survived versus perished, purchased versus not purchased). As a rule of thumb, if the number of outcomes can be displayed “reasonably well” in a drop-down list, then it’s probably a classification task.

In the case of a dataset that contains real estate data, each row contains information about a specific house, such as the number of bedrooms, the square feet of the house, the number of bathrooms, the price of the house, and so forth. In this dataset the price of the house is the label for each row. Notice that the range of possible prices is too large to fit “reasonably well” in a drop-down list. `A real estate dataset involves a regression task: the goal is to train a model based on a training dataset and then predict the price of each house in a test dataset.`

`Unsupervised learning` involves unlabeled data, which is typically the case for clustering algorithms (discussed later). Active learning is a subset of unsupervised learning, as described here:

`[https://www.kdnuggets.com/2018/10/introduction-active-learning.html](https://www.kdnuggets.com/2018/10/introduction-active-learning.html)`

`Self-supervised` and weakly supervised learning:

`[https://towardsdatascience.com/weakly-and-self-supervised-learning-part-4-2fbfd10280b3](https://towardsdatascience.com/weakly-and-self-supervised-learning-part-4-2fbfd10280b3)`

There is one more very important unsupervised task called `anomaly detection`. This task is relevant for fraud detection and detecting outliers (discussed later in more detail).

`Semi-supervised` learning is a combination of supervised and unsupervised learning: some data points are labeled and some are unlabeled. One technique involves using the labeled data in order to classify (i.e., label) the unlabeled data, after which you can apply a classification algorithm.

`Reinforcement` learning pertains to maximizing a reward, and this type of learning is beyond the scope of this book.

## Types of Machine Learning Algorithms

This section contains lists of machine learning algorithms that includes algorithms that are accompanied by code samples later in this book. There are many algorithms that are not discussed in this book, however, they are included in case you decide to learn about them through self-study. Keep in mind that the lists of algorithms are not in increasing order of complexity of the algorithms.

One way to classify machine learning algorithms is based on how closely they perform the same task. A high-level list of various types of algorithms is given here:

* deep Learning algorithms

* instance-based algorithms

* Naive Bayes algorithms

* regression algorithms

* reinforcement learning algorithms

* tree-based algorithms

As you will see later in Chapter [8](#ch08.xhtml), machine learning uses various algorithms to find correlations (patterns) in datasets. Since the distribution of the data in a dataset is often unknown, it’s virtually impossible to predict which algorithm will produce the best accuracy. Therefore, it’s advisable to employ different algorithms on a given dataset and then see which one produces the best accuracy (along with an analysis of other metrics beyond accuracy).

There are three main types of algorithms in machine learning that you will learn about later in this book, and the choice of algorithm depends on the type of analysis that is required. For example, use `linear regression` algorithms when you need to predict numeric values: the price of a house in a real estate dataset, the temperature for the next day or week, and so forth. This type of algorithm belongs to “supervised learning” because you know the labels of the items in the dataset before you train a model on that dataset.

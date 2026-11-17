in a better position to choose a potential algorithm that will solve your problem.

However, what if you don’t have a target variable? In that case, you are facing an unsupervised learning problem. Unsupervised problems do not provide labeled data; instead, they provide all the independent variables (or features) that will allow unsupervised algorithms to find patterns in the data. The most common type of unsupervised learning is **clustering**, which aims to group the observations of the dataset into different clusters, purely based on their features. Observations from the same cluster are expected to be similar to each other, but very different from observations from other clusters. Clustering will be covered in more detail in future chapters of this book.

**Semi-supervised learning** is also present in the ML literature. This type of algorithm can learn from partially labeled data (some observations contain a label and others do not).

Finally, another learning approach that has been taken by another class of ML algorithms is **reinforcement learning**. This approach rewards the system based on the good decisions that it has made autonomously; in other words, the system learns by experience.

You have been learning about approaches and classes of algorithms at a very broad level. However, it is time to get specific and introduce the term **model**.

# The CRISP-DM modeling life cycle

**Modeling** is a very common term used in ML when you want to specify the steps taken to solve a particular problem. For example, you could create a binary classification model to predict whether the transactions from _Table 1.1_ are fraudulent or not.

A model, in this context, represents all the steps to create a solution as a whole, which includes (but is not limited to) the algorithm. The **Cross-Industry Standard Process for Data Mining**, more commonly referred to as **CRISP-DM**, is one of the methodologies that provides guidance on the common steps that you should follow to create models. This methodology is widely used by the market and is covered in the AWS Machine Learning Specialty exam:
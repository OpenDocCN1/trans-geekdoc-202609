# # Chapter 13: Part 5
Deep Learning
SOM: Hybrid Model
Python Implementation

# ### 13.5.1 Problem description

Here we will make a Hybrid Deep Learning Model. We will combine two deep learning models ANN and SOM (supervised and unsupervised).

+   - Our data-set will be made, the credit card applications to identify the frauds.
- The idea is to make an even advanced deep learning model where we can predict the probability that each customer cheated.

+   - It takes two parts:
- In the first part, we'll make the unsupervised deep learning branch of our hybrid deep learning model using SOM.
- And in the second part, we'll make the supervised deep learning branch using ANN.
- And, in the end, we get this hybrid deep learning model composed of unsupervised and supervised deep learning.

+   - We will use the self-organizing map exactly as we previously, to identify the fraud. So, there will be nothing about that.
- But then, the challenge is to use the results of this self-organizing map to ANN/model. ANN will take, as input, the results given by their SOM.
- The challenge is to combine two models. In the end, what we obtain is a ranking of the predicted probabilities each customer cheated.

> NOTE, you will get small probabilities, that's normal. It's because there are few frauds identified by the SOM, but that doesn't matter. What's important that we get this ranking of probabilities.

# ### 13.5.2 SOM part

+   - We run the SOM code to get the map. Execute the code from beginning to show(). method.
- After obtaining the map, we choose a thresholdfor output neuron and we find and select those neurons.
- We concatenate those data.

> NOTE that we execute the following code after excluding the outliers. (8, 6), (1, 7) are just for example, you could be different.

```
### Finding the Frauds
mappings = som_win(X) # not 'x' its our dataset "X", capital X
fraud_1 = mappings((8, 6))
fraud_2 = mappings([1, 7])
frauds = np.concatenate([mappings((8, 6)]), mappings([1, 7])]), axis=0
frauds = sc.inverse_transform(frauds)
```

# ### 13.5.3 ANN & Prediction

Creating the feature matrix We'll take all the columns except first column, i.customer_id.

> NOTE: the first column approved/rejected is not a dependent variable here (it is done by the Bank they don't know if fraud).

```
### creating the matrix of features
cuCustomers = dataset.iloc[:, 1].values
```

+   - Creating the variable for ANN: This dependent variable is about 0 = no fraud and 1 = fraud.
- Since from SOM we extracted some frauds, we can use them as our dependent variable.
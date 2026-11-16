**TIP** Overfitting *means the model has almost memorized the outcomes and cannot be generalized for new data.* It performs poorly on new data even though it works perfectly on training data.

# Using Decision Trees

Decision trees are machine-learning algorithms that can be used for classification and regression. In other words, it is a supervised learning type of algorithm. They work by breaking down the dataset recursively into smaller subsets based on specific criteria until you reach a point where the outcome can be determined.

Say you want to identify the customer who is likely to default on a loan. You collect the dataset of past loan applicants and their information, such as their income, loan amount, credit rating, age, employment, and so on. Then you start by identifying the feature on which to break this dataset. That depends on which feature gives you the highest information gain. You may break the dataset based on the credit score rating in this case.

You then analyze if the customer will default based on their credit rating. If you find that to be true, you create a leaf node that predicts that the customer will default when their credit rating is below that level.

On the other hand, if there is no clear pattern, you choose a different feature, such as their income. You continue with this process until you reach a point where all the data points under a specific subset belong to a particular class, meaning either they have or have not defaulted. Or they stop at some predetermined point, such as a specific tree depth or any other criteria you agree on.

You can then use the prediction on new data once you finalize the decision tree, as shown in Figure 16.9.

The benefits of the decision tree are that it can operate on numerical and categorical data, handle outliers well, and is also visual, making it easy for people to understand. On the other hand, it is susceptible to bias and inaccuracies if it’s not developed properly. Therefore, alternative approaches should be explored if necessary.

Table 16.4 shows various use cases for decision trees.
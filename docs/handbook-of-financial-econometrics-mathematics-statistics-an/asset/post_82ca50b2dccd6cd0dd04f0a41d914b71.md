
The response variable is

- $Y$: Default payment next month (1 = default; 0 = not default).

We use the following 23 variables as explanatory variables:

- $X_1$: Amount of the given credit (NT dollar),
- $X_2$: Gender (1 = male, 2 = female),
- $X_3$: Education (1 = graduate school; 2= university; 3 = high school; 4 = others),
- $X_4$: Marital status (1 = married; 2 = single; 3 = others),
- $X_5$: Age (year),
- $X_6$–$X_{11}$: History of past monthly payment traced back from September, 2005 to April, 2005 (–1 = pay duly; 1 = payment delay for one month; 2 = payment delay for two months; …; 8 = payment delay for eight months; 9 = payment delay for nine months and above),
- $X_{12}$–$X_{17}$: Amount of past monthly bill statement (NT dollar) traced back from September, 2005 to April, 2005.
- $X_{18}$–$X_{23}$: Amount of past payment (NT dollar) traced back from September, 2005 to April, 2005.

This data set is interesting because it contains two “sorts” of attributes. The first sort is about categorical attributes like education, marital status, and age. These attributes have a very small range of possible values, and if there was a high correlation between these categorical attributes then the classification algorithms would be able to easily identify them and produce high accuracies. The second sort of attribute is the past payment information. These attributes are just integers without clear differentiation of categories and have much larger possible ranges of how much money was paid. Especially, if there was not strong correlation between education, marital status, age, etc. and defaulting on payments, it could be more difficult to algorithmically predict the outcome from past payment details, except for the extremes where someone never pays their bills or always pays their bills.

Figure 101.1 plots the heatmap to show pairwise correlations between attributes. It is shown that most correlations are about zeros, but high correlations exist in features of past monthly payments ($X_6$, …, $X_{11}$) and past monthly bill statements ($X_{12}$, …, $X_{17}$).

## 101.3 Machine Learning

Let $X = (X_1, …, X_p)'$ denote the $p$-dimensional input vector, and let $Y = (Y_1, …, Y_d)'$ denote the $d$-dimensional output vector. In its simplest form,

![](img/31ee7e6fa5107b22bbf7960ec96106a1_3719_0.png)

Figure 101.1: The heatmap of correlations between the response variable and all predictors in the credit card dataset.

A learning machine is an input-output mapping, Y = F(X). In statistics, F(·) is usually a simple function, such as a linear or polynomial function. In contrast, the form of the F(·) in machine learning may not be represented by simple functions.

In the following, we introduce the spirit of five machine learning methods: k-nearest neighbors, decision tree, boosting, support vector machine, and neural network, with illustrative examples. Rigorous formulations for each machine learning method will not be covered here because they are out of the scope of this chapter.

### 101.3.1 k-Nearest neighbors

The k-Nearest Neighbors (KNN) method is intuitive and easy to implement. First, a distance metric (such as the Euclidean distance) needs to be chosen to identify the KNNs for a sample of unknown category. Second, a weighting scheme (uniform weighting or distance weighting) to summarize the score of each category needs to be decided. The uniform weighting scheme gives equal weight for all neighbors regardless of its distance to the sample of unknown category, whereas the distance weighting scheme weights distant neighbors less. Third, the score for each category is summed over these KNNs. Finally, the predicted category of this sample is the category yielding the highest score.

![](img/31ee7e6fa5107b22bbf7960ec96106a1_3720_0.png)

Figure 101.2: Illustration of the k-nearest neighbors.

An example is illustrated in Figure 101.2. Suppose there are two classes (category A and category B) for the output and two features (x1 and x2). A sample of unknown category is plotted as a solid circle. KNN predicts the category of this sample as follows. To start, we choose Euclidean distance and uniform distance weight. If K = 3, in the three nearest neighbors to the unknown sample, there are one sample of category A and two samples of category B. Because there are more samples of category B, KNN predicts the unknown sample to be of category B. If K = 6, in the six nearest neighbors to the sample of unknown category, there are four samples of class A and two samples of class B. Because class A occurs more frequently than class B, KNN predicts the sample to be of category A.

In addition to the distance metric and weighting scheme, the number of neighbors K is needed to be decided. Indeed, the performance of the KNN is highly sensitive to the size of K. There is no strict rule in selecting K. In practice, the selection of K can be done by observing the predicted accuracies for various K and select the one that reach the highest training scores and cross-validation scores. Detailed descriptions about how to calculate these scores are given in Section 101.4.

### 101.3.2 Decision trees

A decision tree is also called a classification tree when the target output variable is categorical. For a decision tree, leaves represent class labels and branches represent conjunctions of features that lead to those class labels. Decision tree is usually constructed top-down, by choosing a mapping of feature variables at each step that best splits the set of items. Different algorithms choose different metrics for measuring the homogeneity of the target variables within the subsets. These metrics are applied to each candidate subset and the resulting values are combined to provide a quality of the split. Common metrics include the Gini Index or Information Gain based on the concept of entropy.

Figure 101.3 depicts the structure of a decision tree: the decision tree starts with a root node and consists of internal decision nodes and leaf nodes. The decision nodes and leaf nodes are stemmed from the root node and are connected by branches. Each decision node represents a test function with discrete outcomes labeling the branches. The decision tree grows along with these branches into different depths of internal decision nodes. At each step, the data is classified by a different test function of attributes leading the data either to a deeper depth of internal decision node or it finally ends up at a leaf node.

Figure 101.3 illustrates a simple example. Suppose an interviewer is classified as “decline offer” or “accept offer”. The tree starts with a root node. The root node is a test function to check if the salary is at least $50,000. If data with answer “no” declines offer, the branch ends up with decline offer and hence is represented as a leaf node indicating “decline”. If the answer is yes, the data remain contains samples of declining and accepting the offer. Therefore, this branch results in a second decision node to check if the interviewer needs commuting time more than 1 hour and the output could be “yes” and “no”. If data with answer “yes” declines the offer. Then, this branch ends up

Classification and regression. Because CART is not limited to the types of response and independent variables, it is of wide popularity.

Suppose we would like to build up a next lower node, and the possible classification label is $i$, for $i=1,\ldots,c$. Let $p_i$ represent the proportion of the number of samples in the lower node classified as $i$. The Gini Index is defined as

$$\text{Gini Index}=1-\sum_{i=1}^{c}p_i^2.$$ (101.1)

The attribute used to build the next node is the one that maximize the Gini Index.

The Information Gain is precisely the measure used by the decision tree ID3 and C4.5 to select the best attribute or feature when building the next lower node (Mitchell, 1997). Let $f$ denote a candidate feature, and $D$ denote the data at current node and $D_i$ denote the data classified as label $i$ at the lower node, for $i=1,\ldots,c$. $N=|D|$ is the number of the sample at current node, and $N_i=|D_i|$ is the number of sample classified as label $i$ at the lower node. Then, the Information Gain is defined as

$$IG(D,f)=I(D)-\sum_{i=1}^{c}\frac{N_i}{N}I(D_i).$$ (101.2)

where $I$ is an impurity measure, either the Gini Index as defined in Eq. (101.1) or the entropy. The entropy is defined as

$$I_e=-\sum_{i=1}^{c}p_i\log_2p_i.$$ (101.3)

Eq. (101.2) can be regarded as the original information at current node minus the expected value of the impurity after the data $D$ is partitioned using attribute $f$. Therefore, $f$ is selected to maximize the IG. Entropy and Gini Impurity perform similarly in general, so we can focus on the adjustment of other parameters.

### 101.3.3 Boosting

In the field of computer science, weak learner is a classification rule of lower accuracy, whereas strong learner is that of higher accuracy. The term “boosting” refers to a family of algorithms which convert weak learners to strong learners. There are many boosting algorithms, such as AdaBoost (Adaptive Boosting), Gradient Tree Boosting, and XGBoost. Here, we focus on AdaBoost.

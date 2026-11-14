
from it. This ML model is then tested with new data to make predictions for the unknown target attribute. Let's understand it with an example.

You want to train your model to separate spam mails from your regular emails. To do so, you need to provide your learning algorithm with the training data that contains a white list and black list. The white list contains email addresses of people you tend to receive email from. The blacklist contains all the addresses of users that you want to avoid receiving email from. So, the ML algorithm will learn from this training data and predict if the new mail is from black list or white list. If it's from the black list, it automatically labels it as spam.

To create an effective model, it is important to select an accurate algorithm that can find predictable, repeatable patterns. On the one hand, some problems that need ML are very specific and require a unique approach to solve the problem, On the other hand, some problems need a trial-and-error approach.

Machine learning algorithms are divided into four main types (see Figure 1.5):

- 1. Supervised learning
- 2. Unsupervised learning
- 3. Semi-supervised learning
- 4. Reinforcement learning

Let's learn them one by one:

### 1. Supervised learning

It's a learning algorithm in which the machine is trained with data that is well labeled and predicts with the help of a labeled dataset.

![](img/62da674fd5b031cf7705f5424f5bc7c5_40_0.png)

**FIGURE 1.5** Machine learning algorithms.

**What is labeled data?** The data for which you already know the target answer is called labeled data. For example, if I show you an image and tell you that it is a butterfly, then it's called labeled data. However, if I show you an image without telling you what it is, that is referred to as unlabeled data.

Now let's understand with an example how labeled data makes a machine learn.

We have images that are labeled as spoon and knife; we then feed them to the machine, which analyzes and learns the association of these images with their labels based on their features such as shape, size, and sharpness. Now, if any new image is fed to the machine without any label, the past data helps the machine to predict accurately and tell whether it's a spoon or knife. Thus, in supervised machine learning, the algorithm teaches the model to learn from the labeled example that we provide.

It consists of two techniques: classification and regression.

- **Classification.** For example, if the output variable is categorical such as red or blue, disease or no disease, male or female, will I get an increment or not?

- **Regression.** Regression is a problem when the output variable is a real or a continuous value, for example, salary based on work experience or weight based on height. So, it creates predictive models showing trends in data. For example, how much increment will I get?

The following is a list of commonly used algorithms in supervised learning:

- Nearest neighbor
- Naive Bayes
- Decision trees
- Linear regression
- Support vector machines (SVM)
- Neural networks
- Logistic regression
- Linear discriminant analysis
- Similarity learning

### 2. Unsupervised learning

In this learning, no training is given to the machine, allowing it to act on data that is not labeled. Hence, the machine tries to identify the patterns and provide the predictions. Let's take the example of a spoon and knife, but this time we do not tell the machine whether it's a spoon or a knife. The machine by itself identifies patterns from the set and makes a group based on their patterns, similarities, differences, and so on.

Unsupervised learning consists of two techniques: clustering and association.

- **Clustering.** In clustering, the machine forms groups based on the behavior of the data. For example, which customer made similar product purchases?

- **Association.** It is an area of machine learning that identifies exceptional relationships between variables in large datasets. For example, which products were purchased together?

The following is a list of commonly used algorithms in unsupervised learning:

- k-means clustering
- Association rules

### 3. Semi-supervised learning

Semi-supervised learning is a type of machine learning that uses a combination of both supervised and unsupervised learning techniques. It is used in a scenario where our dataset is a combination of both labeled and unlabeled data.

For example, let's assume that we have access to a large number of unlabeled datasets that we like to train a model on. Manually labeling the whole data by ourselves is just not practical. So, instead of labeling the whole dataset, we manually label some parts of the dataset ourselves and use that portion to train our model. But this way, all the unlabeled data will be of no use. As we know, the more data we have to train our model, the better and more robust our model would be. So what can we do to use the unlabeled data of our dataset?

This is why semi-supervised learning was introduced. To prevent our unlabeled data from getting wasted, we can implement a technique of semi-supervised learning called pseudo labeling.

To understand pseudo labeling, let's continue with the example mentioned previously.

Our model is trained using labeled data, and it is performing pretty well. Everything to this point is just regular supervised learning. Now we will use unsupervised learning to predict the remaining unlabeled portion of data. We will serve the unlabeled data to our model. The trained model will then process this data, and as a result, it will predict individual outputs for each piece of unlabeled data. Thus, pseudo labeling is a process of labeling the unlabeled data with the output that is predicted by our neural network. With pseudo labeling, we can train on an audaciously larger dataset.

### 4. Reinforcement learning

There is no predefined data in reinforcement learning. It is the area of machine learning that is concerned with behavioral psychology. In this learning, an agent is put into an environment, and he learns to behave in this environment by performing certain actions and observing the awards that they get from their actions. Reinforcement learning involves software agents that take appropriate actions in a particular situation to earn maximum rewards. There is no expected output in this learning. The reinforcement agent decides what actions to take to perform a task. In the absence of the training dataset, it is bound to learn from its own experience.

The following is a list of commonly used algorithms in reinforcement learning:

- Q-learning
- Temporal difference (TD)
- Deep adversarial networks

Now to choose which algorithm is right for your problem, you should categorize your problem according to the following:

- Categorize by input
  - Labeled data: supervised learning
  - Unlabeled data: unsupervised learning
  - Combination of labeled and unlabeled data: semi-supervised learning
  - No data and want to optimize an objective function by interacting with an environment: reinforcement learning
- Categorize by output
  - If the output of a model is a number: regression problem
  - If the output of a model is a class: classification problem
  - If the output of your model is a set of input groups: clustering problem
  - To detect an anomaly: anomaly detection
- Understand your constraints
  - Storage capacity of model
  - Fast prediction
  - Fast learning
- Find the available algorithms: Factors affecting the choice of the model are:
  - Business goals
  - Amount of preprocessing required in data
  - Accuracy of the model
  - Scalability of the model
- Consider model complexity
  - Complex feature engineering
  - Computational overhead

These points can help you to choose the right algorithm for developing a solution to a real-time business problem that requires knowledge of business requirements, rules and regulations, and stakeholders' interests as well as significant expertise. Hence, to solve a machine problem, it is crucial to combine and balance algorithms for valuable results.

## Validation

Once the machine learning model has been properly trained on a given dataset, then we have to test the model. In this step, we check for the accuracy of the model by rendering a test dataset to it. Testing the model is important to find out the percentage accuracy of the model as per the project requirement or given problem.

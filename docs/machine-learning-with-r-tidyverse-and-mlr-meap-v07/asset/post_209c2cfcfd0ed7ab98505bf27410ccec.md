
Arthur Samuel, a scientist at IBM, first used the term machine learning in 1959. He used it to describe a form of artificial intelligence (AI) that involved training an algorithm to learn to play the game of checkers. The word learning is what's important here, as this is what distinguishes machine learning approaches from traditional AI.

```
numberOfLegs <- c(4, 4, 0)
climbsTrees <- c(TRUE, FALSE, TRUE)
for (i in 1:3) {
if (numberOfLegs[i] == 4) {
if (climbsTrees[i]) print("cat") else print("dog")
} else print("snake")
}
```

In the R code above I've created three rules, mapping every possible input available to us to an output:

- If the animal has four legs and climbs trees, it's a cat
- If the animal has four legs and does not climb trees, it's a dog
- Otherwise, the animal is a snake

Now if we apply these rules to the data, we get the expected answers:

```
[1] "cat"
[1] "dog"
[1] "snake"
```

The problem with this approach is that you need to know all possible outputs the computer should give you in advance, and the system will never give you an output that you haven't told it to give. Contrast this to the machine learning approach, where instead of telling the computer the rules, you give it the data and allow it to learn the rules for itself. The advantage of this approach is that the "machine" can learn patterns we didn't even know existed in the data, and the more data we provide, the better it gets at learning those patterns (figure 1.2).

![](img/a22105d68c35e8d5bd3c7bafb4644881_8_0.png)

In practice, we call a set of rules a machine learning algorithm learns a model. Once the model has been learned, we can give it new observations and it will output its predictions for the new data. We refer to these as models because they represent real-world phenomena in a simplistic-enough way that we and the computer can interpret and understand. Just as a model of the Eiffel Tower may be a good representation of the real thing but isn’t exactly the same, so statistical models are attempted representations of real-world phenomena but won’t match them perfectly.

> **NOTE** You may have heard the famous phrase coined by the statistician George Box that "all models are wrong, but some are useful", which refers to the approximate nature of models.

The process by which the model is learned is referred to as the algorithm. As we discovered earlier, an algorithm is just a sequence of operations that work together to solve a problem. So how does this work in practice? Let’s take a simple example. Say we have two continuous variables, and we would like to train an algorithm that can predict one (the outcome or dependent variable), given the other (the predictor or independent variable). The relationship between these

![](img/a22105d68c35e8d5bd3c7bafb4644881_10_0.png)

**Figure 1.4** A hypothetical algorithm for learning the parameters of a straight line. This algorithm takes two continuous variables as inputs, and fits a straight line through the mean. It iteratively rotates the line until it finds a solution that minimises the sum of squares. The parameters of the line are output as the learned model.

> **NOTE** One of the initially confusing but eventually fun aspects of machine learning is that there are a plethora of algorithms to solve the same type of problem. The reason for this is that different people have come up with slightly different ways of solving the same problem, all trying to improve upon previous attempts. The result of this is that, for a given task, it is our job as data scientists to choose which algorithm(s) will learn the best performing model.

While certain algorithms tend to perform better than others with certain types of data, there is no single algorithm that will always outperform all others on all problems. This concept is called the *no free lunch theorem*. In other words, you don’t get something for nothing; you need to put some effort into working out the best algorithm for your particular problem. Instead, data scientists typically choose a few algorithms they know tend to work well for the type of data and problem they are working on, and see which algorithm generates the best performing model. We’ll see how we do this later on in the book. We can, however, narrow down our initial choice by dividing machine learning algorithms into categories, based on the function they perform and how they perform it.

## 1.2 Classes of machine learning algorithms

All machine learning algorithms can be categorized by their learning type, and the task they perform. There are three learning types:

- *supervised*
- *unsupervised*
- *semi-supervised*

This depends on how the algorithms learn. Do they require us to hold their hand through the learning process? Or do they learn the answers for themselves? Supervised and unsupervised algorithms can be further split into two classes each:

- supervised
  - *classification*
  - *regression*
- unsupervised
  - *dimension reduction*
  - *clustering*

This depends on what they learn to *do*.

So we categorize algorithms by how they learn, and what they learn to do. But why do we care about this? Well, there are **a lot** of machine learning algorithms available to us. How do we know which one to pick? What kind of data do they require to function properly? Knowing which categories different algorithms belong to makes our job of selecting the most appropriate ones much simpler. In the next section I cover how each of the classes is defined and why it’s different from the others. By the end of this section you’ll have a clear understanding of why you would use algorithms from one class over another. By the end of the book you’ll have the skills to apply a number of algorithms from each class.

### 1.2.1 Differences between supervised, unsupervised, and semi-supervised learning

Imagine you are trying to get a toddler to learn about shapes using blocks of wood. In front of them, they have a ball, a cube, and a star. You ask them to show you the cube, and if they point to the correct shape you tell them they are correct, and if they are incorrect you also tell them. You repeat this procedure until the toddler can identify the correct shape almost all of the time. This is called *supervised learning*, because you, the person who already knows which shape is which, are supervising the learner by telling them the answers.

![](img/a22105d68c35e8d5bd3c7bafb4644881_13_0.png)

**Figure 1.5 Supervised vs. unsupervised machine learning.** Supervised algorithms take data already labeled with a ground-truth, and build a model which can predict the labels of unlabeled, new data. Unsupervised algorithms take unlabeled data and learn patterns within it, such that new data can be mapped onto these patterns.

customers will default on their payments? Which patients will survive? Which objects in a telescope image are stars, planets or galaxies? When faced with problems like these, you should use a classification algorithm.

- Regression algorithms take labeled data, and learn patterns in the data that can be used to predict a *continuous* output variable. How much carbon dioxide does a household contribute to the atmosphere? What will the share price of a company be tomorrow? What is the concentration of insulin in a patient’s blood? When faced with problems like these, you should use a regression algorithm.

Unsupervised machine learning algorithms can also be split into two classes: dimension reduction and clustering algorithms.

- Dimension reduction algorithms take unlabeled (because they are unsupervised learning methods), high-dimensional data (data with many variables) and learn a way of representing it in a lower number of dimensions. Dimension reduction techniques may be used as an exploratory technique (because it’s very difficult for humans to visually interpret data in more than two or three dimensions at once), or as a pre-processing step in our machine learning pipeline (it can help mitigate problems such as *collinearity* and the *curse of dimensionality*, terms we will define in later chapters). We can also use it to help us visually confirm the performance of classification and clustering algorithms (by allowing us to plot the data in two or three dimensions).

- Clustering algorithms take unlabeled data, and learn patterns of clustering in the data. A cluster is a collection of observations which are more similar to each other than to data points in other clusters. We assume that observations in the same cluster share some unifying features or identity that makes them identifiably different from other clusters. Clustering algorithms may be used as an exploratory technique to understand the structure of our data, and may indicate a grouping structure that can be fed into classification algorithms. Are there subtypes of patient responders in a clinical trial? How many classes of respondent were there in the survey? Are there different types of customer that use our company? When faced with problems like these, you should use a clustering algorithm.

See figure 1.6 for a summary of the different types of algorithms by type and function.

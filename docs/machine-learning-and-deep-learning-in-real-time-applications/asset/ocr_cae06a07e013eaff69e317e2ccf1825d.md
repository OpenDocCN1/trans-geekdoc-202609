# Employee's Attrition Prediction Using Machine Learning Approaches

The aim of this chapter is to provide a comparative analysis of different machine learning approaches for employee attrition prediction. Here we have significantly enhanced the training process to solve the imbalanced class problem.

# Methodology

In this chapter, various supervised machine learning approaches are used. This section provides a general description of these approaches.

# Naïve Bayes

It is a probabilistic approach that uses Bayes theorem to predict the posterior probability of a class. It computes the posterior probability of an event based on the prior knowledge of the related feature(Rane & Kumar, 2018). Equation 1 shows the computation of posterior probability.

```
$P\left(\frac{Cl}{x}\right) = \frac{P\left(\frac{Cl}{x}\right)}{P(x)}$$ (1)
```

Where, $Cl$: specified class
$x$: review for classification
$P(Cl)$ and $P(x)$: prior probabilities

$P\left(\frac{Cl}{x}\right)$ : posterior probability

# Support Vector Machine

It is a non-parametric supervised machine learning approaches used for classification and regression. It was initially proposed by Vapnik and cooper in 1995(Cortes & Vapnik, 1995). It assigns a new data member to one of two possible classes. It defines a hyperplane that separates n-dimensional data into two classes.

# Logistic Regression

It is a traditional classification approach used to assign observations to a particular class. It transforms its output using a sigmoid function to return a probability value that can be mapped to a class. It is a widely used classifier that is easy to implement and works well on linearly separable classes (Raschka, 2015).

# Random Forest

It consists of many individual decision trees that are used to train data (Ho, 1995). Each tree in a random forest spits out a class prediction, and the class with the most votes becomes the model's prediction.
# 2.2 Uncertainty in Machine Learning

Applied machine learning requires getting comfortable with uncertainty. Uncertainty means working with imperfect or incomplete information. Uncertainty is fundamental to the field of machine learning, yet it is one of the aspects that causes the most difficulty for beginners, especially those coming from a developer background. For software engineers and developers, computers are deterministic. You write a program, and the computer does what you say. Algorithms are analyzed based on space or time complexity and can be chosen to optimize whichever is most important to the project, like execution speed or memory constraints.

Predictive modeling with machine learning involves fitting a model to map examples of inputs to an output, such as a number in the case of a regression problem or a class label in the case of a classification problem. Naturally, the beginner asks reasonable questions, such as:

+   - What are the best features that I should use?
+   - What is the best algorithm for my dataset?

The answers to these questions are unknown and might even be unknowable, at least exactly.

> Many branches of computer science deal mostly with entities that are entirely deterministic and certain. [...] Given that many computer scientists and software engineers work in a relatively clean and certain environment, it can be surprising that machine learning makes heavy use of probability theory.
> 
> — Page 54, Deep Learning, 2016.

This is the major cause of difficulty for beginners. The reason that the answers are unknown is because of uncertainty, and the solution is to systematically evaluate different solutions until a good or good-enough set of features and/or algorithm is discovered for a specific prediction problem. There are three main sources of uncertainty in machine learning, and in the following sections, we will take a look at the three possible sources in turn.

# 2.3 Noise in Observations

Observations from the domain are not crisp; instead, they contain noise. An observation from the domain is often referred to as an instance or a example and is one row of data. It is what was measured or what was collected. It is the data that describes the object or subject. It is the input to a model and the expected output. An example might be one set of measurements of one iris flower and the species of flower that was measured in the case of training data.

```
Sepal length: 5.1 cm
Sepal width: 3.5 cm
Petal length: 1.4 cm
Petal width: 0.2 cm
Species: Iris setosa
```

Listing 2.1: Example of measurements and expected class label.

In the case of new data for which a prediction is to be made, it is just the measurements without the species of flower.
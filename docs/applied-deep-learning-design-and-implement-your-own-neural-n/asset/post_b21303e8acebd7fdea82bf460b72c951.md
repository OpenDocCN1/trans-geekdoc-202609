
The logistic regression hypothesis inclines to limit the cost function of the logistic function between 0 and 1. Hence, linear functions fail to characterize because they can have a value even more than 1 or sometimes less than 0.

```
0 \le h_\theta(x) \le 1
```

The preceding equation represents the expectation of the hypothesis of logistic regression.

## Sigmoid function

We use the sigmoid function to map the predicted values to the probabilities. The function can transform or map any type of real-value into another value which lies between 0 and 1. In the case of machine learning, we use the sigmoid function to map the predictions we get into the probabilities. Figure 1.20 shows the curve for the sigmoid function:

![](img/7e519fee1b702b91799cdf1664598392_50_0.png)

Figure 1.20: Sigmoid function

The sigmoid function can be represented as follows:

```
$\sigma(z) = \frac{1}{1+e^{-z}}$ (1.5)
```

Where z is the value for which the sigmoid function changes.

## Hypothesis representation of the logistic regression

The model for the logistic regression can be defined as follows:

```
$Z = \beta_a + \beta_b X$ (1.6)
```

Where X is one independent variable, Z is the observed dependent variable and β_a and β_b are the two parameters. The hypothesis representation of the logistic regression in the sigmoid function of Z.

```
$h_\varphi(x) = \sigma(Z) = Sigmoid (Z)$ (1.7)
```

That is,

$h_\varphi(x) = \frac{1}{1+e^{-(\beta_a + \beta_b x)}}$ (1.8)

The preceding equation represents the hypothesis of logistic regression.

## Decision boundary

As we expect the classifier to provide the output as a set of classes based on the probability, whenever we provide the inputs to the classifier by using a prediction function, the classifier must return a value of probability between 0 and 1.

So, now to map this to a discrete class (a = Domestic animals/ b = Wild animals, true/ false), we select a threshold, say, 0.5. So, above 0.5, we classify values into class “a = Domestic animals”, and below which, we classify values into class “b = Wild animals”.

For example, if you observe figure 1.21, if the value of y = 0.7, then we classify it as a positive value and if the value of y = 0.2, then we classify it as a negative value:

![](img/7e519fee1b702b91799cdf1664598392_51_0.png)

Figure 1.21: Decision boundary

There are two types of logistic regression:

- Binary logistic regression
- Multinomial logistic regression

## Binary logistic regression

Binary or binomial logistic regression handles the situations for which the detected outcome of a dependent variable can be only two types of values, 1 or 0. For example, alive versus dead or loss versus win. In binary logistic regression, the output is coded as 0 or 1. So, it denotes that the regression taking place is a straightforward interpretation. This type of regression can be used for the prediction of the odds for a case depending upon the observed values of the predictors or, say, independent variables.

## Multinomial logistic regression

Multinomial logistic regression handles the situations of the cases when the output can be of more than two possible types and is not in an ordered sequence. It compares multiple groups by using a combination of multiple binary logistic regressions.

For example, suppose we want to study the difference in behavior among Bachelor’s, Master’s, and PhD students. The multinomial logistic regression will compare the Bachelor’s students to Master’s and PhD students, similarly comparison of Master’s students with bachelor’s and PhD students will take place. For each independent class, there will be at least two comparisons.

Some more examples are as follows:

- Nature of person (rude, introvert, and humble)
- Color of flower (green, yellow, and red)

## Cost function

In terms of linear regression, the cost function denotes the objective function, which is optimized; that is, in the case of linear regression, we first define a cost function and then minimize it to develop a model with a minimum error rate.

Figure 1.22 represents the graphs corresponding to cost function estimation using logistic regression:

![](img/7e519fee1b702b91799cdf1664598392_53_0.png)

![](img/7e519fee1b702b91799cdf1664598392_53_1.png)

Figure 1.22: Cost function of logistic regression

In the case of logistic regression, the cost function is defined as negative log-likelihood or binary cross-entropy function as Cost(h_φ(x), y) with the following equation:

```
Cost(h_φ(x), y) = {
  -log(1 - h_φ(x))   if y = 0
  -log(h_φ(x))       if y = 1
} (1.9)

where h_φ(x) = 1 / (1 + e^-(β_a + β_b x))
```

As observed from figure 1.22, the value of the cost function at y = 1 can be determined by using the value of h_φ(x) = 0.8.

So, for this scenario, the cost function is written as follows:

Cost(0.8, 1) = -log(0.8)

So, by solving the preceding equation, we get

-log(0.8) = 0.096

The preceding two cost functions are re-written into a single cost function as follows:

Cost(h_φ(x), y) = -y log(h_φ(x)) - (1 - y) log(1 - h_φ(x))

## Non-linear regression

It is a form of regression analysis in which data is modeled using a function having non-linear combinations of the parameters of the model. The function consists of one or more independent variables. In this type of regression, the data is fitted by successive approximation methods.

A statistical model of the non-linear regression is as follows:

b ~ f(a, β)

where a is a vector of independent variables and b denotes the set of observed dependent variables. β is the set of parameters for which the function f is non-linear.

Let’s take an example of the Michaelis–Menten model for enzyme kinetics.

f(a, β) = β1 a / (β2 + a)

This model has one independent variable a, and two parameters β1 and β2. The function is non-linear as it cannot be represented by a linear combination of two β.

## Linearly and non-linearly separable data

For a better understanding of likely separable data, let us consider two classes represented by blue and red color. A dataset is linearly separable if there is a line that can distinguish the blue and red points from each other.

Figure 1.23 represents the data which is linearly separable for a dataset:

![](img/7e519fee1b702b91799cdf1664598392_55_0.png)

Figure 1.23: Linearly separable data

Figure 1.24 represents the data that is not linearly separable as follows:

![](img/7e519fee1b702b91799cdf1664598392_55_1.png)

Figure 1.24: Linearly non-separable data

## Mathematical definition of a single neuron

The logistic regression is itself a neuron, as shown in figure 1.25. Multiple neurons can be built by using multiple logistic regressions. We can also define the linearly separated data by an algebraic method by considering the separator as a single linear function, that is if the input is ($x_1, x_2, x_3$). Then, separator is a function as follows:

![](img/7e519fee1b702b91799cdf1664598392_56_0.png)

Figure 1.25: Multi-class objects build a neural network

```
$z_1 = w_{11} * x_1 + w_{21} * x_2 + w_{31} * x_3$ (1.15)
$z_2 = w_{12} * x_1 + w_{22} * x_2 + w_{32} * x_3$ (1.16)
$y = z_1 + z_2 + b$ (1.17)
```

where w11, w21, w31, w12, w22, w32 are weights, and b is the associated bias value.

## Generative learning

The generative learning technique works by building separate models of positive and negative values. We can think of the generative learning technique as a model of a blueprint for a class. To create these types of models, the generative learning method uses the joint probability distribution. Classification is a type of generative learning technique, which is discussed as follows.

## Classification

Classification can be defined as a learning approach that is supervised, in which a system learns from the input data (labels) provided to it and then uses it to classify new objects. The type of classification can be either binary or multi-classification.

![](bbox=[0.22, 0.06, 0.78, 0.28])

FIGURE 7.1: Scheme of a perceptron.

+   - if the point is red, there is no need for adjustment: it is labelled correctly as it lies on the right side of the border.

+   - if the point is blue, then the model needs to be updated appropriately. Given the rule mentioned above, this means adjusting the slope of the line downwards. Depending on η, the shift will be sufficient to change the classification of the new point - or not.

At the time of its inception, the perceptron was an immense breakthrough which received an intense media coverage (see Olazaran (1996) and Anderson and Rosenfeld (2000)). Its rather simple structure was progressively generalized to networks (combinations) of perceptrons. Each one of them is a simple unit, and units are gathered into layers. The next section describes the organization of simple multilayer perceptrons (MLPs).

# 7.2 Multilayer perceptron

# 7.2.1 Introduction and notations

A perceptron can be viewed as a linear model to which is applied a particular function: the Heaviside (step) function. Other choices of functions are naturally possible. In the NN jargon, they are called activation functions. Their purpose is to introduce nonlinearity in otherwise very linear models.

Just like for random forests with trees, the idea behind neural networks is to combine perceptron-like building blocks. A popular representation of neural networks is shown in Figure 7.2. This scheme is overly simplistic. It hides what is really going on: there is a perceptron in each green circle and each output is activated by some function before it is sent to the final output aggregation. This is why such a model is called a Multilayer Perceptron (MLP).
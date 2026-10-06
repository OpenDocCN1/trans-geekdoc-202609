# 9.6 NNet with PyTorch (brulee)

We can show this with an example using a Neural Network with one predictor (x), one hidden layer, and multiple hidden neurons.

Let us look at the first hidden neuron. Before its activity is transmitted to the output neuron it is weighted with $eta_3$. Therefore we consider ($eta_3 Act_{t,i}$) rather than its activity ($Act_{t,i}$):

```
$$\beta_3 Act_{t,i} = \beta_3 max (0, \Gamma_{t,i}) \qquad (9.11)$
```

Since we have only one predictor variable $x$, substituting the effective input $\Gamma_{t,i}=eta_1+\beta_2x$ into Equation (9.11) leads to:

```
$$\beta_3 Act_t = \beta_3 (0, \beta_1 + \beta_2 x) \qquad (9.12)$
```

with:
$\beta_3$: parameter for hidden neuron B1
$\beta_2$: parameter for the only predictor variable $x$

Equation (9.12) can be plotted and for $\beta_1=0$, $\beta_2=1$, and $\beta_3=1$, the plot shows the ReLU from Figure 9.7.

By changing $eta_1$, $\beta_2$, and $\beta_3$, the graph of the augmented ReLU function in Figure 9.7 can be transformed:

+   - horizontally shifted (changing $\beta_1$)
- the slope can be changed (changing $\beta_3$)
- the graph can be turned upside down (changing $\beta_3$ to a negative value)
- the graph can be mirrored horizontally (changing the sign of $\beta_2$)

Using the transformations above on two different ReLU functions (two hidden neurons) they can jointly form a step function similar to a Sigmoid function, except that the step on the two ReLU function has two kinks and the slope between the two kinks is constant.

In Section 9.9, we provide a link to an internet app and a blog post where you can transform and combine ReLU functions to form a complete step function.

**Summary:** If we can combine two hidden neurons with ReLU activation functions into a step function, we can expect the approximation properties from a Neural Network with ReLU activation functions that are defined in Section 9.5 for Neural Networks with Sigmoid functions.

The constant slope of a ReLU activation function is a major advantage over a Sigmoid function. Let us compare the slope of the Logistic activation function in Figure 9.3 with the slope of the ReLU activation function in Figure 9.7. The ReLU activation function has a constant slope of one for all positive effective inputs. In contrast, the slope of the Logistic activation function is
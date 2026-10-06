# 4.3 The training-generalization decomposition of $E_{new}$

model value: too small and too high model complexity raises $E_{new}$. This is illustrated in Figure 4.3. A too high model complexity, meaning that $E_{new}$ is higher than it is with a less complex model, is called overfitting. The other situation, when model complexity is low, sometimes called underfitting. In a consistent terminology, the point where $E_{new}$ attains minimum could be referred to as a balanced fit. Since the goal is to minimize $E_{new}$, we are interested in this sweet spot. We also illustrate this by Example 4.1.

Note that we discuss the usual behavior of $E_{train}$ and the generalization gap. We use the term ‘usual’ because there are so many supervised learning methods and problems that it is almost impossible to make any claim that is always true for all possible situations, and counterexamples also exist. One should also keep in mind that $E_{train}$ and $E_{new}$ are the average behavior when the model is trained and evaluated on (hypothetical) training data sets, see Example 4.1.

# **Example 4.1: The training error-generalization decomposition for $k$-NN**

We consider a simulated binary classification case with a two-dimensional input $x$. To contrast to all world machine learning methods, in a simulated example like this we know $p(x)$, which is a uniform distribution on the square $[-1, 1]^2$, and $p(y|x)$ is defined as follows: all points above the curve in Figure 4.4 are blue with probability 0.8, and below the curve are red with probability 0.8. (The optimal classifier, in terms of $E_{new}$, would be the dotted line as its decision boundary and achieve $E_{new} = 0.2$).

![](bbox=[0.381, 0.355, 0.618, 0.51])

**Fig. 4.4**

We have $n=200$ in the training data, and three classifiers: $k$-NN with $k=70$, $k=20$ and $k=2$, respectively. In model complexity, $k=70$ gives the least flexible model, and $k=2$ is the most flexible model. They plot their decision boundaries, together with the training data, in Figure 4.5.

![](bbox=[0.185, 0.583, 0.814, 0.735])

**Fig. 4.5**

We see in Figure 4.5 that $k=2$ (right) adapts too much the data. With $k=70$ (left), on the other hand, the model is not enough to adapt to the noise, but possibly to be too inflexible to adapt well to the dotted line in Figure 4.4.

We can compute $E_{train}$ by counting the fraction of misclassified training data points in Figure 4.5. From left to right, we get $E_{train}=0.27, 0.24, 0.2$. Since this is a simulated example, we can also access $E_{new}$ (or estimate it numerically by simulating a test of data), and from left to right we get $E_{new}=0.26, 0.23, 0.33$. This pattern resembles Figure 4.3, except for the fact that $E_{new}$ is smaller than $E_{train}$ for some values of $k$. However, this is not contrary to the theory, as discussed in the main text or over $E_{new}$ and $E_{train}$ not the situation with $E_{new}$ and $E_{train}$ for one particular set of training data. To study $E_{new}$ and $E_{train}$ we repeat this experiment 100 times, and compute the average over those 100 experiments:
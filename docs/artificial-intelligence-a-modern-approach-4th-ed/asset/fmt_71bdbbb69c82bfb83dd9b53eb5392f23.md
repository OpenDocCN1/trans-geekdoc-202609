
# Finding hypotheses to fit data

## Data sets overview

For both data sets, four graphs are plotted. Thirteen data points are plotted on each graph with a trend of increasing toward the upper right. Data set 1. Linear graph: The function graph passes through five points. Four points each are above and below the line. Sinusoidal graph: Except for two points, the curve either passes through the points or slightly touches them. Piecewise linear graph: The graph is plotted through every single point. Degree-12 polynomial graph: The graph starts from the first point from the left, reaches a sharp peak, decreases to a minimum through the second point, and proceeds to pass through other points as a sinusoidal-like curve. The curve rises to a peak again before the last point and ends on the last point. Data set 2. Linear graph: The function graph passes through seven points. Three points each are above and below the line. Sinusoidal graph: Except for two points, the curve either passes through the points or slightly touches them. Piecewise linear graph: The graph is plotted through every single point. Degree-12 polynomial graph: The graph starts from the first point from the left, reaches a sharp dip, increases to a maximum through the second point, and proceeds to pass through other points as a sinusoidal-like curve. The curve rises to a peak again before the twelfth point, decreases sharply to a minimum, increases again to end on the last point.

×![](images/Fig-263.jpg)

Figure 19.1 Finding hypotheses to fit data. Top row: four plots of best-fit functions from four different hypothesis spaces trained on data set 1. Bottom row: the same four functions, but trained on a slightly different data set (sampled from the same `f(x)` function).

## Hypothesis spaces

• Column 1: Straight lines; functions of the form `h(x) = w1x + w0`. There is no line that would be a consistent hypothesis for the data points.

• Column 2: Sinusoidal functions of the form `h(x) = w1x + sin(w0x)`. This choice is not quite consistent, but fits both data sets very well.

• Column 3: Piecewise-linear functions where each line segment connects the dots from one data point to the next. These functions are always consistent.

• Column 4: Degree-12 polynomials, `h(x) = Σ[i=0]^(12) w[i] x^(i)`. These are consistent: we can always get a degree-12 polynomial to perfectly fit 13 distinct points. But just because the hypothesis is consistent does not mean it is a good guess.

## Bias and variance

One way to analyze hypothesis spaces is by the bias they impose (regardless of the training data set) and the variance they produce (from one training set to another).

### Bias

By bias we mean (loosely) the tendency of a predictive hypothesis to deviate from the expected value when averaged over different training sets. Bias often results from restrictions imposed by the hypothesis space. For example, the hypothesis space of linear functions induces a strong bias: it only allows functions consisting of straight lines. If there are any patterns in the data other than the overall slope of a line, a linear function will not be able to represent those patterns. We say that a hypothesis is underfitting when it fails to find a pattern in the data. On the other hand, the piecewise linear function has low bias; the shape of the function is driven by the data.

<p class="sidebar">Bias</p> <p class="sidebar">Underfitting</p>

### Variance

By variance we mean the amount of change in the hypothesis due to fluctuation in the training data. The two rows of [Figure 19.1](#Chapter19-02.xhtml#fig19-1) represent data sets that were each sampled from the same `f(x)` function. The data sets turned out to be slightly different. For the first three columns, the small difference in the data set translates into a small difference in the hypothesis. We call that low variance. But the degree-12 polynomials in the fourth column have high variance: look how different the two functions are at both ends of the x-axis. Clearly, at least one of these polynomials must be a poor approximation to the true `f(x)`. We say a function is overfitting the data when it pays too much attention to the particular data set it is trained on, causing it to perform poorly on unseen data.

<p class="sidebar">Variance</p> <p class="sidebar">Overfitting</p>

## Bias–variance tradeoff

Often there is a bias–variance tradeoff: a choice between more complex, low-bias hypotheses that fit the training data well and simpler, low-variance hypotheses that may generalize better. Albert Einstein said in 1933, “the supreme goal of all theory is to make the irreducible basic elements as simple and as few as possible without having to surrender the adequate representation of a single datum of experience.” In other words, Einstein recommends choosing the simplest hypothesis that matches the data. This principle can be traced further back to the 14th-century English philosopher William of Ockham.[2](#Chapter19-11.xhtml#sup19-2) His principle that “plurality \[of entities\] should not be posited without necessity” is called Ockham’s razor because it is used to “shave off” dubious explanations.

<p class="sidebar">Bias–variance tradeoff</p>

## Simplicity and model selection

Defining simplicity is not easy. It seems clear that a polynomial with only two parameters is simpler than one with thirteen parameters. We will make this intuition more precise in [Section 19.3.4](#Chapter19-03.xhtml#sec19-3-4). However, in [Chapter 22](#Chapter22-00.xhtml) we will see that deep neural network models can often generalize quite well, even though they are very complex—some of them have billions of parameters. So the number of parameters by itself is not a good measure of a model’s fitness. Perhaps we should be aiming for “appropriateness,” not “simplicity” in a model class. We will consider this issue in [Section 19.4.1](#Chapter19-04.xhtml#sec19-4-1).

Which hypothesis is best in [Figure 19.1](#Chapter19-02.xhtml#fig19-1)? We can’t be certain. If we knew the data represented, say, the number of hits to a Web site that grows from day to day, but also cycles depending on the time of day, then we might favor the sinusoidal function. If we knew the data was definitely not cyclic but had high noise, that would favor the linear function.

## Bayesian perspective

In some cases, an analyst is willing to say not just that a hypothesis is possible or impossible, but rather how probable it is. Supervised learning can be done by choosing the hypothesis `h*` that is most probable given the data:

$\\left. h^{\*} = \\underset{h \\in H}{\\text{argmax}}P\\text{(}h \\middle| data\\text{)}\\text{.} \\right.$

By Bayes’ rule this is equivalent to

$\\left. h^{\*} = \\underset{h \\in H}{\\text{argmax}}P\\text{(}data \\middle| h\\text{)}P(h)\\text{.} \\right.$

Then we can say that the prior probability `P(h)` is high for a smooth degree-1 or -2 polynomial and lower for a degree-12 polynomial with large, sharp spikes. We allow unusual-looking functions when the data say we really need them, but we discourage them by giving them a low prior probability.

## Hypothesis space complexity

Why not let ![](images/H.jpg) be the class of all computer programs, or all Turing machines? The problem is that there is a tradeoff between the expressiveness of a hypothesis space and the computational complexity of finding a good hypothesis within that space. For example, fitting a straight line to data is an easy computation; fitting high-degree polynomials is somewhat harder; and fitting Turing machines is undecidable. A second reason to prefer simple hypothesis spaces is that presumably we will want to use `h` after we have learned it, and computing `h(x)` when `h` is a linear function is guaranteed to be fast, while computing an arbitrary Turing machine program is not even guaranteed to terminate.

For these reasons, most work on learning has focused on simple representations. In recent years there has been great interest in deep learning ([Chapter 22](#Chapter22-00.xhtml)), where representations are not simple but where the `h(x)` computation still takes only a bounded number of steps to compute with appropriate hardware.

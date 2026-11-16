$(x_i, y_i), i=1, \cdots, N$ where $x_i$ is an example input and $y_i$ is the corresponding label provided by human annotators. Ideally after learning, f should map each input in the dataset $(x_i, y_i), i=1, \cdots, N$ to the correct label, i.e. $f(x_i) = y_i$. The hope is that the learner can learn the correct mapping between x and y based on these examples, so that on unseen data, the learner f can also correctly classify.

Usually f is selected from a class of functions indexed by a parameter $\theta$. For example, the class of functions can be quadratic functions
\( f(x) = ax^2 + bx + c \)

![](bbox=[0.27, 0.32, 0.72, 0.48])

# **Figure 1.** Samples from the MNIST dataset.

![](bbox=[0.33, 0.54, 0.66, 0.61])

# **Figure 2.** Classifying multiple digits.

in this example, \(\theta = (a, b, c)\) are the parameters. We will denote the function selected by a parameter choice as \(f_\theta\).

To encourage the learner to select a \(f_\theta\) that maps each \(x_i\) to the correct \(y_i\) we define a loss function such as
\(\mathcal{L}_\theta = \sum_{i=1}^N (f_\theta(x_i) - y_i)^2\)

In general any loss function that takes a smaller value when f(xi) is closer to yi can be used. For classification tasks we use a special class of functions \(f_\theta\) that outputs a probability distribution. That is for each \(x_i\), \(f_\theta(x_i)\) is the probability the input belongs to the j-th class. Then we can use the cross-entropy loss

# 142 Probabilistic regression and Bayes nets

![](img/2087e3fd78fc2bbc9ee0bfaab66e3bde_146_0.png)

Fig. 7.1 (A) A terrestrial robot with Lego Mindstorm with an ultrasonic sensor at the front. (B) Measurements of distance travelled by a robot when running the motor for different numbers of milliseconds with a given power. (C) Corresponding histogram of differences between data and a line that is fitted by minimizing the mean square error between the data and the line.

for most of the data. Let us therefore run a linear regression as discussed in Chapter 5 with the model,

$$\hat{y}(\mathbf{x}) = w_0 + w_1x.$$

We only considered one input variable $x$ above, but we can easily generalize this to higher-dimensional problems where more attributes are given. example, another factor that influences the distance travelled is the power setting of the motor. Of course, the distance travelled within a certain time depends on the power and it is not just an independent additive effect on the distance travelled. Results of the experiment for different power settings and different travel times are shown in Fig.7.2. Fig 7.2A also includes a fit to Eq 7.2. However, these data are better described by a bi-linear hypothesis,

$$\hat{y}(\mathbf{x}) = w_0 + w_1x_2.$$

The corresponding fit of the data is also shown in Figure 7.2. Sometimes we do not know all the factors. For example, we might not be given the power settings of the motors in this sensor so that the data look as shown in Figure 7.2C. These data look more noisy than the previous data, although we know that this is not really noise but, rather, unknown factors. The point of including this is basically that it does not really matter if this randomness may come from an *irreducible indeterminacy*; that is, true randomness that cannot be penetrated by further knowledge, or this noise might represent *epistemological limitations* as the lack of knowledge of hidden processes or limitations in observing states directly. The only important fact for us that we have to live with these limitations. The inclusion of describing uncertainty has helped to make large progress in machine learning.

# A

# B

![](img/2087e3fd78fc2bbc9ee0bfaab66e3bde_147_0.png)

![](img/2087e3fd78fc2bbc9ee0bfaab66e3bde_147_1.png)

![](img/2087e3fd78fc2bbc9ee0bfaab66e3bde_147_2.png)

![](img/2087e3fd78fc2bbc9ee0bfaab66e3bde_147_3.png)

Fig. 7.2 (A) Measurements of distance travelled by the robot when running the motor for number of milliseconds and various power settings. Fitting to Eq 7.2 (B) Histogram of differences between data and hypothesis. (C) The same data as shown in (A) when collapsed across the power setting. The corresponding distribution shown in (D) is much wider than the histogram shown in Fig. 7.1.

We have so basically ignored the fluctuations in the data with the functional regression procedure, and we now investigate more the fluctuations around this trend. 7.1C, 7.2B, and 7.2D are plots of the histogram of the differences between the actual data and the (linear) functional hypothesis of the regressions. The histograms look a lot like a Gaussian distribution. This is not surprising according to the central limit theorem, a Gaussian can be expected as a result of a variety of independent noise sources and this is often observed in nature.

In the following, we will assume that the input values x are given and hence they are not random variables. However, all the following derivations are easily modified if we treat these also as random. In this case we would use for the data density function

```
$p(\tilde{y}|x,w)=p(\tilde{y}|x,w)p(\mathbf{x}).$
```

In this example, we have actually chosen the x-values from a uniform distribution so that the factor p(x) would be a constant or 0 so that it would not matter anything. It does not really matter in the following example. We only mention this fact here as many textbooks in Bayesian statistics consider density functions of data given parameters, $p(D|w)$, and we just to highlight that we will maintain consistent notation in machine learning where we only consider predicted value as random. Of course, with the deterministic case, we have to come up with a specific parameterized function, a density function with parameters $w$. Let us do this for the robot example. Given the form of the "noise" in the above robot example, we assume here that the data in Fig. 7.1C is Gaussian distributed with a mean $\mu = \hat{y}(x)$ that depends linearly on the value of $x$,

```
$p(\hat{y}|x; \sigma) = N(\mu=w^Tx, \sigma) =\frac{1}{\sqrt{2\pi}\sigma}\exp\left(-\frac{(\hat{y}-w^Tx)^2}{2}\right).
```

This functions specifies the likelihood (probability) of values for $\hat{y}$, given an input $x$ and the model with parameters $w$ and $\sigma$. In the following, we keep the parameter $\sigma$ at a specific value so that we only consider $w$ as free. This simply helps to keep the formulae manageable for illustration purposes, though including a variance is all possible. Specifying a model with a density function is an important step in modern modelling and machine learning. In this type of thinking, we treat data as stochastic from the outset, we have just justified a probabilistic model for the example.

## 7.2 Learning in probabilistic models: Maximum likelihood estimate

We will now turn to the important principle that will guide our learning process. Learning means, of course, determining the parameters of the model from data. Here we introduce the maximum likelihood principle. This principle states that in the following way: Given a hypothesis function $p(x|w)$, we will choose the values which make the training data $\{x\}$ most likely. The MLE principle is stated here again in its general form for all random data. In our case we start with a model of the form $p(y|x;w)$ which specifies a probabilistic regression model for given input. This is why the input data appears on the right side of the horizontal bar. However, we will see shortly in MLE we replace all the data at some point with a function (the likelihood function) that is a function of the parameters. Hence, in this case it does not matter if we treat the input as given or as random variables.

Let us illustrate this with the Gaussian example with a parameterized model (Eq 7.5). We are considering the 1-dimensional case with one feature value $x$. Given parameters $w_0, w_1$, and assuming that $\sigma=1$ to simplify the discussions, and the feature value for the first data point $x^{(1)}$, the prediction of the probability of the corresponding label

```
$p(Y_1 = y^{(1)}|x^{(1)}; w_0, w_1) = \frac{1}{\sqrt{2\pi}} \exp \left(-\frac{(y^{(1)} - w_0 - w_1x^{(1)})^2}{2}\right). \quad (7.6)$
```

Now we invoke the maximum likelihood principle and ask which parameters we choose so that the observed data would be most likely under the model with these parameters. That is, we can maximize the probability so that $y = y^{(1)}$. This can be achieved by choosing values

```
$w_1 = \text{arbitrary} \quad (7.7)$
$w_0 = y^{(1)} - w_1x^{(1)}, \quad \quad (7.8)$
```

This is our first maximum likelihood estimate (MLE) of the parameters $w_0$ and $w_1$. Of course, since we have more parameters than data points there is a manifold of solutions and it is clear that we need more than one data point to make predictions. In order to do this, we need to know the probability of a combination of data points for $(x^{(1)}, y^{(1)})$ and $(x^{(2)}, y^{(2)})$. We then need to know the joint distribution of having the values for two labels with specific values. We have not specified a model for this until now. We can do this by making the assumption that the data points are conditionally independent:

```
$p(Y_1=y^{(1)}, Y_2=y^{(2)}|x^{(1)},x^{(2)}; w_0, w_1) = p(Y_1=y^{(1)}|x^{(1)}; w_0, w_1)p(Y_2=y^{(2)}|x^{(2)}; w_0, w_1). \quad (7.9)$
```

In general, if we have $m$ samples, and if we assume that the observation are all conditionally independent, the joint probability of several observations is the product of individual probabilities

```
$p(Y_1=y^{(1)}, Y_2=y^{(2)}, ..., Y_m=y^{(m)}|x^{(1)},...,x^{(m)}; w) = \prod_{i=1}^m p(y_i|x^{(i)}; w). \quad (7.10)$
```

We have written this formula for a general case where all the parameters are collected in the vector $w$, and $y_i$ is a short form of $Y_i = y^{(i)}$. We can insert the specific observations (training data) into the resulting function. We then arrive at a function that is a function of the parameters, no longer a probability for random variables. This function is called the likelihood function

```
$L(w) = \prod_{i=1}^m p(w;y^{(i)}, x^{(i)}). \quad (7.11)$
```

Since it is not a probability density function, we replaced the notation of the vertical bar $|$ with the semi-colon $;$.

We are nearly done. Instead of evaluating this large product, it is common to use the logarithm of the likelihood function, so that we can use the sum of the examples

```
$l(w) = \log L(w) = \sum_{i=1}^m \log p(w;y^{(i)}, x^{(i)}). \quad \quad (7.12)$
```

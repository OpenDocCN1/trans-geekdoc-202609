
*True. By definition of odds, it is easy to notice that p = 0.8 satisfies the following relation:*

$$\text{odds} = \big( \frac{0.8}{0.2} \big) = 4 \qquad \qquad (2.14)$$

**SOL-13 ✏ CH.SOL- 2.10.**

*The graph of odds to probabilities is depicted in Figure 2.12.*

![](img/574135cb1d7125b50cf484d943cdd676_52_0.png)

**SOL-14 ✏ CH.SOL- 2.11.**

*A binary logistic regression GLM consists of three components:*

- 1. *Random component: refers to the probability distribution of the response variable (Y), e.g., binomial distribution for Y in the binary logistic regression, which takes on the values Y = 0 or Y = 1.*
- 2. *Systematic component: describes the explanatory variables: $(X_1, X_2, \dots)$ as a combination of linear predictors. The binary case does not constrain these variables to any degree.*
- 3. *Link function: specifies the link between random and systematic components. It says how the expected value of the response relates to the linear predictor of explanatory variables.*

*Note: Assume that $Y$ denotes whether a human voice activity was detected $(Y=1)$ or not $(Y=0)$ in a given time frame. Propose two systematic components and a link function adjusted for this task.*

**SOL-15** ➡ **CH.SOL- 2.12.**
*The hyperplane is simply defined by:*

$$ \theta_{0} + \theta^{T} X = 0 . $$ (2.15)

*Note: Recall the use of the logit function and derive this decision boundary rigorously.*

**SOL-16** ➡ **CH.SOL- 2.13.**
*True. The logit function is defined as:*

$$ z(p) = logit(p) = \log \left( \frac{p}{1-p} \right) , $$ (2.16)

*for any* $p \in [0,\ 1]$ . *A simple set of algebraic equations yields the inverse relation:*

$$ p(z) = \frac{\exp z}{1+\exp z} , $$ (2.17)

*which exactly describes the relation between the output and input of the logistic function, also known as the sigmoid.*

## 2.3.3 The Sigmoid

**SOL-17 CH.SOL- 2.14.**
There are various approaches to solve this problem, here we provide two: direct derivation or derivation via the softmax function.

- 1. Direct derivation:

$$\frac{d}{dx}\sigma(x) = \frac{d}{dx}((1+e^{-x})^{-1}) = -(1+e^{-x})^{-2}\frac{d}{dx}(1+e^{-x}) = \frac{e^{-x}}{(1+e^{-x})^2}.$$

- 2. Softmax derivation:

In a classification problem with mutually exclusive classes, where all of the values are positive and sum to one, a softmax activation function may be used. By definition, the softmax activation function consists of $n$ terms, such that $\forall i \in [1, n]$:

$$f(\theta_i) = \frac{e^{\theta_i}}{\sum_{k} e^{\theta_k}} = \frac{1}{1+e^{-\theta_i}\sum_{k \neq i} e^{\theta_k}}.$$

> To compute the partial derivative of (2.18), we treat all $\theta_k$ where $k \neq i$ as constants and then differentiate $\theta_i$ using regular differentiation rules. For a given $\theta_i$, let us define:

$$\beta = \sum_{k \neq i} e^{\theta_k},$$ (2.19)

and

$$f(\theta_i) = \frac{1}{1+\beta e^{-\theta_i}} = (1+\beta e^{-\theta_i})^{-1}.$$ (2.20)

> It can now be shown that the derivative with respect to $\theta_i$ holds:

$$f'(\theta_i) = (1+\beta e^{-\theta_i})^{-2}\beta e^{-\theta_i},$$ (2.21)

which can take on the informative form of:

$$f'(\theta_i) = f(\theta_i)(1 - f(\theta_i)).$$ (2.22)

It should be noted that (2.21) holds for any constant $\beta$, and for $\beta=1$ it clearly reduces to the sigmoid activation function.

Note: Characterize the sigmoid function when its argument approaches 0, $\infty$ and $-\infty$. What undesired properties of the sigmoid function do these values entail when considered as an activation function?

![](img/574135cb1d7125b50cf484d943cdd676_55_0.png)

### SOL-18 CH.SOL- 2.15.

- 1. The logit value is simply obtained by substituting the values of the dependent variables and model coefficients into the linear logistic regression model, as follows:

$$\begin{split}
& logit = \beta_0 + \beta_1x_1 + \beta_2x_2 \\
& = -1.5 + 3 \cdot 1 + -0.5 \cdot 5 \\
& = -1.5 + 3 - 2.5 \\
& = -1.0
\end{split}
\qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad \qquad (2.23)$$

- 2. According to the natural relation between the logit and the odds, the following holds:

$$odds = e^{logit} = e^{\beta_0 + \beta_1 x_1 + \beta_2 x_2} = e^{-1} = 0.3678794.$$ (2.24)

- 3. The odds ratio is, by definition:

$$odds = \frac{P(y = 1)}{P(y = 0)},$$ (2.25)

so the logistic response function is:

$$P(y = 1) = \frac{1}{1 + e^{-logit}} = \frac{1}{1 + e^{1}} = 0.2689414.$$ (2.26)

![](img/574135cb1d7125b50cf484d943cdd676_55_1.png)

## 2.3.4 Truly Understanding Logistic Regression

### SOL-19 CH.SOL- 2.16.

- 1. Tumour eradication ($Y$) is the response variable and cancer type ($X$) is the explanatory variable.
- 2. Relative risk (RR) is the ratio of risk of an event in one group (e.g., exposed group) versus the risk of the event in the other group (e.g., non-exposed group). The odds ratio (OR) is the ratio of odds of an event in one group versus the odds of the event in the other group.
- 3. If we calculate odds ratio as a measure of association:

$$\hat{\theta} = \frac{560 \times 36}{69 \times 260} = 1.23745.$$ (2.27)

The odds ratio is larger than one, indicating that the odds for a breast cancer is more than the odds for a lung cancer to be eradicated. Notice however, that this result is too close to one, which prevents conclusive decision regarding the odds relation.

Additionally, if we calculate relative risk as a measure of association:

$$\mathrm{RR} = \frac{\frac{560}{560+260}}{\frac{69}{69+36}} = 1.0392.$$ (2.28)

- 4. The 95% confidence interval for the odds-ratio, $\theta$ is computed from the sample confidence interval for log odds ratio:

$$\hat{\sigma}\left(\log(\hat{\theta})\right) = \sqrt{\frac{1}{560} + \frac{1}{260} + \frac{1}{69} + \frac{1}{36}} = 0.21886.$$ (2.29)

Therefore, the 95% CI for $\log (\theta)$ is:

$$0.21886 \pm 1.95 \times 0.21886 = (-0.2101056, 0.6478256).$$ (2.30)

Therefore, the 95% CI for $\theta$ is:

$$(e^{-0.210}, e^{0.647}) = (0.810, 1.909).$$ (2.31)

- 5. The CI $(0.810, 1.909)$ contains 1, which indicates that the true odds ratio is not significantly different from 1 and there is not enough evidence that tumour eradication is dependent on cancer type.

![](img/574135cb1d7125b50cf484d943cdd676_57_0.png)

### SOL-20 CH.SOL- 2.17.

- 1. By using the defined values for $X_1$ and $X_2$, and the known logistic regression model, substitution yields:

$$\hat{p}(X) = \frac{e^{-6+0.05X_1+X_2}}{(1+e^{-6+0.05X_1+X_2})} = 0.3775.$$ (2.32)

- 2. The equation for the predicted probability tells us that:

$$\frac{e^{-6+0.05X_1+3.5}}{(1+e^{-6+0.05X_1+3.5})} = 0.5,$$ (2.33)

which is equivalent to constraining:

$$e^{-6+0.05X_1+3.5} = 1.$$ (2.34)

By taking the logarithm of both sides, we get that the number of milliseconds needed is:

$$X_1 = \frac{2.5}{0.05} = 50.$$ (2.35)

![](img/574135cb1d7125b50cf484d943cdd676_57_1.png)

### SOL-21 CH.SOL- 2.18.

*For the purpose of this exercise, it is instructive to pre-define z as:*

$$z(X_1, X_2) = -6.36 - 1.02 \times X_1 + 0.12 \times X_2.$$ (2.36)

- 1. By employing the classic logistic regression model:

$$odds = \exp(z(X_1, X_2)).$$ (2.37)

- 2. By substituting the given values of $X_1, X_2$ into $z(X_1, X_2)$, the probability holds:

$$p = \frac{\exp(z(1, 100))}{1 + \exp(z(1, 100))} = 0.99.$$ (2.38)

- 3. Yes. The coefficient for coffee consumption is positive (0.119) and the p-value is less than 0.05 (0.0304).

*Note: Can you describe the relation between these numerical relations and the positive conclusion?*

- 4. No. The p-value for this predictor is $0.3818 > 0.05$.

*Note: Can you explain why this inequality implicates a lack of statistical evidence?*

### SOL-22 CH.SOL- 2.19.

- 1. The estimated probability of improvement is:

$$\hat{\pi}(gum\ bacteria) = \frac{\exp(-4.8792 + 0.0258 \times gum\ bacteria)}{1 + \exp(-4.8792 + 0.0258 \times gum\ bacteria)}$$

*Hence, $\hat{\pi}(33) = 0.211868$.*

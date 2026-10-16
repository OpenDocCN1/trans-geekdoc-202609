
These three properties are pretty straightforward and just formalize what we normally mean by probability. A probability of an event is a number between zero and one. The probability of one event or another event happening is the sum of their individual probabilities as long as the two events don’t contain any of the same outcomes.

The *probability mass function* (pmf) makes life easier in describing probability for discrete sample spaces. It is a function \(p\) that takes outcomes \(\omega\) as input and gives back probabilities for those outcomes. The sum of the pmf across all outcomes in the sample space is one, \(\sum_{\omega\in\Omega} p(\omega)=1\), which is needed to satisfy the second property of probability.

The probability of an event is the sum of the pmf values of its constituent outcomes. For example, if the pmf of employment status is \(p(\text{employed})=0.60\), \(p(\text{unemployed})=0.05\), and \(p(\text{other})=0.35\), then the probability of event {employed, other} is \(P(\{\text{employed, other}\})=0.60+0.35=0.95\). This way of adding pmf values to get an overall probability works because of the third property of probability.

*Random variables* are a really useful concept in specifying the safety requirements of machine learning problems. A random variable \(X\) takes on a specific numerical value \(x\) when \(X\) is measured or observed; that numerical value is random. The set of all possible values of \(X\) is \(\mathcal{X}\). The probability function for the random variable \(X\) is denoted \(P_X\). Random variables can be discrete or continuous. They can also represent categorical outcomes by mapping the outcome values to a finite set of numbers, e.g. mapping {employed, unemployed, other} to {0, 1, 2}. The pmf of a discrete random variable is written as \(p_X(x)\).

Pmfs don’t exactly make sense for uncountably infinite sample spaces. So the *cumulative distribution function* (cdf) is used instead. It is the probability that a continuous random variable \(X\) takes a value less than or equal to some sample point \(x\), i.e. \(F_X(x)=P(X\leq x)\). An alternative representation is the *probability density function* (pdf) \(p_X(x)=\frac{d}{dx}F_X(x)\), the derivative of the cdf with respect to \(x\). The value of a pdf is not a probability, but integrating a pdf over a set yields a probability.

To better understand cdfs and pdfs, let’s look at one of the ThriveGuild features you’re going to use in your machine learning lending model: the income of the applicant. Income is a continuous random variable whose cdf may be, for example:

\[F_X(x)=\begin{cases}1-e^{-0.5x}, & x\geq 0\\0, & \text{otherwise}\end{cases}\]

Equation 3.2

Figure 3.1 shows what this distribution looks like and how to compute probabilities from it. It shows that the probability that the applicant’s income is less than or equal to 2 (in units such as ten thousand dollars) is \(1-e^{-0.5\cdot 2}=1-e^{-1}\approx 0.63\). Most borrowers tend to earn less than 2. The pdf is the derivative of the cdf.

'marginalize' here with the social marginalization that leads individuals and groups to be made powerless by being treated as insignificant.

The employment status feature and the loan approval label in the ThriveGuild model are random variables that have a joint pmf. For example, this multivariate function could be p(employed, approve) = 0.20, p(employed, deny) = 0.40, p(unemployed, approve) = 0.01, p(unemployed, deny) = 0.04, p(other, approve) = 0.10, and p(other, deny) = 0.25. This function is visualized as a table of probability values in Figure 3.2. Summing loan approval out from this joint pmf, you recover the marginal pmf for employment status given earlier. Summing employment status out, you get the marginal pmf for loan approval as p(approve) = 0.31 and p(deny) = 0.69.

### joint pmf of employment status and loan approval

| | employed | unemployed | other |
|---|---|---|---|
| approve | 0.20 | 0.01 | 0.10 |
| deny | 0.40 | 0.04 | 0.25 |

### marginal pmf of employment status

![](img/78fc6ae0a1bc731065313dc3a5886b2f_40_0.png)

### marginal pmf of loan approval

![](img/78fc6ae0a1bc731065313dc3a5886b2f_40_1.png)

Figure 3.2. Examples of marginalizing a joint distribution by summing out one of the random variables. Accessible caption. A table of the joint pmf has employment status as the columns and loan approval as the rows. The entries are the probabilities. Adding the numbers in the columns gives the marginal pmf of employment status. Adding the numbers in the rows gives the marginal pmf of loan approval.

Probabilities, pmfs, cdfs, and pdfs are all tools for quantifying aleatoric uncertainty. They are used to specify the requirements for the accuracy of models, which is critical for the first of the two parts of safety: risk minimization. A correct prediction is an event and the probability of that event is the accuracy. For example, working with the problem owner, you may specify that the ThriveGuild lending model must have at least a 0.92 probability of being correct. The accuracy of machine learning models and other similar measures of basic performance are the topic of Chapter 6 in Part 3 of the book.

## 3.3 Summary Statistics of Uncertainty

Full probability distributions are great to get going with problem specification, but can be unwieldy to deal with. It is easier to set problem specifications using summary statistics of probability distributions and random variables.

### 3.3.1 Expected Value and Variance

The most common statistic is the expected value of a random variable. It is the mean of its distribution: a typical value or long-run average outcome. It is computed as the integral of the pdf multiplied by the random variable:

E[X] = ∫_{-∞}^{∞} x p_X(x) dx.

Equation 3.4

Recall that in the example earlier, ThriveGuild borrowers had the income pdf 0.5e^{-0.5x} for x ≥ 0 and zero elsewhere. The expected value of income is thus ∫_0^∞ x0.5e^{-0.5x} dx = 2. When you have a bunch of samples drawn from the probability distribution of X, denoted {x_1, x_2, ..., x_n}, then you can compute an empirical version of the expected value, the sample mean, as x̄ = 1/n Σ_{i=1}^n x_i. Not only can you compute the expected value of a random variable alone, but also the expected value of any function of a random variable. It is the integral of the pdf multiplied by the function. Through expected values of performance, also known as risk, you can specify average behaviors of systems being within certain ranges for the purposes of safety.

How much variability in income should you plan for among ThriveGuild applicants? An important expected value is the variance E[(X − E[X])^2], which measures the spread of a distribution and helps answer the question. Its sample version, the sample variance is computed as 1/(n−1) Σ_{j=1}^n (x_j − x̄)^2. The correlation between two random variables X (e.g., income) and Y (e.g., loan approval) is also an expected value, E[XY], which tells you whether there is some sort of statistical relationship between the two random variables. The covariance, E[(X − E[X])(Y − E[Y])] = E[XY] − E[X]E[Y], tells you whether if one random variable increases, the other will also increase, and vice versa. These different expected values and summary statistics give different insights about aleatoric uncertainty that are to be constrained in the problem specification.

### 3.3.2 Information and Entropy

Although means, variances, correlations, and covariances capture a lot, there are other kinds of summary statistics that capture different insights needed to specify machine learning problems. A different way to summarize aleatoric uncertainty is through the information of random variables. Part of information theory, the information of a discrete random variable X with pmf p_X(x) is I(x) = −log(p_X(x)). This logarithm is usually in base 2. For very small probabilities close to zero, the information is very large. This makes sense since the occurrence of a rare event (an event with small probability) is deemed

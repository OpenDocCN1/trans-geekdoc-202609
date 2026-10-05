
## 7.2 Sampling framework

using a shovel to select balls from a bowl. A **random sample** is a sample found using simple random sampling. In the bowl activities, physical and virtual, we use simple random sampling to get random samples from the bowl.

**A population parameter** (or simply a **parameter**) is a numerical summary (number) that represents some characteristic of the population. A **sample statistic** (or simply a **statistic**) is a numerical summary computed from a sample. In the bowl activities the parameter of interest was the population proportion $p = 0.375$. Similarly, previously a sample of 50 balls was taken and 17 were red. A statistic is the *sample proportion* which in this example was $\hat{p} = 0.34$. How observe we use $p$ to represent the population proportion (parameter) and $\hat{p}$ for the sample proportion (statistic).

The **distribution** of lists is the set of the possible values in the list and how often they occur. The **sampling distribution of the sample proportion from each possible** random samples of a given size. To illustrate this concept recall that in Subsection 7.1.3 we drew three histograms shown in Figure 7.12. The histogram on the left, for example, constructed from taking 1000 random samples of size $n = 25$, finding the sample proportion for each sample and using these proportions to draw the histogram. This histogram is a good visual approximation of the *sampling distribution* of the sample proportion.

The *sampling distribution* can be a difficult concept to grasp right away:

- *The *sampling distribution of the sample proportion* is the distribution of *sample proportions*; it is constructed using exclusively sample proportions.*
- *Be careful as people learning this terminology sometimes confuse the *term distribution* with a *sample's distribution*. The latter can be understood as the distribution of the values in a given sample.*
- *A histogram from a simulation of sample proportions is only a visual approximation of the sampling distribution. It is not the exact distribution. Still, when the simulations produce a large number of sample proportions, the resulting histogram provides a good approximation of the sampling distribution. This was the case in Subsection 7.1.3 and the three histograms shown in Figure 7.12.

The lessons learned by performing the activities in Section 7.1 contribute to gaining insights about key characteristics of the *sampling distribution* of the sample proportion, namely:

- *The center of the *sampling distribution***
- *The effect of *sampling variation* on the *sampling distribution* and the effect of the sample size on this *sampling variation***
- *The shape of the *sampling distribution***

The first two points relate to measures of central tendency and dispersion, respectively. The last one provides a connection to one of the most important theorems in statistics: the Central Limit Theorem. In the next section, we formally study these characteristics.

## Learning check

(LC7.10) In the case of our bowl activity, what is the population parameter? Do we know its value? How can we know its value exactly?

(LC7.11) How did we ensure that the samples collected with the shovel were random?

## 7.3 The Central Limit Theorem

A fascinating result in statistics is that, when retrieving random samples from any population, the corresponding sample means follow a typical behavior: their histogram is bell-shaped and has very unique features. This is true regardless of the distribution of the population values and forms the basis of what we know as the Central Limit Theorem. Before fully describing it, we introduce a theoretical framework to construct this and other characteristics related to sampling.

### 7.3.1 Random variables

A simple theoretical framework can help formalize important properties of the sampling distribution of the sample proportion. To do this we modify the bowl activity slightly. Instead of using a shovel to select all 25 balls at once, we randomly select one ball at a time, 25 times. If the ball is red we call it a success and record a 1 (one); if it is not we call it a failure and record a 0 (zero). Then, we return the ball to the bowl so the proportion of red balls in the bowl does not change. This process is called a trial or a Bernoulli trial in honor of Jacob Bernoulli, a 17th-century mathematician who is among the first to work with these trials. Getting a sample of 25 balls is running 25 trials and getting 25 numbers, ones or zeros, representing whether or not we have observed red balls on each trial, respectively. The average of these 25 numbers (zeros or ones) precisely represents the proportion or red balls in a sample of 25 balls.

It is useful to represent a trial as a random variable. We use the uppercase letter $X$ and the subscript 1 as $X_1$ to denote the random variable for the first trial. After the first trial is completed, the color of the first ball is observed, the value of $X_1$ is realized as 1 if the ball is red or 0 if the ball is white. For example, if the first ball is red, we write $X_1 = 1$. Similarly, we use $X_2$ to represent the second trial. example, if the second ball is white, $X_2$ is realized as $X_2 = 0$, and so on. $X_1, X_2$, ... are random variables only before the trials have been performed. After the trials, they are just the *ones* or *zeros* representing red or white balls, respectively.

Moreover, since our experiment is to perform 25 trials and then find the average of them, this average before the trials are carried out, can also be expressed as a random variable:

$$\bar{X} = \frac{X_1 + X_2 + \dots + X_{25}}{25}$$

$\bar{X}$ is the observed sample. This is why we call $\bar{X}$ the sample proportion.

### 7.3.2 The sampling distribution

The distribution of $\bar{X}$ is the set of the possible values in the list and how often they occur. The sampling distribution of the sample proportion from each possible random samples of a given size. To illustrate this concept recall that in Subsection 7.1.3 we drew three histograms shown in Figure 7.12. This is why of the sampling distribution of the sample proportion.

### 7.3.3 The center of the distribution: The expected value

Since the distribution of $\bar{X}$ is composed of all the sample proportions that can be calculated for a given sample size, the center of this distribution can be understood as the average of all these proportions. This is the value we *expect* to get, on average, from all these sample proportions. This is why the center value of the sampling distribution is called the *expected value* of the sample proportion, and write $E(\bar{X})$. Based on probability theory, the mean of $\bar{X}$ happens to be equal to the population proportion of red balls in the bowl. In Subsection 7.1.1 we determined that population proportion was 900/2400 = 0.375, therefore

$E(\bar{X}) = p = 0.375.$

As an illustration, we noted in Subsection 7.1.3 when looking at the histograms in Figure 7.12 that all three histograms were centered at some value between 0.35 and

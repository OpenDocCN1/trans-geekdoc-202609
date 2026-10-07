
# Research Design and Statistical Analysis

b) Let p be probability of failure in the sample. If the null hypothesis is true, the mean of the sampling distribution of p is $\pi$ (.4) and its variance is $\pi(1 - \pi)/n$. In the study, only 12 of the 48 participants suffered a recurrence of symptoms after one year. Use the normal distribution to test the null hypothesis. State your conclusions.

c) We might want a better sense of the true probability of recurrence of symptoms. Calculate a 95% confidence interval and interpret your result.

d) In parts (b) and (c), we used the normal probability (z) table to draw inferences about a population probability. (i) What about the sampling probability of p is implied by our methods? (ii) What justifies this assumption? (iii) Would the mean of p be unjustifiable if the sample had only 10 people in it? Explain.

## 5.5 Sampling from nonnormal distribution

A population of scores is uniformly distributed between 0 and 1. This means that all values between 0 and 1 are equally likely and $f(y)$ (the probability of a score less than y) equals y. For example, $p(Y < .8) = .8$. The mean and standard deviation of this uniformly distributed population are .5 and $\sqrt{1/12}$.

- a) What is $p(Y < .6)$? (ii) What is the probability that in a sample of two scores both are less than .6? Express your answer as a probability raised to a power. (iii) What is the probability that in a sample of 20 scores are all less than .6?

- b) Assume that we draw many samples of 20 scores and calculate the mean of each sample. Describe the shape of the sampling distribution. What are its mean and standard deviation?

- c) Based on your answer to (b), what is the probability that the mean of 20 scores is less than .6? Would the same approach be appropriate in answering part (a) (iii)? Explain.

- d) Briefly state your justification for your approach to part (c).

## 5.6 Expected values and variances

We have a population in which $\pi = p(X=1) = .2$ and $1 - \pi = p(X=0) = .8$.

- a) Calculate the population mean, $\mu_x$, and variance, $\sigma_x^2 = E(X)$ and $var(X)$. Note that $E(X) = (\pi)(1) + (1 - \pi)(0)$ and $var(X) = E(X^2) - [E(X)]^2$. (ii) Assume that we draw samples of 3 from this population. What would be the variance of the sampling distribution of the mean?

- b) Assume we draw samples of 3. If we define the outcome of experiment as a value of $Y$ where $Y = \sum X$, there are four possible outcomes. Complete the following table ($s^2$ is the variance with $n$ in the denominator whereas $S^2$ is $n-1$ in the denominator):

| Y | $p(Y)$ | $\bar{X}$ | $\bar{S}_x^2$ | $S_x^2$ | $s_x^2$ |
|---|---|---|---|---|---|
| 0 | .851 | | | | |
| 1 | $(3)(.8)^2(.2)=.384 | | | | |
| 2 | $(3)(.8)(.2)^2=.096 | | | | |
| 3 | .208 | | | | |

- c) Using the entries in the table above, find (i) $E(Y)$, (ii) $E(\bar{X})$, (iii) $E(S_x^2)$, and (iv) $E(s_x^2)$.

- d) How do $E(Y)$ and $E(\bar{X})$ compare with the value of $E(X)$ in part (a)?

- e) How do $E(S_x^2)$ and $E(s_x^2)$ compare with the value of $var(X)$ in part (a)?

- f) What do your answers to parts (d) and (e) say about which statistics are biased or unbiased?

## 5.7 Confidence interval, hypothesis testing, and power

A national survey of many college students in 1983 yielded an “authoritarian” score of 52.8 and a standard deviation of 10.5. For all practical purposes, we may view these as population parameters.

- a) Suppose we wish to examine whether authoritarian attitudes have increased since the survey by examining a random sample of 50 students. Test $H_0$ and the rejection region assuming $\alpha=.05$.

- b) Assume that the mean of 50 samples is 56.0. Carry out the significance test and state your conclusion.

- c) Suppose the true population mean is 57.0. What is the power of your significance test?

- d) Based on your sample (assuming the population variance has stayed), what is the 95% confidence interval for the population mean?

- e) In part (d) you found the 95% confidence interval. What exactly is a 95% confidence interval? What exactly happens 95% of the time?

## 5.8 Properties of estimators

Two random samples are available from a population with unknown mean. Sample 1 has $n_1$ scores and a mean of $\bar{Y}_1$, sample 2 has $n_2$ scores and a mean of $\bar{Y}_2$. Consider two possible estimates of the population mean, $\mu$, that are based on both samples: One is the mean of the sample means,
$UM = \frac{\bar{Y}_1 + \bar{Y}_2}{2}$

and the other is the weighted mean of the sample means,
$WM = \frac{n_1\bar{Y}_1 + n_2\bar{Y}_2}{n_1 + n_2}$

In the following questions, remember that $E(\bar{Y}_i) = E(Y_i) = \mu_i$:

- a) Is $UM$ an unbiased estimator of the population mean? Show why or not.

- b) Is $WM$ an unbiased estimator of the population mean? Show why or not.

- c) Assume that $n_1=20$ and $n_2=80$, and the population variance, $\sigma^2$, equals 4. Calculate the variance of $UM$.

- d) Calculate the variance of $WM$. Is $UM$ or $WM$ a better estimate of the population mean? Why?

- e) Is either $UM$ or $WM$ a better estimate of the population mean than $\bar{Y}_1$? Why?

## 5.9 Linear combinations and effect size

Assume that we have a treatment (T) and a control (C) population for which $\mu_t$ is larger than $\mu_c$. Assume that both populations are normally distributed and have the same variance, $\sigma^2$.

- a) Let $T$ and $C$ be randomly sampled scores from their respective populations. Assume that $\mu_t$ is .5 larger than $\mu_c$. Express the mean and variance of the sampling distribution of $T-C$ as a function of $\sigma$ (see Appendix 5.1).

- b) What is the probability that a randomly chosen score from the treatment population will be higher than a randomly chosen score from the control population? (i.e., what is $p(T - C > 0)$?) You don't need numerical values for $\mu_t$, $\mu_c$, and $\sigma$.

- c) (i) what is the probability that the mean of randomly chosen scores from the treatment population will be larger than the mean of randomly chosen scores? (ii) What is the probability if $\mu_t$ is .2 larger than $\mu_c$?

## 5.10 effect of stratified sampling on variance

A population of voters consists of equal numbers of conservatives and liberals. Furthermore, .9 of liberals prefer the Democratic candidate in the upcoming election, whereas .3 of the conservatives prefer the Democratic candidate.

- a) What is $p_0$ the probability of sampling an individual from the entire population who prefers the Democratic candidate?

- b) The variance of a proportion $p$ is $p(1 - p)/n$ (see Appendix B for the proof). With this mind, what is the variance of the sampling distribution of $p_0$ the proportion of Democratic voters in a sample of 50 individuals who are randomly selected from the population of voters?

- c) Suppose you are a pollster who knows that the population is equally divided between liberals and conservatives, but you don't know what the proportion of Democratic voters is. You sample 50 individuals with the constraint that 25 are conservatives and 25 liberals; this referred to as stratified sampling.

- i. From the information presented at the start of this problem, what is the variance of the sampling distribution of $p_{dt}$ the proportion of Democratic voters in a sample of 25 liberals?

- ii. What is the variance of the sampling distribution of $p_{ds}$ the proportion of Democratic voters in a sample of 25 conservatives?

- iii. The proportion of Democrats in the stratified sample is $p_d = (1/2)(p_{dt} + p_{ds})$. What is the variance of the sampling distribution of $D$ when stratification is employed?

- iv. In view of your answers to (b) and (c) (iii), discuss the effect of stratification.

## 5.11 Confidence intervals and hypothesis testing

Instruction in problem-solving methods raised the scores of a sample of 225 students by an average of two points. A difference between the before and after scores was calculated for each student and the standard deviation of the differences was 13.6.

- a) Find the standard error of the difference.

- b) Using the result in part (a), find the .95% confidence interval for the difference in the means.

- c) Carry out the z test of the null hypothesis of no instructional effect; $\alpha = .05$.

## 5.12 Comparing between- and within-participant designs

Assume that we estimate the population variances from a previous study to $s_1^2 = 160$ and $s_2^2 = 240$.

- a) Assume that there is a new experiment with $n$ participants in each of two groups, one from each population. Express the variance of the difference between the means as a function of the variance estimates and $n$. (Appendix 5.1 should be helpful here.)

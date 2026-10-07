# Developing the Fundamentals of Hypothesis Testing

Now suppose the urn consists of 50 red and 50 black balls. Our assumption of independence leads us to the same probability of drawing three red balls in a row, .125. This time, however, the true probability if we select without replacement is $p(R_i$ and $R_j) = (50/100)(49/98) = .121$, and the true and inferred probabilities are quite close; thus, the violation of the independence assumption did not lead to a very large error.

There are two implications of examples that extend beyond simple probability calculations and violations of the independence assumption. First, violations may lead to wildly incorrect conclusions, as the urn with 10 marbles attends. Second, the consequences of violated assumptions may be more damaging when the sample size is large. Neither of these statements will be true for every inferential procedure, but they are often true and therefore bearing in mind.

# Exercises

+   4.1 [Interpreting a and power] Assume that in a particular research area 30% of the null hypotheses tested are true. Assume a very large number of experiments are conducted, each with $\alpha = .05$ and power =80.

+   a) What proportion of true null hypotheses will be rejected?
b) What proportion of false null hypotheses will not be rejected?
c) What proportion of nonrejected null hypotheses will actually be true?
d) What proportion of all null hypotheses will be rejected?

+   4.2 [Logic of hypothesis tests] For each of the following, state the null and alternative hypotheses:

+   a) The recovery rate for a disease is known to be 25%. A new drug is tried with a sample of people who have the disease to determine whether the probability of recovering is increased.
b) An experiment such as that in Exercise 3.1 is conducted to assess the evidence for the existence of ESP.
c) In the ESP experiment of Exercise 3.1, a proponent of ESP (Claire Voyant?) claims that she will be successful on greater than 60% of the trials.

+   4.3 [Calculations with binomial distribution] Use the binomial table (Appendix Table C.1) to find the rejection region in each of the following cases ($p$ is the population probability), and then use your answers to confirm your understanding of the *binomial* of distribution functions in R or SPSS:

| Case | $H_0$ | $H_1$ | n | a |
|---|---|---|---|---||
| (a) | $\pi = .25$ | $\pi > .25$ | 20 | .01 |
| (b) | $\pi = .25$ | $\pi > .25$ | 20 | .01 |
| (c) | $\pi = .25$ | $\pi < .25$ | 20 | .05 |
| (d) | $\pi = .5$ | $\pi 
eq .5$ | 20 | .01 |

+   4.4 [Interpreting $p$-values] In an experiment, data are collected such that when a test is conducted, the null hypothesis is rejected with $p = .003.

+   a) Can you conclude that $H_0$ is true with probability .003? Why or why not?
b) Can you conclude that $H_1$ is true with probability .997? Why or why not?
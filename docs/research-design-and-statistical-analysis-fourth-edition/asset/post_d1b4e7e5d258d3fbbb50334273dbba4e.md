
analyses. Confidence intervals and test statistics should then be calculated. Following exploratory and inferential analyses, the researcher is prepared to interpret the results and make decisions based upon them, including plans for replications or follow-up studies.

## Exercises

For this chapter, which integrates content from all of Part I, we do not provide a purpose for each problem. Instead, your understanding of the previous chapters will guide you to the solutions.

- a) Assume of -1, 0, and 1 are assigned to underachievers, higher achievers, and achievers, based on a test of motivation. If the proportions of the population in each category are 1/4, 1/2, and 1/4, what are the population mean and variance?
- b) Assume that a sample of two students is drawn from the population. What are the possible values of the mean of their two scores? What is the probability of each value? Construct a table of the possible means and their probabilities. Note that this is the sampling distribution of the mean for samples of size 2.
- c) What are the mean and variance of the sampling distribution constructed in part (b)?

7.2 Assume that the selection criteria for personnel for a mission to Mars are based on tests of motivation (M), physical fitness (P), and intelligence (I). The following population parameters have been established:

| M | P | I |
|---|---|---|---|
| $\mu$ | 62 | 66 | 60 |
| $\sigma$ | 28 | 20 | 13 |

M, P, and I are independently and normally distributed. The selection criterion (C) is a weighted average of each individual's score: $C = 25M + 25P + 5I$.

- a) What are $\mu_C$, the average criterion score in the population, and $\sigma_C$, the standard deviation of the population of criterion scores?
- b) Those selected for training the mission must be in the top 5% of the population with respect to C. What criterion score will serve as the cutoff?
- c) The five-person crew of a previous mission had a mean criterion score of 64.5. Find the 90% confidence interval. Does the limit indicate that this crew's mean score was significantly below the criterion score computed in part (b)?

7.3 In a study phase, each of 100 participants is shown a series of six objects for five seconds. In the following test phase, each participant is tested on six trials. On each trial, four objects are presented, one of which was present in the study phase. The participant's task is to choose the previously studied object on each test trial.

- a) If a participant is guessing, what is the probability of correct response on a single test trial?
- b) Assuming guessing, state the probabilities of possible outcomes (i.e., 0 correct, 1 correct, 6 correct) for a single participant.
- c) Assuming guessing, what is the expected number of participants exhibiting each outcome?
- d) Assuming guessing, what is the expected mean correct for each participant?
- e) What is the probability by chance a participant will exceed the expected number?

7.4 In the experiment described in 7.3, the actual distribution of outcomes

| Number Correct | 0 | 1 | 2 | 3 | 4 | 5 | 6 |
|---|---|---|---|---|---|---|---|
| Number of Participants | 12 | 30 | 32 | 19 | 6 | 1 | 0 |

- a) Assign a task to all participants who had more than the value in your answer to 7.3(d) and minus to all others. Then test whether participants have more correct responses than be expected by chance. You can do this by using a normal approximation to the binomial distribution: $z = \frac{y-np}{\sqrt{np(1-p)}}$. In part (a), we used the normal distribution to carry out a test of the null hypothesis of guessing. However, because we have scores of 100 participants, could calculate the observed mean and variance, and perform a t test.
- b) What is the observed mean of the 100 scores?
- c) What is the variance of the 100 scores?
- d) Calculate the t statistic and test the null hypothesis of chance.

7.5 Reading scores of 62 experimental volunteers were trained by reinforcement techniques. Pretest and posttest scores are in the file EX7_S.xlsx. Group 1 is the experimental group.

- a) Calculate the 95% confidence intervals for the scores for each group. State whether the change for each group is significant.
- b) Test the difference between groups in the average change score, assuming $\alpha = .05$ and the test is one-tailed.

7.6 The test in Exercise 7.5, part (b), is likely to have low power because the group sizes were small. Replicate the study

- a) Estimate Cohen's d for the difference between groups in mean change scores for the EX7_S.xlsx data. Use this result to determine the group size needed to have power = .9, assuming $n_1 = n_2$. Use a one-tailed test.
- b) Assuming the group you obtained in part (a), what power would you have for a one-tailed test that the group improved from pretest to posttest? Estimate the effect size based on the data.

7.7 In this chapter, we analyzed the memory data from independent designs in which some participants received a drug designed to improve memory and others received a placebo. We want to rerun the experiment, this time testing a group of participants before and after taking the drug. We have estimated Cohen's d to be 0.43 for the data from the previous experiment and wish to use those data to decide on the sample size for the new experiment.

- a) Assuming the population variances are the same in both the experimental and control groups, we estimate variance to be 12.5 from the data analyzed earlier. A reasonable estimate of the population correlation ($\rho$) is .6 for participants tested in both conditions. Given that the population variance of difference scores is $\sigma_1^2+\sigma_2^2-2\rho\sigma_1\sigma_2$, and if $\sigma^2=12.5$ and $\rho=.6$, we estimate the standard deviation of the difference scores.
- b) From the independent-groups experiment, we estimate the difference between the two population means to be 1.52. Use this information and your answer to part (a) to estimate Cohen's $d$.
- c) How many participants should run in this test-retest to have .8 detect a memory improvement corresponding to the value of $d$ calculated in part (b)?

7.8 A new drug was administered to several patients to reduce anxiety. One question is whether this drug has an effect on cognitive processes than a previously described drug. A clinical researcher compared response times (RTs) on a decision-making task for 30 participants who had been taking the new drug (Group 1) with RTs for 20 participants (Group 2) who had been taking the drug prescribed long for anxiety. The data is in the EX7_8.xlsx file.

- a) Explore the data and describe any aspects that might affect the error rates of the t test comparing the group members.
- b) Select a transformation of the data and explore the transformed data. Did the transformation address your concerns?
- c) Test the hypothesis that the drug slows responses in cognitive tasks.

7.9 Consider alternative approaches to analyzing the data of 7.8.

- a) Perform a trimmed test using the RT data.
- b) Compare the 95% confidence interval with that for the untrimmed data.
- c) Perform a Mann-Whitney U test on the same data.


# Chapter 5

# Further Development of the Foundations of Statistical Inference

## 5.1 Overview

In Chapter 2, we explored a subset of data in the study in which Royer and his colleagues collected accuracy scores and response times on simple arithmetic skills from students in first to eighth grades. Usually, this is a preliminary step in addressing questions about the data of a population of students represented by our sample. Among the many questions we ask of the data we collect are as follows:

- What is the average addition score of the population of first-graders?
- What are reasonable bounds on our estimate of the population average?

The answers to questions such as the first involve point estimates; we use sample data to estimate a point, a single parameter value, in the population of scores. The answer to questions such as the second involve interval estimates; we use sample data to estimate an interval within which we believe the population parameter falls.

There are many other questions we could ask of these data. For example,

- Does the average score of the sampled population differ from some standard set by the government? 
- Does the average score differ from that of some other population of first-graders, perhaps first-grade students taught by a different method?

These last queries imply tests of the null hypothesis, that are based on the logic presented in Chapter 4. Most researchers are primarily concerned with these questions. However, point and interval estimates of population parameters should take precedence. For example, rather than immediately asking whether there is a statistically significant difference between two means, we should first ask what the size of the observed difference is and place some bounds on our estimate. Testing for significance is equivalent to asking whether there is an effect, but our understanding of behavior in question will proceed more rapidly if we ask what the magnitude of the effect is, a question that encompasses the possibility that there is little or no effect.

Both estimates and significance tests are influenced by the variability in our data. The variability in the population distribution is reflected in the variability of the distribution of the sample data and in the distribution of sample statistics. The greater the variability, the more a sample statistic, such as the sample mean or variance, will vary from sample to; that is, the greater will be the variance of the sampling distribution of the statistic. As a result of sampling variability, no statistic from a single sample will exactly match the parameter it estimates, and inferences about the parameter may be in error. In this chapter, we consider the relation between the sampling distribution of a statistic and both estimation and hypothesis testing.

The major topics of this chapter are organized as follows:

- The use of sample statistics to estimate population parameters. Familiar statistics such as the mean and standard deviation are unusual estimators because they provide important information about the "typical" score and variability of scores in a population. However, other sample statistics can be used to estimate the average score or the variability in a population, such as the median and the IQR. We will see that the choice among estimators of a parameter rests on comparisons of characteristics of the sampling distributions of the sample statistics.

- The distribution of the sample mean plays a critical role in many inferential procedures. This is because the central limit theorem assures that the sampling distribution of the mean is approximately normal in shape over a wide range of circumstances. For this reason, we can use the normal distribution as a basis for probability computations using inferential procedures concerning means of populations.

- The normal distribution may be used to construct inferential estimates and hypothesis tests concerning population means. The construction and interpretation of interval estimates is introduced in this chapter. In addition, we present the use of the normal distribution to test hypotheses about means and to power calculations. The discussion of hypothesis testing and power calculations serves, in part, to emphasize that the logic of these procedures is the same regardless of the application. Relations among interval estimates, hypothesis tests, and power calculations are also discussed.

- The validity of the assumptions underlying our inferential procedures affects the validity of the inferences we draw from our data. Using confidence intervals and hypothesis tests based on the normal distribution, we discuss these assumptions and the consequences of violating them.

In this chapter, we will discuss sampling distributions and their role in estimating population parameters and testing hypotheses about those parameters. We introduce the normal distribution to exemplify these concepts and procedures, in part because the normal distribution plays several important roles in inferential procedures that we will study in subsequent chapters of this text.

## 5.2 Using Sample Statistics to Estimate Population Parameters

### 5.2.1 Populations, Samples, and Sampling Distributions

Usually, a researcher has a sample and wants to draw inferences about population. As we discussed in Chapter 4, there is basic problem in drawing inferences from sample to population: The values of sample statistics are not identical to those of population. For example, the sample mean will vary over independent replications of a study. Two important questions this variability raises:

- How is a particular statistic distributed over repeated samples?
- Can more than one statistic be used to estimate a population parameter? If so, how do we decide between these estimates?

These are some of the questions we will consider in Section 5.2. The answers require an understanding of sampling distributions, the topic we turn to.

### 5.2.2 What is a Sampling Distribution?

The concept of sampling distribution was introduced in Chapter 4, where we developed the binomial for proportions. However, the concept of sampling distribution is much more general than the context in which it was introduced. For example, consider the following study. Fifty individuals are randomly sampled from some well-defined population and asked to try a new brand of cereal. The number of grams of cereal they consume is recorded as a measure of enjoyment. If we wish to test whether the mean of population is different from the serving size of 40 grams. The mean weight of cereal consumed by our participants is 60 grams. If the sample mean changed from one sample to another, this value would provide strong evidence against the hypothesis that population mean equals 40, and would suggest that the new cereal is worth further. On the other hand, if the sample mean was quite variable over samples, a sample value of 60 grams could have well even when population mean was 40.

It is useful to perform many replications of the 50-participant sampling experiment, with each replication giving rise to a value of the mean, Y. If we tabulate all the possible values of Y and their associated relative frequencies of occurrence, the result is the sampling distribution of the mean for samples of 50. Knowing the properties of this sampling distribution will help evaluate inferences made from a single value of Y. If we know that the sampling distribution has little variability, we have considerable confidence that our estimate is close to the population parameter; conversely, we are less satisfied with an estimate when the variability of the sampling distribution is high. Further, as we shall see, if we have knowledge of the shape of the sampling distribution – e.g., that the population of scores is normally distributed – we can draw various inferences about the parameter.

### 5.2.3 Criteria for Estimators

We have established that researchers usually draw inferences about population parameters from their sample data. For example, they want to know the mean of the population, or estimate some measure of variability (e.g., the standard deviation). In fact, there is

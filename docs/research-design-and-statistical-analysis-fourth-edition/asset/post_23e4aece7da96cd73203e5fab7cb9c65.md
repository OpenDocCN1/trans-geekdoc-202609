
## 5.5 Inferences About Population Means

In this section, we apply concepts developed in Chapter 4 to inferences based on the normal distribution. The application of normal probabilities assumes knowledge of the population variance. Using the data that we have collected, we can only estimate that variance, a fact that introduces some error into our calculations. Although more accurate results require using the t distribution, we will wait until the next chapter to develop that. For now, we will continue to focus on the normal distribution to further illustrate and extend ideas introduced in Chapter 4.

One of the measures available to us in the Seasons data set is the seasonal total cholesterol score (TC1, ..., TC4). We calculated the average over the four seasons for those participants who were measured in all four seasons (some participants met at least one of the four seasons); data are in the file, TC_Data; the link is on the Seasons page on the website. We used the sample data to estimate the TC of a subpopulation – namely males 50 and older (Agegrps 3 and 4 in the file). These are in the file TC_Data over 50. Keeping in mind that doctors frequently recommend that TC should be at 200 or more, we wanted to know whether the mean in the subpopulation differed from this recommended maximum level. In what follows, we analyze the TC data of the 117 males in Agegrps 3 and 4 to estimate the mean of a population of such individuals and to test the null hypothesis that the population mean equals 200.

### 5.5.1 A First Look at the Data

As we emphasized in Chapter 2, we should explore our data before conducting any inferential procedures. We begin our exploration of the TC data with Figure 5.2, which presents a

![](img/53d3130502f4ff3b15cbe3697d6e8c5a_132_0.png)

Figure 5.2 Box plot of total cholesterol scores of men age 50 and older.

a box plot of the data overlaid with individual scores. Several aspects of the plot are interesting. First, because the median approximately bisects the box and the whiskers are of equal length, it appears that the distribution is symmetric. Second, the median is clearly above the recommended maximum TC level of 200. Furthermore, the lower hinge is also above 200, meaning that at least 75% of the participants have TC scores above the recommended maximum. There is some good news, however. None of the participants have a TC level as high as 300, a value that would clearly signal a high-risk patient. Nevertheless, the box plot warns that cholesterol level may be a problem for many of the patients. One other point should be noted about the box plot. There is one extreme outlier, a TC score close to 100. This is such an unusual case that it might be wise to recheck this patient’s data entry error.

The Q–Q plot in Figure 5.3 shows the expected z scores (on the x-axis) under the assumption that TC is normally distributed. The majority of scores fall on or very near the straight line; one clear exception is the outlier noted previously. We can confirm that the data are approximately normally distributed by observing a nonsignificant result of the Shapiro-Wilk test in R (using the shapiro.test function in the stats package), which can be thought of as the square of the correlation in the Q–Q plot. Although these test results provide confirmation of normality, we should be aware that there are occasions where

![](img/53d3130502f4ff3b15cbe3697d6e8c5a_133_0.png)

Figure 5.3 Q–Q plot of the total cholesterol scores of men age 50 and older.

when samples are large, even small departures from normality may yield significant results; when samples are small (≤ 30), the Shapiro-Wilk test has low power (Razali & Wah, 2011). But statistically significant deviations from the expected normal distribution may have little effect on subsequent tests that assume normality. In view of this, we are concerned only when the Q-Q plot signals marked departures from normality or the presence of outliers that require our attention.

Given the orders of data exploration, it seems reasonable to assume that the population from which the TC scores were sampled follows a normal distribution. Therefore, our subsequent analyses will be based on the standard normal distribution. We were troubled by the one outlier, so we performed the analyses to be described with and without that. We found little difference in our two sets of results and therefore report the analyses based on the entire sample of 117 scores. The values we need for this example are n = 117, Y = 224.684, and s = 31.302. We are now ready to estimate an interval containing the population mean, and whether that mean differs significantly from the theoretical value of 200.

### 5.5.2 A Confidence Interval for μ

In Chapter 4, we introduced the inferential procedure of hypothesis testing. In this section, we introduce a new inferential procedure called interval estimation. Interval estimation answers the question, “What is the plausible range of values of θ?” where θ is a population parameter. Thus, interval estimation is a very general and useful procedure that is almost invariably more meaningful than the binary outcome of a significance test (i.e., reject or fail to reject the null hypothesis).

Although various population parameters may be estimated, we are currently interested in estimating the mean of a population. Let’s begin by illustrating the procedure for our current example. Y = 224.684 provides a point estimate of μ, the population mean TC score for men older than 50 years. However, the sample mean might be close to the population, or it might reflect considerable error. To have a sense of the accuracy of such estimates, we calculate an interval estimate or confidence interval (CI), a pair of numbers which provide reasonable bounds for the parameter being estimated.

The procedure for constructing a CI for μ is based on what we have learned about the sampling distribution of the sample mean; namely, the distribution of the sample mean is normal with expected value equal to μ and variance divided by the sample size, n. Imagine many samples of 117 TC scores each from a population of TC scores. Further assume that the mean of each sample is converted into a standardized (z) score by subtracting the mean of the sampling distribution and then dividing the difference by the standard error (SE) of the mean. Suppose we want a 95% CI. If that Table C.2 tells us that 95% of the z scores will lie between -1.96 and 1.96, then we can be 95% confident that the population mean is contained within this interval.

To construct the interval, we use the formula $\bar{y} \pm z^* \frac{s}{\sqrt{n}}$. For a 95% CI, $z^* = 1.96$. Using our values: $224.684 \pm 1.96 \frac{31.302}{\sqrt{117}} = 224.684 \pm 5.672$. This gives an interval of (219.012, 230.356). In other words, we are 95% confident that the true mean TC score for men over 50 is between 219.01 and 230.36.

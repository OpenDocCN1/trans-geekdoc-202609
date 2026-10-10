
# Analysis of Variance (ANOVA)

We noted earlier that research questions are usually comparative. Typically, the goal is to compare two or more interfaces or interaction techniques to determine which is better. By "better" we mean superior performance on one or more dependent variables, such as task completion time, error rate, task re-tries, presses of the `Backspace` key, target re-entries, and so on. It is interesting that the test is called the "analysis of variance" yet our interest is in overall performance:

![](images/B9780443140969000129/fx001.jpg)

The question above refers to time – the overall, average, or mean, time that was observed and measured. Little can be inferred from a single observation made on one participant for one trial under one test condition. So, the mean is calculated for each test condition over multiple users and often over multiple trials of a representative task. The mean is a more stable measure since it represents the central tendency in a collection of measurements.

In some situations, multiple trials of a task are administered to investigate learning effects (see [Chapter 5](#Chp005_203-242_B9780443140969000117.xhtml), Longitudinal Studies); but, often, multiple trials are used just to obtain stable and representative measurements. Nevertheless, it is the difference in the means, not the variances, that interests us. Note that while the above research question is certainly important, the statistical question pursued is not a question. It is a statement known as the *null hypothesis*:

![](images/B9780443140969000129/fx002.jpg)

There is an assumption of "no difference," which is a reasonable starting point. The ANOVA tests the data to determine the likelihood that the null hypothesis is true (tenable) or false (rejected). In most cases, the researcher seeks to reject the null hypothesis. By convention, a statistically significant result means there is little likelihood the null hypothesis is true. The conclusion in such case is that (i) there is a difference in the means, (ii) the difference is statistically significant, and (iii) the difference was caused by distinguishable properties in the test conditions. Let's see how this is done.

Consider a hypothetical experiment where 10 participants perform a few repetitions of a task using two interaction techniques. The techniques could be anything, for example, use of a finger vs. a stylus for input on a smartphone. A task is chosen that is representative of common interactions, yet likely to expose inherent differences. An example might be entering an appointment in a calendar application. How long does this take using finger input? How long does it take using stylus input? For this discussion, we'll just refer to the interaction methods as A and B. Bear in mind that the experiment has a single factor (interaction method) with two levels (A and B).

Performance is measured on a dependent variable such as task completion time (in seconds) and the means are computed for each participant over a few trials. Then the means are computed for each method. Two example outcomes for this hypothetical experiment are shown in the bar charts in [Fig. 6.3](#Chp006_243-291_B9780443140969000129.xhtml#f0020).

![Figure 6.3 Difference in task completion time (in seconds) across two interaction methods, A and B. Two hypothetical outcomes are shown: (a) The difference is statistically significant. (b) The difference is not statistically significant. See text for discussion.](images/B9780443140969000129/gr003.jpg)

**Figure 6.3** Difference in task completion time (in seconds) across two interaction methods, A and B. Two hypothetical outcomes are shown: (a) The difference is statistically significant. (b) The difference is not statistically significant. See text for discussion.

The mean task completion times are the same in [Fig. 6.3a](#Chp006_243-291_B9780443140969000129.xhtml#f0020) and [Fig. 6.3b](#Chp006_243-291_B9780443140969000129.xhtml#f0020). However, the annotations proclaim vastly different outcomes. In [Fig. 6.3a](#Chp006_243-291_B9780443140969000129.xhtml#f0020), the difference in the means is statistically significant. This implies that in all likelihood the difference observed was real and was due to distinguishing properties of method A vs. method B. Simply put, method A is faster than method B. Do the test again, and there is a pretty good chance the result will be similar.

In [Fig. 6.3b](#Chp006_243-291_B9780443140969000129.xhtml#f0020), the difference in the means is not statistically significant. This implies the difference in the means is likely due to chance. There is no reasonable basis to suggest that either method is faster than the other. Do the test again and the outcome could very well be reversed. Despite the dramatically different interpretations, the two examples seem the same: a task completion time of 4.5 seconds for method A vs. 5.5 seconds for method B. How is this? The answer lies in the variability in the observations – the variance. Let's have a closer look.

[Fig. 6.4a](#Chp006_243-291_B9780443140969000129.xhtml#f0025) gives the data for the simulation in [Fig. 6.3a](#Chp006_243-291_B9780443140969000129.xhtml#f0020) as the mean task completion time (in seconds) for each participant for each method along with the overall mean and standard deviation for each method. [Fig. 6.4b](#Chp006_243-291_B9780443140969000129.xhtml#f0025) shows the corresponding bar chart embellished with error bars. The error bars show ±1 standard deviation about the means. The variance is the square of the standard deviation; however, it is more common in research papers to report standard deviations because the units of the standard deviation and the mean are the same ("seconds" in this case).

![Figure 6.4 Simulation in Fig. 6.3a. (a) Data. (b) Bar chart. Error bars show ±1 standard deviation about the means.](images/B9780443140969000129/gr004.jpg)

**Figure 6.4** Simulation in [Fig. 6.3a](#Chp006_243-291_B9780443140969000129.xhtml#f0020). (a) Data. (b) Bar chart. Error bars show ±1 standard deviation about the means.

The step-by-step process of doing an ANOVA on the data in [Fig. 6.4a](#Chp006_243-291_B9780443140969000129.xhtml#f0025) depends on the statistics app used. The result is a table similar to that shown in [Fig. 6.5](#Chp006_243-291_B9780443140969000129.xhtml#f0030).^([^(101)](#fn101))

![Figure 6.5 Analysis of variance table for data in Fig. 6.4a.](images/B9780443140969000129/gr005.jpg)

**Figure 6.5** Analysis of variance table for data in [Fig. 6.4a](#Chp006_243-291_B9780443140969000129.xhtml#f0025).

The most important statistic in the table is the "`p`-Value." The `p`-value is the probability of obtaining the observed data if the null hypothesis is true. A low probability indicates that the differences in the means are unlikely to have occurred in view of the null hypothesis. A high probability indicates that the differences in the means may simply be a chance outcome. With `p` = .0121, there is a fairly low probability – less than 2% – that the difference is simply a chance outcome. In all likelihood, there are distinguishing properties in the methods that caused the difference. Note the term "caused" in the preceding sentence. One reason experimental research is so valuable is that conclusions of a cause-and-effect nature are possible.

At the same time, it is important to acknowledge an important limitation in statistical procedures such as the ANOVA, and statistics in general. Statistics can determine the probability of an event – in this case, the probability that observed data are consistent with the null hypothesis – but statistics do not explain or interpret. For this, the researcher draws upon insight and other resources, such as examinations of the behaviours and responses involved.

It is common in experimental research that significance, in a statistical sense, requires `p` less than .05, or a 1 in 20 probability.^([^(102)](#fn102))


The data are the `x`-coordinates of selection, mapped so that 0.0 is the centre of the target. Negative values are selections on the near side, positive values are selections on the far side. Although the data include selections near the centre of the target and selections on either side, the researcher questions whether the data follow a normal distribution. To determine this, the Lilliefors test is used. See [Fig. 6.31](#Chp006_243-291_B9780443140969000129.xhtml#f0160). As seen in the last three lines of output, the test statistic (`M` = 0.2054) exceeds the critical value (`CV` = 0.1920); therefore, the null hypothesis is rejected. The conclusion is that the selection coordinates for the sequence of trials are not normally distributed.

![Figure 6.31 Lilliefors test for normality on selection coordinates from a target selection task.](images/B9780443140969000129/gr031.jpg)

Figure 6.31 Lilliefors test for normality on selection coordinates from a target selection task.

One issue to consider in this example is whether the selection coordinates include outliers. Were the responses, as a whole, just slightly deviate – enough to yield a non-normal distribution? Or, were there one or two particular responses that were so deviate, or abnormal, as to be deemed outliers? This issue was studied in Chapter [2](#Chp002_31-91_B9780443140969000087.xhtml) (The Human Factor). See section [2.7.6](#Chp002_31-91_B9780443140969000087.xhtml) (p. 83).

Most sources detailing the K-S or Lilliefors tests include graphs contrasting the observed and expected cumulative probabilities. [Fig. 6.32](#Chp006_243-291_B9780443140969000129.xhtml#f0165) is an example for the analysis in [Fig. 6.31](#Chp006_243-291_B9780443140969000129.xhtml#f0160). The test statistic (`M`) is the largest vertical distance between the observed and expected cumulative distributions.

![Figure 6.32 Observed vs. expected cumulative probability distributions for Example 2 (Fig. 6.31). The test statistic (M) is the largest vertical distance between the two lines.](images/B9780443140969000129/gr032.jpg)

[Figure 6.32](#Chp006_243-291_B9780443140969000129.xhtml#cf0645) Observed vs. expected cumulative probability distributions for Example 2 ([Fig. 6.31](#Chp006_243-291_B9780443140969000129.xhtml#f0160)). The test statistic (`M`) is the largest vertical distance between the two lines.

### 6.4.3 Example 3

Example 2 tested the normality assumption for a single sequence of 20 trials. However, the experiment included several independent variables and multiple blocks for each condition [[302]](#Chp006_243-291_B9780443140969000129.xhtml#br1510). In all, there were 1920 sequences of trials. The Lilliefors utility in GoStats has options to analyse and summarize many data sequences in one pass. As an example, the file `lilliefors-ex3.txt` contains the data for 12 sequences of trials from this experiment. If the utility is run using the "Single-line" and "Meta results" options, the output summarizes the analyses over all sequences. See [Fig. 6.33](#Chp006_243-291_B9780443140969000129.xhtml#f0170). The single-line output option gives, for each sequence, the number of samples, the mean, the standard deviation, the test statistic, and the critical value. These are followed by the result of the test of the null hypothesis: Rejected or `Not_Rejected`. The Meta results option (last line in [Fig. 6.33](#Chp006_243-291_B9780443140969000129.xhtml#f0170)) summarizes the analyses. In the example, nine sequences were deemed normally distributed and three sequences were deemed not normally distributed.

![Figure 6.33 Lilliefors test for multiple sequences of data.](images/B9780443140969000129/gr033.jpg)

Figure 6.33 Lilliefors test for multiple sequences of data.

Other HCI research using the Lilliefors test is hereby cited [[70](#Chp006_243-291_B9780443140969000129.xhtml#br0350), [165](#Chp006_243-291_B9780443140969000129.xhtml#br0825), [182]](#Chp006_243-291_B9780443140969000129.xhtml#br0910). See also student exercises [6-10](#Chp006_243-291_B9780443140969000129.xhtml#o0055) and [6-11](#Chp006_243-291_B9780443140969000129.xhtml#o0060) at the end of this chapter.

## 6.5 Non-parametric tests for ordinal data

Non-parametric tests make no assumptions about the probability distribution of the population from which the underlying data are obtained. In the examples ahead, non-parametric tests are described as they are typically used in HCI research – to analyse ordinal (and sometimes interval) data. The data are typically obtained through questionnaires (e.g., using a Likert scale), preference ratings, or assessments on a scale. Rather than using direct measurement of human responses, the data are obtained subjectively, from participants, or using heuristics or other non-empirical or semi-empirical methods.

The four most common non-parametric procedures are the Mann-Whitney U test, the Wilcoxon Signed-Ranks test, the Kruskal-Wallis test, and the Friedman test. Each is used in a particular context, depending on the number of test conditions and the experiment design. [Fig. 6.34](#Chp006_243-291_B9780443140969000129.xhtml#f0175) illustrates. Between-subjects and within-subjects designs generate data that are from `independent samples` and `correlated samples`, respectively, as shown in the figure. Between-subjects designs generate independent samples because different participants are tested with each condition. Within-subjects designs generate correlated samples (aka dependent samples) because the same participants are tested with each condition. Bear in mind that the conditions are levels of a single independent variable (factor) in the experiment.

![Figure 6.34 Choosing a non-parametric test based on experiment design and number of conditions.](images/B9780443140969000129/gr034.jpg)

Figure 6.34 Choosing a non-parametric test based on experiment design and number of conditions.

The non-parametric tests in [Fig. 6.34](#Chp006_243-291_B9780443140969000129.xhtml#f0175) are demonstrated below through a series of hypothetical examples. As the problems are described and the data presented, it will be apparent which test is appropriate. Since the Kruskal-Wallis and Friedman tests operate on three or more conditions, a statistically significant outcome is usually followed with post hoc pairwise comparisons. This is also demonstrated.

For each example, two versions of the data analysis are provided. One uses a commercial statistics application. The other uses the GoStats utility available on this book's web site. The results are identical for both analyses. Let's begin.

### 6.5.1 Mann-Whitney U test

A researcher seeks to determine if there is a difference in the political leaning of Mac users vs. PC users. Are Mac or PC users more likely to have political views leaning to the "left" or "right?" The experimenter randomly selects 10 Mac users and 10 PC users.^([^(112)](#fn112))

![Figure 6.35 Assessments of the political leanings for 10 Mac users and 10 PC users. See text for discussion.](images/B9780443140969000129/gr035.jpg)

[Figure 6.35](#Chp006_243-291_B9780443140969000129.xhtml#cf0695) Assessments of the political leanings for 10 Mac users and 10 PC users. See text for discussion.

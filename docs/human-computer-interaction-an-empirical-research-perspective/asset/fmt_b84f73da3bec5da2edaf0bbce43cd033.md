
The mean scores (not shown) are 3.7 for the Mac users and 4.5 for the PC users. Evidently, the PC users are a little more “right-leaning.” But, is the difference real or is it just an artefact of the variability in responses? The data are potentially interval-scale, but the researcher senses that the intervals between successive codes are not equal – because they are based on a qualitative assessment. The data are at least ordinal; so, a non-parametric test is chosen to answer this question. There are two conditions and the assignment is between-subjects, therefore the appropriate test is Mann-Whitney U (see [Fig. 6.34](#Chp006_243-291_B9780443140969000129.xhtml#f0175)). The results are shown in [Fig. 6.36](#Chp006_243-291_B9780443140969000129.xhtml#f0185) using a commercial app and using GoStats. There are numerous behind-the-scenes data manipulations and calculations leading to the test statistic, *U*.^([^(113)](#fn113))

![Figure 6.36 Mann-Whitney U test for the political leanings of Mac and PC users. (a) Commercial app. (b) GoStats.](images/B9780443140969000129/gr036.jpg)

[Figure 6.36](#Chp006_243-291_B9780443140969000129.xhtml#cf0705) Mann-Whitney U test for the political leanings of Mac and PC users. (a) Commercial app. (b) GoStats.

For the example, *U* = 31.0 with *p* = .1418 (corrected for ties). Since *p* is greater than .05, the differences in the assessments fail to meet the customary threshold for statistical significance. The conclusion is that there is no difference in the political leanings of Mac users and PC users (*U* = 31.0, *p* > .05).

### 6.5.2 Wilcoxon Signed-Ranks test

A researcher is interested in comparing two new designs for media players. There is a particular interest in knowing if the designs differ in “cool appeal” for young users. Ten young tech-savvy participants are recruited and given demos of the two media players (MPA, MPB). The participants are asked to rate the designs for “cool appeal” on a linear scale from 1 (*not cool at all*) to 10 (*really cool*). The results are given in [Fig. 6.37](#Chp006_243-291_B9780443140969000129.xhtml#f0190).

![Figure 6.37 Ratings for “cool appeal” of two media players. See text for discussion.](images/B9780443140969000129/gr037.jpg)

[Figure 6.37](#Chp006_243-291_B9780443140969000129.xhtml#cf0720) Ratings for “cool appeal” of two media players. See text for discussion.

The mean ratings (not shown) are 6.4 for media player A and 3.7 for B. It seems media player A fares quite well compared to media player B. However, there was some variability in the responses, so perhaps the difference was just a chance outcome. To test if the differences in the ratings are real, a statistical test is used. Since the data are interval-scale (see discussion for Example 1), a non-parametric test is chosen. There are two test conditions and the design is within-subjects, therefore the Wilcoxon Signed-Ranks test is appropriate (see [Fig. 6.34](#Chp006_243-291_B9780443140969000129.xhtml#f0175)). The results are shown in [Fig. 6.38](#Chp006_243-291_B9780443140969000129.xhtml#f0195) using a commercial app and using GoStats.

![Figure 6.38 Wilcoxon Signed-Ranks test for the “cool appeal” ratings for two media players. (a) Commercial app. (b) GoStats.](images/B9780443140969000129/gr038.jpg)

[Figure 6.38](#Chp006_243-291_B9780443140969000129.xhtml#cf0730) Wilcoxon Signed-Ranks test for the “cool appeal” ratings for two media players. (a) Commercial app. (b) GoStats.

The test statistic for the Wilcoxon Signed-Ranks test is a normalized *z* score. For the example, *z* = -2.254 with *p* = .0242 (corrected for ties). Since *p* is less than .05, the customary threshold for statistical significance is exceeded. The conclusion is that the two media players differ in “cool appeal” (*z* = -2.254, *p* < .05).

### 6.5.3 Kruskal-Wallis test

The designers of a new vehicle GPS tracker are wondering if age will be a factor in the acceptance of the product. They decide to conduct a small experiment to find out. Eight participants are recruited from each of three age groups: 20-29 years, 30-39 years, and 40-49 years. The participants are given a demo of the new GPS tracker, and then asked if they liked it enough to consider purchasing it for personal use. They respond on a linear scale from 1 (*definitely no*) to 10 (*definitely yes*). The results are given in [Fig. 6.39](#Chp006_243-291_B9780443140969000129.xhtml#f0200).

![Figure 6.39 Acceptability scores by three age groups for a GPS tracker. See text for discussion.](images/B9780443140969000129/gr039.jpg)

[Figure 6.39](#Chp006_243-291_B9780443140969000129.xhtml#cf0735) Acceptability scores by three age groups for a GPS tracker. See text for discussion.

The mean scores by age group (not shown) are 7.1 (20-29), 4.0 (30-39), and 2.9 (40-49). There is a difference, since the 20-29 year age group gave higher acceptability scores than the other two groups. However, there was also variability in the scores. So the question remains: Are the differences in the acceptability scores among the three age groups statistically significant, or are the differences simply a chance outcome? Since the data are interval-scale (see discussion for Example 1), a non-parametric test is chosen to help answer the question. There are three age groups and the design is between-subjects, therefore the Kruskal-Wallis test is appropriate (see [Fig. 6.34](#Chp006_243-291_B9780443140969000129.xhtml#f0175)). The results are shown in [Fig. 6.40](#Chp006_243-291_B9780443140969000129.xhtml#f0205) using a commercial app and using GoStats.

![Figure 6.40 Kruskal-Wallis test for acceptability of a GPS tracker by three age groups. (a) Commercial app. (b) GoStats (with post hoc comparisons).](images/B9780443140969000129/gr040.jpg)

Figure 6.40 Kruskal-Wallis test for acceptability of a GPS tracker by three age groups. (a) Commercial app. (b) GoStats (with post hoc comparisons).

The test statistic is *H*, which follows a chi-square distribution with *df* = *k* - 1 (*k* is the number of groups). In the example, *H* = 9.605 with *p* = .0082 (corrected for ties). Since *p* is below the customary threshold for statistical significance (.05), the test shows a significant effect of age group on the acceptability of the GPS tracker design (*χ*²![Image](images/B9780443140969000129/si1.png) = 9.605, *df* = 2, *p* < .05).

There are three age groups, therefore post hoc pairwise comparisons are needed to determine which age groups differ significantly from one another. This is available in GoStats by checking the “Post hoc tests” box in [Fig. 6.40](#Chp006_243-291_B9780443140969000129.xhtml#f0205)b.^([^(114)](#fn114))

### 6.5.4 Friedman test

A researcher implemented four variations of a search engine interface (A, B, C, and D). Each uses a different dialogue for users to build queries. The researcher wishes to know if the interfaces differ in the quality of results they produce. Eight participants are recruited and are given a demonstration of each interface and then asked to do a series of search tasks. The “quality of results” is assessed for each participant and for each search engine. The assessment uses a linear scale from 1 (*very poor*) to 100 (*very good*). A Latin square was used to balance the order of conditions, but this isn't important here. The results are given in [Fig. 6.41](#Chp006_243-291_B9780443140969000129.xhtml#f0210).

![Figure 6.41 Quality of results for four variations of a search engine interface. See text for discussion.](images/B9780443140969000129/gr041.jpg)

[Figure 6.41](#Chp006_243-291_B9780443140969000129.xhtml#cf0765) Quality of results for four variations of a search engine interface. See text for discussion.

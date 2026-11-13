
hypothesis when the sample size is large (30 or more). The z test statistic for the mean is found by the following equations:

\(z = \frac{\bar{x} - \mu}{\sigma_{\bar{x}}} = \frac{\bar{x} - \mu}{\frac{\sigma}{\sqrt{n}}}\) (6.12)

where \(\bar{x}\) is the observed mean, \(\mu\) is the expected mean, \(\sigma\) is the population standard deviation and \(n\) is the sample size. \(\sigma_{\bar{x}}\) is the standard error of the mean. Therefore, when testing the null hypothesis about a mean, the z scores are units of the standard deviation. The z test statistic for the proportion is calculated differently, as:

\(z = \frac{\hat{p} - p}{\sigma_{\hat{p}}} = \frac{\hat{p} - p}{\sqrt{\frac{p(1-\hat{p})}{n}}}\) (6.13)

where \(\hat{p}\) is the observed proportion, \(p\) is the expected proportion and \(\sigma_{\hat{p}}\) is the standard error of the proportion.

For example, suppose we have a sample of 120 farms from a rural area which has a mean size of 130 ha. The population of farms in the area has a mean size of 65 ha and a standard deviation of 114 ha. H₀ is that there is no difference between the sample mean and the population mean. The z score for this example is:

\(z = \frac{130 - 65}{\frac{114}{\sqrt{120}}} = 6.246\) (6.14)

The z test statistic is assumed to have a normal probability distribution, which can be depicted as a bell-shaped curve. As shown in Figure 6.10, the curve shows the probabilities associated with different z scores. It is peaked when z = 0, which is the mean of the distribution, and its tails approach, but never reach, the horizontal axis. The total area under the curve equals 1.0. The proportion of the area under the curve between two z scores is the probability of any feature or value falling between the two z scores.

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_317_0.png)

Figure 6.10 Distribution of the z test statistic.

For example, the area under the curve between the two z-values of -0.5 and 0.5 (as shaded in Figure 6.10) is 38.29 per cent of the total area covered by the curve; thus, there is a 38.29 per cent probability of any feature or value falling between the two z scores. The probability of a feature or value not occurring between the two scores (that is, outside the shaded area) is 100.0 per cent – 38.29 per cent = 61.71 per cent.

The probabilities associated with z scores form the basis of decisions about whether to reject or accept the null hypothesis. The probability at which such a decision is made is known as the **significance level**, denoted by $\alpha$. This is also the probability of making the mistake of rejecting H₀ when it is actually valid. The typical choices for $\alpha$ are 0.05, 0.01 and 0.10, with 0.05 being most common. The absolute z score at the chosen significance level is called the **critical value**. The critical value separates the area under the normal curve of the z test statistic into critical and non-critical regions (Figure 6.11).

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_318_0.png)

Figure 6.11 Critical values and critical regions of the distribution of the z scores.

The critical region encompasses the test statistics whose absolute values are equal to or larger than the critical value. Any z score in the critical region leads to rejection of H₀. All z scores in the non-critical region lead us to accept H₀. For the previous example of 120 farms in a rural area, a z score of 6.246 is exceptionally large, which is located in the critical region of $\alpha = 0.01$. Indeed, the probability of getting a z score of 6.246 is less than 0.0000000006, which is extremely small. Therefore, the mean size of 130 ha of the farm sample is significantly different from the population mean, which is very unlikely to occur by chance, and H₀ can be confidently rejected.

The exact probability of getting a value of the test statistic of a given magnitude if the null hypothesis is true is called the **p-value**. The **p-value** is twice the area of the extreme region (tail area) bounded by the test score under the normal curve in the probability distribution of the test statistic (Figure 6.12). If the z score calculated for a sample has a p-value of equal to or less than the significance level, H₀ should be rejected; otherwise, H₀ cannot be rejected. The significance level is usually specified before doing a significance testing. The spatial pattern analysis tools in GIS commonly report the p-value associated with the calculated z score. Reject the null hypothesis of a random spatial pattern or no spatial pattern if the p-value <= alpha (the significance level, for example, 0.05); accept the null hypothesis if the p-value > alpha.

![](img/8aad3fa01ca9db86bd50bb2edb9a3134_319_0.png)

Figure 6.12 Finding p-values in the probability distribution of the z scores.

## 6.4.2 Nearest Neighbour Analysis

Nearest neighbour analysis involves measuring the distance of each feature to its nearest neighbour, then comparing the observed distances with that expected from a random spatial pattern of features. It was originally developed to analyse the spatial distribution of plant species (Clark and Evans 1954) and is now one of the standard tools in GIS for measuring point patterns. Nearest neighbour analysis involves calculating the ratio between the observed and expected average or mean distance between two points and their nearest neighbours to produce the nearest neighbour statistic R. The mean distance expected from a random pattern of points, $r_e$, is calculated as:

$r_e = 0.5\sqrt{\frac{A}{n}}$ (6.15)

where A is the size of the study area and n is the number of points. The mean observed distance, $r_o$, is calculated as:

$r_o = \frac{\sum_{i=1}^n d_i}{n}$ (6.16)

where $d_i$ is the distance between the ith point to its nearest neighbour. R is then calculated as \( R = r_o / r_e \). This gives R values within the range 0.0–2.1491. A value of R = 0 represents perfect clustering, where all points occupy exactly the same location. Thus, a clustered pattern tends to have an R value towards 0. A value of 2.1491 is obtained when a regularly dispersed pattern is present, in which points form a triangular lattice, so that every point has an equal distance from its six nearest neighbours and the mean distance to the nearest neighbour is maximised. A value of 1.0 indicates a random pattern, where the observed mean distance is equal to the expected mean distance. The following rules are used to describe a spatial pattern using R:

- IF R < 1, THEN it shows a tendency towards clustering.
- IF R = 1, THEN it shows a random pattern.
- IF R > 1, THEN it shows a tendency towards dispersion.

However, an R value other than 1.0 does not by itself suggest that the features have some form of spatial preference, and it may occur by chance or as a result of sampling error. The probability of an R value occurring by chance is established through significance testing using the z test statistic. H₀ states that the sample R does not equal to 1.0 due to sampling error or as the result of a random process. The z test statistic is calculated as:

\( z = \frac{r_o - r_e}{\sigma_{\bar{x}}} \) (6.17)

\( \sigma_{\bar{x}} = \frac{0.26136}{\sqrt{n \left( \frac{n}{A} \right)}} \) (6.18)

where \(\sigma_{\bar{x}}\) is the standard error. The p-value associated with a z score can then be assessed for testing H₀.

For example, the peasant distribution depicted in Figures 6.4 and 6.6 has an R value of 0.500566; therefore, it shows a clustered pattern. The z score for the R value is -5.652536, and the p-value is less than 0.000001. The p-value indicates that the probability of getting this z score is very small. There is less than 0.0001 per cent likelihood that this clustered pattern could be the result of random chance. Therefore, H₀ is rejected and the conclusion can be made that peasants in the catchment tend to be clustered, and this clustered pattern does not occur by chance and is statistically significant.

There are three main problems with nearest neighbour analysis. First, the R statistic is highly dependent on the size and shape of the study area. A long and narrow area may result in a relatively low R value, as the points tend to be close to each other. If the study area is large compared with the extent of the point distribution, a low R value would be obtained. However, if the same points are tightly enclosed by the boundary of the study area, a large R value would be produced. Therefore, the boundary must be carefully drawn by considering the phenomena under investigation, and comparing results of nearest neighbour analysis is most appropriate when the study area is fixed. The second problem is that the same R value could be obtained from very different point patterns, as the R statistic only relates to the distance between points and does not account for other characteristics of the spatial arrangements of the points, such as angular configuration. Moreover, the

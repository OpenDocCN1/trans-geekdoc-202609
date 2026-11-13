calculated as \( R = r_o / r_e \). This gives \( R \) values within the range 0.0–2.1491. A value of \( R = 0 \) represents perfect clustering, where all points occupy exactly the same location. Thus, a clustered pattern tends to have an \( R \) value towards 0. A value of 2.1491 is obtained when a regularly dispersed pattern is present, in which points form a triangular lattice, so that every point has an equal distance from its six nearest neighbours and the mean distance to the nearest neighbour is maximised. A value of 1.0 indicates a random pattern, where the observed mean distance is equal to the expected mean distance. The following rules are used to describe a spatial pattern using \( R \):

+   - IF \( R < 1 \), THEN it shows a tendency towards clustering.
+   - IF \( R = 1 \), THEN it shows a random pattern.
+   - IF \( R > 1 \), THEN it shows a tendency towards dispersion.

However, an \( R \) value other than 1.0 does not by itself suggest that the features have some form of spatial preference, and it may occur by chance or as a result of sampling error. The probability of an \( R \) value occurring by chance is established through significance testing using the \( z \) test statistic. \( H_o \) states that the sample \( R \) does not equal to 1.0 due to sampling error or as the result of a random process. The \( z \) test statistic is calculated as:

```
\( z = \frac{r_o - r_e}{\sigma_{\bar{x}}} \) (6.17)

\( \sigma_{\bar{x}} = \frac{0.26136}{\sqrt{n \left( \frac{n}{A} \right)}} \) (6.18)
```

where \( \sigma_{\bar{x}} \) is the standard error. The \( p \)-value associated with a \( z \) score can then be assessed for testing \( H_o \).

For example, the peasant distribution depicted in Figures 6.4 and 6.6 has an \( R \) value of 0.500566; therefore, it shows a clustered pattern. The \( z \) score for the \( R \) value is -5.652536, and the \( p \)-value is less than 0.000001. The \( p \)-value indicates that the probability of getting this \( z \) score is very small. There is less than 0.0001 per cent likelihood that this clustered pattern could be the result of random chance. Therefore, \( H_o \) is rejected and the conclusion can be made that peasants in the catchment tend to be clustered, and this clustered pattern does not occur by chance and is statistically significant.

There are three main problems with nearest neighbour analysis. First, the \( R \) statistic is highly dependent on the size and shape of the study area. A long and narrow area may result in a relatively low \( R \) value, as the points tend to be close to each other. If the study area is large compared with the extent of the point distribution, a low \( R \) value would be obtained. However, if the same points are tightly enclosed by the boundary of the study area, a large \( R \) value would be produced. Therefore, the boundary must be carefully drawn by considering the phenomena under investigation, and comparing results of nearest neighbour analysis is most appropriate when the study area is fixed. The second problem is that the same \( R \) value could be obtained from very different point patterns, as the \( R \) statistic only relates to the distance between points and does not account for other characteristics of the spatial arrangements of the points, such as angular configuration. Moreover, the
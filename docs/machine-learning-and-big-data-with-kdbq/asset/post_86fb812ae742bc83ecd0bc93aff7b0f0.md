
# Basic Overview of Statistics

```
// concordance
concordance: ((x>x2) and (y>y2)) or ((x<x2) and (y<y2));
// discordance
discordance: ((x>x2) and (y<y2)) or ((x<x2) and (y>y2));
// output triplet
:(concordance;discordance; not concordance or discordance);
```

The outcome of the concordanceRoutine function is a triplet of binary numbers, where only one of the triplets can be true, or 1b, denoting whether the pair of pairs is concordant/discordant/neither of these.
The example of the function is:

```
r1:(3.1;3.4);
r2:(3.3;5.7);
.quant.stats.concordanceRoutine[r1;r2];
```

giving:

```
10b
```

This denotes that the pair of pairs is concordant. Kendall’s r correlation.
Further, we create a function for the calculation of the rank function takes two arguments, sample to compare variable X and sample for variable Y:

Calculate the r coefficient for two randomly distributed vectors:

```
x: 100?1;
y: 100?1;
.quant.stats.kendallTauRank[x;y];
```

The value is close to zero, confirming the nature of the vectors x and y.
For the sake of completeness, we calculate the r coefficient for perfectly aligned vectors:

```
x: 100?1;
y: y;
.quant.stats.kendallTauRank[x;y];
```

```
1f
```

# 218 DATA SCIENCE

Further, we utilise r and define Somers' D in function somersD:

```
quantQ.stats.somersD:[yS;xS]
// xS, yS -- arrays of values to calculate D
// calculate Somers' D using Kendall's Tau Rank
// .quantQ.stats.kendallTauRank[xS;yS]%quantQ.stats.kendallTauRank[xS;xS];
```

We test the implementation for two random vectors:

```
x: 1007.1;
y: 1007.1;
quantQ.stats.somersD[y;x];
```

The result verifies the independence of two vectors, though not in the form of a statistic
but rather indicates.

For two continuously distributed random variables without mass points, Somers'
D is symmetric:

```
.quantQ.stats.somersD[x;y];
```

```
-0.02424242
```

The asymmetry appears when discretely observed points are assessed, with a possible
overlap in sample values. Let us define a discrete sample now:

```
x: 10072;
y: 10073;
```

and calculate Somers' D relative to both X and Y:

```
.quantQ.stats.somersD[x;y];
```

```
0.1553156
```

and

```
.quantQ.stats.somersD[x;y];
```

```
0.1163116
```

There is an asymmetry in the outcome. On the other hand, Kendall's r is symmetric:

```
.quantQ.stats.kendallTauRank[x;y];
```

```
0.1511111
```

and

```
.quantQ.stats.kendallTauRank[y;x];
```

```
0.1511111
```

# Basic Overview of Statistics

Further, we proceed with Somers' D for X being binary variable:

```
.quantQ.stats.somersDBX:[yS;xS]
// xS, yS -- arrays of values to calculate D, xS being binary
// return modified Somers' D
:0.5x1_0.quantQ.stats.somersD[yS;xS];
;
```

which gives for a random sample:

```
x:10072;
y:10071;
.quantQ.stats.somersDBX[y;x];
```

This suggests a seeming alignment in variables. Without critical values, though, there is no statistical power to support our claim.

Further, we implement the Somers' D for a case when X is binary, and Y is an integer. The modified definition has a different notion of a tie, which is calculated for the second argument alone. Before we proceed with the definition, we define the concordance routine:

```
quantQ.stats.concordanceRoutineBinaryXIntegerY:[row1;row2]
// row -- pair of observations (xj,yj) with J=1,2
// XJ -- being binary
// YJ -- being integers
// explicitly x's and y's
x1: first row1;
y1: last row1;
x2: first row2;
y2: last row2;
// concordance
concordance((x1<x2) and (y1>y2)) or ((x1<x2) and (y1<y2));
// discordance
discordance((x1>>x2) and (y1<y2)) or ((x1<x2) and (y1>y2));
// tie
t:(x1<x2) and (y1>y2);
// output is triplet
:(concordance;discordance;tie);
```

and then define the adjusted Somers' D:

```
.quantQ.stats.somersDBXIntegerY:[yS;xS]
// xS, yS -- arrays of values to calculate D
// xS -- being binary
// yS -- being integer
stats: sum[.quantQ.stats.concordanceRoutineBinaryXIntegerY/:y:(1+(x?y)][t]
// t: flip(xS);
// Somers' D
:stats[0]-stats[1]+stats[2]);
```

# 220 DATA SCIENCE

Let us run it for example of randomly distributed arrays, one with binary and the other with integer:

```
x:10072;
y:10074;
quantQ.stats.somersIntegerY[y;x]
```

The value is rather small, but without a statistical test, such an assertion is descriptive.

Finally, we implement Kruskal's y. First, function kruskalGamma takes two arguments: two samples of random variables which were examined:

```
quantQ.stats.kruskalGamma:[x;y]
// xS, yS arrays of values to compare the rank
// aggregate statistics
stats: sum[.quantQ.stats.concordanceRoutineBinaryXIntegerY/:y..(1+x?y)][t]
// each t: flip(x;y)
// return gamma
{stats[0]-stats[1]%stats[0]+stats[1]};
```

Let us test the function against a pair of random variables:

```
x:100?0;
y:100?10;
quantQ.stats.kruskalGamma[x;y]
```

```
-0.0048485
```

The value is small and suggests no alignment. To test such statement, we also implement:

```
quant.stats.tKruskal:y
// xS, yS arrays of values to compare the rank
// calculate Kruskal's gamma
gamma: .quantQ.stats.kruskalGamma[x;y]
// count of combinations
stats: sum[.quantQ.stats.concordanceRoutineBinaryXIntegerY/:y..(1+x?y)][t]
// each t: flip(x;y)
// return t_gamma
gamma=sqrt(stats[0]+stats[1])%(count[xS]+count[xS]*1-gamma);
```

The transformed y then reads:

```
.quant.stats.tKruskal[x;y]
```

```
-0.0031125
```

# Basic Overview of Statistics 221

In order to perform a proper two-sided test against normally distributed critical values, we run:

```
.quantQ.stats.pValueTwoSided .quantQ.stats.tKruskal[x;y]
```

```
1f
```

The outcome suggests we cannot reject the null hypothesis at any level. This confirms the true nature of the data, which are without any link.

# 2.3.8 Multiple Hypothesis Testing

Finally we mention an important problem which is crucial to be aware when working with data. Let us imagine: we have dependent variable Y and 100 features, X^(1), X^(2), ..., X^(100). Further, let us assume that there is no true correlation between the dependent variable and each of the features. We calculate the correlation between the dependent variable and each feature, one by one, and assess the statistical hypothesis that the correlation is equal to 0.0 using tp. What will be the result? Let us illustrate it right now using 100 observations for every variable:

First, we generate the dependent variable:

```
y:100?0;
```

and then generate 100 features and assess it with the tStatsCorr function, where we calculate tp based on correlation between y and new feature, and save it to an array:

```
draws: [[x].quantQ.stats.tStatsCorr[y;100?0];count 100?0]]
til 100
```

12.5 depicts the histogram of draws by binnedHist with 40 bins. The values are distributed within a range spanning from -2.87 to 3.26. The histograms show a distribution similar in shape to the normal distribution. Importantly, illustrates our assertion made previously that the statistic is a random variable drawn from a given distribution. This means that even when we use the null hypothesis, we get statistics with an extreme value given we made enough draws. Thus, if we perform hypothesis testing multiple times, we may end up with a false conclusion.

The histogram has been produced:

```
.quantQ.stats.getHistogram[];.quantQ.stats.histBin[40]] draws
```

Let us look further into the outcome of the simulation exercise in more detail. The values of the tp span [-2.87, 3.26], which suggests that we may reject the null hypothesis for some values. The p-values for the left tail of the distribution are:

```
10#.quantQ.stats.pValueLeftSide each asc draws
0.005 0.005 0.005 0.005 0.005 0.005 0.005 0.005 0.001
```

# 222 DATA SCIENCE

![](img/97f581128bd0b85683d4c69d94242_246_0.png)

**FIGURE 12.5** Histogram of $t_ho$ for 1000 realisations under the null

and for the right tail of the distribution, where we properly adjust the $p$-value to correspond to percentile:

```
{1-x} each -10 = .quantQ.stats.pValueRightSided each asc draws
```

0.99 0.99 0.99 0.99 0.99 0.995 0.995 0.995 0.995 0.995

Given the value of 0.005 is the smallest value in the map between distribution value and p-values, we do realize extreme values in the distribution. How many such observation out of 1000 realisations have exceeded the 0.05 confidence level to reject the null hypothesis? We can answer the question numerically as:

```
sum 0.05>=.quantQ.stats.pValueTwoSided abs draws
```

52

Thus, 52 out of 1000 observations are rejected. This corresponds to statistical properties of the $t_ho$ under null being distributed according the given distribution. This numerical exercise does not contradict the asymptotic behaviour, i.e. normal distribution, which may be seen as verification (not proof though) of the presented statements.

The previous example illustrates the fundamental issue with multiple testing. The problem occurs when we simultaneously test the number of hypotheses, or family of

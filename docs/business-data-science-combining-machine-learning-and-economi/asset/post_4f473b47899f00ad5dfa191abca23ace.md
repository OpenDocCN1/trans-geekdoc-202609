
$$
\mathbf { Y } _ { T ^ { + 1 } } ( 0 ) = \begin { array } { l l l l l } y _ { 1 1 } ( 0 ) & y _ { 1 2 } ( 0 ) & \cdots & y _ { 1 T } ( 0 ) & ? \\ ( y _ { 2 1 } ( 0 ) & y _ { 2 2 } ( 0 ) & \cdots & y _ { 2 T } ( 0 ) & y _ { 2 T + 1 } ( 0 ) \\ \vdots & \vdots & & \vdots & \ \\ y _ { J 1 } ( 0 ) & y _ { J 2 } ( 0 ) & \cdots & y _ { J T } ( 0 ) & y _ { J T + 1 } ( 0 ) \end { array } ,
\tag { 6 . 2 0 }
$$

and if you look forward to future time points you will continue to miss only the first entry for each column.

Given this available data, a synthetic controls analysis first builds a model to predict $y _ { 1 t } ( 0 )$ from $\mathrm { y } _ { - 1 t } ( 0 ) = [ \mathrm { y } _ { 2 t } ( 0 ) \ldots \mathrm { y } _ { J t } ( 0 ) ] ^ { \prime }$. This model is estimated using the fully observed data from periods $t \leq T$ and is then used to predict the unobserved control values $y _ { 1 T + 1 } ( 0 ), y _ { 1 T + 2 } ( 0 )$, etc. The original synthetic controls work of Abadie and Gardeazabal [2003] uses positive weights summing to one to combine the control series when predicting the treatment series. However, you should feel free to use whatever regression model works best for prediction in your application. Since there are typically many control series $( J )$ relative to the number of time periods $( T )$, it will often make sense to use a regularized regression like the AICc lasso.

## **ALGORITHM 16** **Synthetic Controls**

- Build a regression model for $\mathbb { E } \left[ y _ { 1 t } ( 0 ) | y _ { - 1 t } ( 0 ) \right]$, and estimate this regression using data from time periods $t = 1 \ldots T$.
- Use this regression to predict $\hat { y } _ { 1 T + 1 } ( 0 ), \hat { y } _ { 1 T + 2 } ( 0 )$, etc., and estimate the treatment effect at each time point as follows:

$$
\hat { \boldsymbol { y } } _ { 1 T + s } = \boldsymbol { y } _ { 1 T + s } ( \mathbf { 1 } ) - \hat { \boldsymbol { y } } _ { 1 T + s } ( 0 ) .
$$

To illustrate the approach, we will revisit the data example from Abadie and Gardeazabal [2003] concerning the economic costs of terrorism in the Basque region of Spain. Beginning with a single killing in the summer of 1968, the terrorist group ETA began a campaign of killing and kidnapping that continued, with periodic cease fires, until 2010. The violence was high from the late 1970s through the early 1990s, with a peak of 92 people killed and 13 kidnapped in 1980. Almost 70% of the deaths occurred in the Basque country, and Basque business owners were common kidnapping targets.

Abadie and Gardeazabal ask the question: "How much did the ETA campaign harm the economy of the Basque country?" In addition to the obvious and tragic human cost of terrorism, the threat of violence will also deter investment and lower productivity. To answer this question, we can look at how the Basque region performed in comparison to the other regions in Spain (which experienced significantly less violence). For data, we have the GDP per capita (measured in 1986 \$1000 USD) from 1955 through 1990 for each of the 17 regions in Spain. This data was obtained from the `Synth` package for R, which also implements the original estimators from Abadie and Gardeazabal. After some wrangling, it yields a matrix of the form in Equation 6.20 with the treated, Basque, region in the first row and the 16 “control” region series below. We print a portion of the matrix here:

```R
> round(y[1:5,11:19],2)
           1965  1966  1967  1968  1969  1970  1971  1972  1973
Basque Country (Pais Vasco) 5.47 5.55 5.61 5.85 6.08 6.17 6.28 6.56 6.81
Andalucia                  2.58 2.69 2.80 2.99 3.18 3.35 3.52 3.76 3.99
Aragon                     3.75 3.88 4.02 4.24 4.48 4.60 4.72 5.00 5.28
Principado De Asturias     3.74 3.91 4.07 4.31 4.55 4.63 4.70 5.02 5.35
Baleares (Islas)           5.18 5.47 5.74 6.16 6.58 6.89 7.17 7.57 7.96
```

Since the terrorism campaign started midway through 1968, we will assume that the first treated year is 1969 (i.e., $T = 1968$; results don’t change much if $T = 1967$). We then create a simple function called `synthc` to execute Algorithm 16 using a `gamlr` AICc lasso for regression:

```R
> synthc <- function(j, tyear=1968, ...){
+   y0t <- t(y[,1:(tyear-1954)])
+   fit <- gamlr( y0t[,-j], y0t[,j], ...)
+   y0hat <- predict(fit, t(y[,-j,]) [,1])
+   return(list(w=coef(fit)[,1], y0hat=y0hat))
+ }
```

Running `synthc` for $j = 1$, we find that the selected model for predicting untreated per capita GDP in the Basque region has nonzero positive weights on Castilla y León, the largest region bordering the Basque country, as well as on the Mediterranean region of Murcia and on the capital, Madrid. There are negative loadings on Valencia and the Balearic Islands, indicating that *after* controlling for León, Madrid, and Murcia, an *extra* increase in, say, Valencia's GDP tends to correspond to a decrease in GDP for the Basque country.

```
> sc <- synhc(1, lmr=1e-4)
> sc$w [sc$w!=0]
```

| | Baleares | Castilla y Leon | Valencia | Madrid | Murcia |
| --- | --- | --- | --- | --- | --- |
| intercept | 0.8324923 | -0.1436622 | 0.5159924 | -0.3581780 | 0.4263979 | 0.8928448 |

These coefficients can then be used to predict what GDP per capita *would* have been in the Basque country if the ETA had not existed. This happens inside *synhc* with the creation of $y _ { 0 } \mathrm { h a t }$:

```
+ y0hat <- predict(fit, t[y[-j,]])
```

Note that we are predicting the synthetic control $\hat { y } _ { i t } ( 0 )$ for all $t$, not just for $t$ after 1968. *Figure 6.7* shows the synthetic control series, $\hat { y } _ { i t } ( 0 )$, against the observed series, $y _ { i t }$. The observed series is untreated until 1968, so $y _ { i t } = y _ { i t } ( 0 )$, and treated afterward, so $y _ { i t } = y _ { i t } ( 1 )$. The left panel of *Figure 6.7* shows a clear break between the two series after 1968, and the results indicate a cost of terrorism ($\widehat { \alpha } _ { i t }$) as high as \$1000 per capita in 1980.

![](img/315929ad4bddd26368466d02e06e2385_270_0.png)

![](img/315929ad4bddd26368466d02e06e2385_270_1.png)

FIGURE 6.7: Synthetic controls analysis of the economic effects of Basque (ETA) terrorism. Per capita GDP values are in 1986 \$1000 USD units. On the left, you can see the synthetic (no terrorism) GDP against the observed GDP. The right shows the difference between these counterfactuals against the available *placebos*: the difference between synthetic and realized GDP series for the 16 other regions in Spain.

How significant are these differences? For uncertainty quantification with synthetic controls, we can use *permutation testing* to create a sample from the null distribution. Under this method, you compare the estimated treatment effects to results obtained using the same methods on *placebo* units: regions where you know that no treatment has been applied. In this case, the placebo units are the 16 non-Basque regions of Spain. We can use `synthc` to replicate the synthetic control estimation across the series for these regions and then compare $\hat { y } _ { i t } ( 0 )$ to the observed $y _ { i t } ( 0 )$. We do this using a `parSapply` from the parallel library, which allows multiple regions to be predicted simultaneously.

```
```r
> # permutation test
> library(parallel)
> cl <- makeCluster (detectCores())
> clusterExport (cl, c("y", "gam1r", "synthc"))
>
> gety0 <- function(j) { synthc(j, lmr=1e-4)$y0hat }
> Ysynth <- parSapply(cl, 1:nrow(y), gety0)
> diff <- Ysynth - t(y)
```
```

The resulting difference matrix, `diff`, contains the difference between synthetic and observed series, $\hat { y } _ { i t } ( 0 ) - y _ { i t }$, for every region in Spain. Only the first column of `diff` contains actual treatment effect estimates (for years after 1968). The other columns are full of placebo effect estimates: draws from the null distribution of what the method would predict as the treatment effect in the case where no treatment was actually applied.

The right panel of *Figure 6.7* shows all of these differences. The Basque (treatment) series is highlighted. You can see that it is indeed among the largest of the 17 estimated differences, indicating a low *p*-value (i.e., it is rare under the null hypothesis). One placebo series showing a large difference corresponds to Madrid, the capital region of Spain. It is plausible that the relationship between Madrid and the rest of Spain is different before and after


available at time $t$. More precisely, $\mathbb{E}_t[\cdot] = \mathbb{E}[\cdot|\mathcal{F}_t]$. $\mathbb{V}[\cdot]$ will denote the variance operator. Depending on the context, probabilities will be written simply $P$, but sometimes we will use the heavier notation $\mathbb{P}$. Probability density functions (pdfs) will be denoted with lowercase letters ($f$) and cumulative distribution functions (cdfs) with uppercase letters ($F$). We will write equality in distribution as $X \stackrel{d}{=} Y$, which is equivalent to $F_X(z) = F_Y(z)$ for all $z$ on the support of the variables. For a random process $X_t$, we say that it is **stationary** if the law of $X_t$ is constant through time, i.e., $X_t \stackrel{d}{=} X_s$, where $\stackrel{d}{=}$ means equality in distribution. Sometimes, asymptotic behaviors will be characterized with the usual Landau notation $o(\cdot)$ and $O(\cdot)$. The symbol $\propto$ refers to proportionality: $x \propto y$ means that $x$ is proportional to $y$. With respect to derivatives, we use the standard notation $\frac{\partial}{\partial x}$ when differentiating with respect to $x$. We resort to the compact symbol $\nabla$ when all derivatives are computed (gradient vector). In equations, the left-hand side and right-hand side can be written more compactly: l.h.s. and r.h.s., respectively.

Finally, we turn to functions. We list a few below:

- $1_{\{x\}}$: the indicator function of the condition $x$, which is equal to one if $x$ is true and to zero otherwise.
- $\phi(\cdot)$ and $\Phi(\cdot)$ are the standard Gaussian pdf and cdf.
- $\text{card}(\cdot) = \#(\cdot)$ are two notations for the cardinal function which evaluates the number of elements in a given set (provided as argument of the function).
- $\lfloor \cdot \rfloor$ is the integer part function.
- for a real number $x$, $[x]^+$ is the positive part of $x$, that is $\max(0, x)$.
- $\tanh(\cdot)$ is the hyperbolic tangent: $\tanh(x) = \frac{e^x - e^{-x}}{e^x + e^{-x}}.$
- $\text{ReLu}(\cdot)$ is the rectified linear unit: $\text{ReLu}(x) = \max(0, x)$.
- $s(\cdot)$ will be the softmax function: $s(\mathbf{x})_i = \frac{e^{x_i}}{\sum_{j=1}^J e^{x_j}}$, where the subscript $i$ refers to the $i^{th}$ element of the vector.

### 1.2 Dataset

Throughout the book, and for the sake of **reproducibility**, we will illustrate the concepts we present with examples of implementation based on a single financial dataset available at https://github.com/shokru/mlfactor.github.io/tree/master/material. This dataset comprises information on 1,207 stocks listed in the US (possibly originating from Canada or Mexico). The time range starts in November 1998 and ends in March 2019. For each point in time, 93 **characteristics** describe the firms in the sample. These attributes cover a wide range of topics:

- **valuation** (earning yields, accounting ratios);
- **profitability** and quality (return on equity);
- **momentum** and technical analysis (past returns, relative strength index);
- **risk** (volatilities);
- estimates (earnings-per-share);
- volume and liquidity (share turnover).

The sample is not perfectly rectangular: there are no missing points, but the number of firms and their attributes is not constant through time. This makes the computations in the backtest more tricky, but also more realistic.

```r
library(tidyverse)  # Activate the data science package
library(lubridate)  # Activate the date management package
load("data_ml.RData") # Load the data
data_ml <- data_ml %>%
  filter(date > "1999-12-31",
         date < "2019-01-01") %>%
  arrange(stock_id, date)
data_ml[1:6, 1:6]   # Sample values
```

```
## # A tibble: 6 x 6
##   stock_id date      Advt_12M_Usd Advt_3M_Usd Advt_6M_Usd Asset_Turnover
##   <int>   <date>         <dbl>      <dbl>      <dbl>      <dbl>
## 1     1 2000-01-31      0.41      0.39      0.42      0.19
## 2     1 2000-02-29      0.41      0.39      0.42      0.19
## 3     1 2000-03-31      0.4      0.37      0.37      0.2
## 4     1 2000-04-30      0.39      0.36      0.37      0.2
## 5     1 2000-05-31      0.4      0.42      0.4      0.2
## 6     1 2000-06-30      0.41      0.47      0.42      0.21
```

The data has 99 columns and 268336 rows. The first two columns indicate the stock identifier and the date. The next 93 columns are the features (see Table 17.1 in the Appendix for details). The last four columns are the labels. The points are sampled at the monthly frequency. As is always the case in practice, the number of assets changes with time, as is shown in Figure 1.1.

```r
data_ml %>%
  group_by(date) %>%   # Group by date
  summarize(nb_assets = stock_id %>%   # Count nb assets
            as.factor() %>% nlevels()) %>%
  ggplot(aes(x = date, y = nb_assets)) + geom_col() +   # Plot
  coord_fixed(3)
```

![](img/8861a37f775d09b4ba7a5151f604d9f5_25_0.png)

FIGURE 1.1: Number of assets through time.

There are four immediate **labels** in the dataset: R1M_Usd, R3M_Usd, R6M_Usd and R12M_Usd, which correspond to the 1-month, 3-month, 6-month and 12-month future/forward returns of the stocks. The returns are **total returns**, that is, they incorporate potential **dividend** payments over the considered periods. This is a better proxy of financial gain compared to price returns only. We refer to the analysis of Hartzmark and Solomon (2019) for a study on the impact of decoupling price returns and dividends. These labels are located in the last 4 columns of the dataset. We provide their descriptive statistics below.

| Label | mean | sd | min | max |
|---|---|---|---|---|
| R12M_Usd | 0.137 | 0.738 | -0.991 | 96.0 |
| R1M_Usd | 0.0127 | 0.176 | -0.922 | 30.2 |
| R3M_Usd | 0.0369 | 0.328 | -0.929 | 39.4 |
| R6M_Usd | 0.0723 | 0.527 | -0.98 | 107. |

In anticipation for future models, we keep the name of the predictors in memory. In addition, we also keep a much shorter list of predictors.

```r
features <- colnames(data_ml[3:95]) # Keep the feature's column names (hard-coded, beware!)
features_short <- c("Div_Yld", "Eps", "Mkt_Cap_12M_Usd", "Mom_11M_Usd",
                    "Ocf", "Pb", "Vol1Y_Usd")
```

The predictors have been uniformized, that is, for any given feature and time point, the distribution is uniform. Given 1,207 stocks, the graph below cannot display a perfect rectangle.

```r
data_ml %>% filter(date == "2000-02-29") %>%
ggplot(aes(x = Div_Yld)) + geom_histogram(bins = 100) + coord_fixed(0.03)
```

![](img/8861a37f775d09b4ba7a5151f604d9f5_26_0.png)

**FIGURE 1.2:** Distribution of the dividend yield feature on date 2000-02-29.

The original labels (future returns) are numerical and will be used for regression exercises, that is, when the objective is to predict a scalar real number. Sometimes, the exercises can be different and the purpose may be to forecast **categories** (also called **classes**), like “buy”, “hold” or “sell”. In order to be able to perform this type of classification analysis, we create additional labels that are categorical.

```r
data_ml <- data_ml %>% group_by(date) %>% # Group by date
mutate(R1M_Usd_C = R1M_Usd > median(R1M_Usd), # Create the categorical labels
       R12M_Usd_C = R1M_Usd > median(R12M_Usd)) %>%
ungroup() %>%
mutate_if(is.logical, as.factor)
```

The new labels are binary: they are equal to 1 (true) if the original return is above that of the median return over the considered period and to 0 (false) if not. Hence, at each point in time, half of the sample has a label equal to zero and the other half to one: some stocks outperform and others underperform.

In machine learning, models are estimated on one portion of data (**training set**) and then tested on another portion of the data (**testing set**) to assess their quality. We split our sample accordingly.

```r
separation_date <- as.Date("2014-01-15")
training_sample <- filter(data_ml, date < separation_date)
testing_sample <- filter(data_ml, date >= separation_date)
```

We also keep in memory a few key variables, like the list of asset identifiers and a rectangular version of returns. For simplicity, in the computation of the latter, we shrink the investment universe to keep only the stocks for which we have the maximum number of points.

```r
stock_ids <- levels(as.factor(data_ml$stock_id)) # A list of all stock_ids
stock_days <- data_ml %>%
  group_by(stock_id) %>%
  summarize(nb = n())
stock_ids_short <- stock_ids[which(stock_days$nb == max(stock_days$nb))] # Stocks with full data
returns <- data_ml %>%
  filter(stock_id %in% stock_ids_short) %>%
  dplyr::select(date, stock_id, R1M_Usd) %>%
  spread(key = stock_id, value = R1M_Usd)
```

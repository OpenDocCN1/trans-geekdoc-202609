
### 3.2.4 Fama-MacBeth regressions

Another detection method was proposed by Fama and MacBeth (1973) through a two-stage regression analysis of risk premia. The first stage is a simple estimation of the relationship (3.1): the regressions are run on a stock-by-stock basis over the corresponding time series. The resulting estimates \(\hat{\beta}_{i,k}\) are then plugged into a second series of regressions:

\(r_{t,n} = \gamma_{t,0} + \sum_{k=1}^K \gamma_{t,k}\hat{\beta}_{n,k} + \varepsilon_{t,n},\) (3.4)

which are run date-by-date on the cross-section of assets.¹ Theoretically, the betas would be known and the regression would be run on the \(\beta_{n,k}\) instead of their estimated values. The \(\hat{\gamma}_{t,k}\) estimate the premia of factor \(k\) at time \(t\). Under suitable distributional assumptions on the \(\varepsilon_{t,n}\), statistical tests can be performed to determine whether these premia are significant or not. Typically, the statistic on the time-aggregated (average) premia \(\hat{\gamma}_k = \frac{1}{T} \sum_{t=1}^T \hat{\gamma}_{t,k}\) :

\(t_k = \frac{\hat{\gamma}_k}{\hat{\sigma}_k / \sqrt{T}}\)

is often used in pure Gaussian contexts to assess whether or not the factor is significant (\(\hat{\sigma}_k\) is the standard deviation of the \(\hat{\gamma}_{t,k}\) ).

We refer to Jagannathan and Wang (1998) and Petersen (2009) for technical discussions on the biases and losses in accuracy that can be induced by standard ordinary least squares (OLS) estimations. Moreover, as the \(\hat{\beta}_{i,k}\) in the second-pass regression are *estimates*, a second level of errors can arise (the so-called errors in variables). The interested reader will find some extensions and solutions in Shanken (1992), Ang et al. (2018) and Jegadeesh et al. (2019).

Below, we perform Fama and MacBeth (1973) regressions on our sample. We start by the first pass: individual estimation of betas. We build a dedicated function below and use some functional programming to automate the process.

```r
nb_factors <- 5
data_FM <- left_join(data_ml %>%
  dplyr::select(date, stock_id, R1M_Usd) %>%
  filter(stock_id %in% stock_ids_short),
  FF_factors,
  by = "date") %>%
mutate(R1M_Usd = lag(R1M_Usd)) %>%
na.omit() %>%
spread(key = stock_id, value = R1M_Usd)
models <- lapply(paste0("'", stock_ids_short,
         ~ MKT_RF + SMB + HML + RMW + CMA'),   # Model spec
```

¹Originally, Fama and MacBeth (1973) work with the market beta only: \(r_{t,n} = \alpha_n + \beta_{n,t_M} + \epsilon_{t,n}\) and the second pass included nonlinear terms: \(r_{t,n} = \gamma_{n,0} + \gamma_{t,1}\hat{\beta}_n + \gamma_{t,2}\hat{\beta}_n^2 + \gamma_{t,3}\hat{s}_n + \eta_{t,n}\), where the \(\hat{s}_n\) are risk estimates for the assets that are not related to the betas. It is then possible to perform asset pricing tests to infer some properties. For instance, test whether betas have a linear influence on returns or not (\(\mathbb{E}[\gamma_{t,2}] = 0\)), or test the validity of the CAPM (which implies \(\mathbb{E}[\gamma_{t,0}] = 0\)).

TABLE 3.2: Sample of beta values (row numbers are stock IDs).

| | Constant | MKT_RF | SMB | HML | RMW | CMA |
|---|---|---|---|---|---|---|
| 1 | 0.008 | 1.438 | 0.525 | 0.567 | 1.006 | -0.301 |
| 3 | -0.002 | 0.791 | 1.084 | 0.854 | 0.220 | -0.423 |
| 4 | 0.005 | 0.364 | 0.305 | -0.072 | 0.589 | 0.267 |
| 7 | 0.006 | 0.414 | 0.682 | 0.284 | 0.294 | 0.119 |
| 9 | 0.005 | 0.810 | 0.682 | 1.047 | 0.009 | 0.147 |
| 11 | 0.000 | 0.937 | 0.120 | 0.494 | -0.247 | 0.085 |

TABLE 3.3: Sample of reformatted beta values (ready for regression).

| | MKT_RF | SMB | HML | RMW | CMA | 2000-01-31 | 2000-02-29 | 2000-03-31 |
|---|---|---|---|---|---|---|---|---|
| 1 | 1.438 | 0.525 | 0.567 | 1.006 | -0.301 | -0.036 | 0.263 | 0.031 |
| 3 | 0.791 | 1.084 | 0.854 | 0.220 | -0.423 | 0.077 | -0.024 | 0.018 |
| 4 | 0.364 | 0.305 | -0.072 | 0.589 | 0.267 | -0.016 | 0.000 | 0.153 |
| 7 | 0.414 | 0.682 | 0.284 | 0.294 | 0.119 | -0.009 | 0.027 | 0.000 |
| 9 | 0.810 | 0.682 | 1.047 | 0.009 | 0.147 | 0.032 | 0.076 | -0.025 |
| 11 | 0.937 | 0.120 | 0.494 | -0.247 | 0.085 | 0.144 | 0.258 | 0.049 |

```r
function(f){ lm(as.formula(f), data = data_FM,
na.action="na.exclude") %>% # Call lm(.)
summary() %>% # Gather the output
"$"(coef) %>% # Keep only coefs
data.frame() %>% # Convert to dataframe
dplyr::select(Estimate)} # Keep the estimates
betas <- matrix(unlist(models), ncol = nb_factors + 1, byrow = T) %>% # Extract the betas
data.frame(row.names = stock_ids_short) # Format: row names
colnames(betas) <- c("Constant", "MKT_RF", "SMB", "HML", "RMW", "CMA") # Format: col names
```

In the table, MKT_RF is the market return minus the risk free rate. The corresponding coefficient is often referred to as the beta, especially in univariate regressions. We then reformat these betas from Table 3.2 to prepare the second pass. Each line corresponds to one asset: the first 5 columns are the estimated factor loadings and the remaining ones are the asset returns (date by date).

```r
loadings <- betas %>% # Start from loadings (betas)
dplyr::select(-Constant) %>% # Remove constant
data.frame() # Convert to dataframe
ret <- returns %>% # Start from returns
dplyr::select(-date) %>% # Keep the returns only
data.frame(row.names = returns$date) %>% # Set row names
t() # Transpose
FM_data <- cbind(loadings, ret) # Aggregate both
```

We observe that the values of the first column (market betas) revolve around one, which is what we would expect. Finally, we are ready for the second round of regressions.

```r
models <- lapply(paste("", returns$date, "", ' ~ MKT_RF + SMB + HML + RMW + CMA', sep = ""),
function(f){ lm(as.formula(f), data = FM_data) %>% # Call lm(.)
```

TABLE 3.4: Sample of gamma (premia) values.

| | Constant | MKT_RF | SMB | HML | RMW | CMA |
|---|---|---|---|---|---|---|
| 2000-01-31 | -0.031 | 0.037 | 0.227 | -0.157 | -0.276 | 0.044 |
| 2000-02-29 | 0.020 | 0.081 | -0.134 | 0.050 | 0.089 | -0.027 |
| 2000-03-31 | 0.007 | -0.011 | -0.016 | 0.054 | 0.036 | 0.039 |
| 2000-04-30 | 0.127 | -0.132 | -0.104 | 0.088 | 0.117 | -0.002 |
| 2000-05-31 | 0.042 | -0.005 | 0.075 | -0.113 | -0.080 | -0.045 |
| 2000-06-30 | 0.028 | -0.029 | -0.019 | 0.054 | 0.045 | 0.017 |

```r
summary() %>%
"$"(coef) %>%
data.frame() %>%
dplyr::select(Estimate)}
)
gammas <- matrix(unlist(models), ncol = nb_factors + 1, byrow = T) %>%
data.frame(row.names = returns$date)
colnames(gammas) <- c("Constant", "MKT_RF", "SMB", "HML", "RMW", "CMA")
```

Visually, the estimated premia are also very volatile. We plot their estimated values for the market, SMB and HML factors.

```r
gammas %>%
dplyr::select(MKT_RF, SMB, HML) %>%
bind_cols(date = data_FM$date) %>%
gather(key = factor, value = gamma, -date) %>%
ggplot(aes(x = date, y = gamma, color = factor)) +
geom_line() + facet_grid( factor~ . ) +
scale_color_manual(values=c("#F87E1F", "#0570EA", "#F81F40")) +
coord_fixed(980)
```

![](img/8861a37f775d09b4ba7a5151f604d9f5_44_0.png)

FIGURE 3.3: Time series plot of gammas (premia) in Fama-MacBeth regressions.

The two spikes at the end of the sample signal potential collinearity issues; two factors seem to compensate in an unclear aggregate effect. This underlines the usefulness of penalized estimates (see Chapter 5).

### 3.2.5 Factor competition

The core purpose of factors is to explain the cross-section of stock returns. For theoretical and practical reasons, it is preferable if redundancies within factors are avoided. Indeed, redundancies imply collinearity which is known to perturb estimates (Belsley et al. (2005)). In addition, when asset managers decompose the performance of their returns into factors, overlaps (high absolute correlations) between factors yield exposures that are less interpretable; positive and negative exposures compensate each other spuriously.

A simple protocol to sort out redundant factors is to run regressions of each factor against all others:

$$f_{t,k} = a_k + \sum_{j \neq k} \delta_{k,j} f_{t,j} + \epsilon_{t,k}.$$ (3.5)

The interesting metric is then the test statistic associated to the estimation of $a_k$. If $a_k$ is significantly different from zero, then the cross-section of (other) factors fails to explain exhaustively the average return of factor $k$. Otherwise, the return of the factor can be captured by exposures to the other factors and is thus redundant.

One mainstream application of this technique was performed in Fama and French (2015), in which the authors show that the HML factor is redundant when taking into account four other factors (Market, SMB, RMW and CMA). Below, we reproduce their analysis on an updated sample. We start our analysis directly with the database maintained by Kenneth French.

We can run the regressions that determine the redundancy of factors via the procedure defined in Equation (3.5).

```r
factors <- c("MKT_RF", "SMB", "HML", "RMW", "CMA")
models <- lapply(paste(factors, ' ~ MKT_RF + SMB + HML + RMW + CMA', factors),
function(f){ lm(as.formula(f), data = FF_factors) %>% # Call lm(.)
summary() %>% # Gather the output
"$"(coef) %>% # Keep only the coefs
data.frame() %>% # Convert to dataframe
filter(rownames(.) == "(Intercept)") %>% # Keep only the Intercept
dplyr::select(Estimate, `Pr(>|t|)`)} # Keep the coef & p-value

alphas <- matrix(unlist(models), ncol = 2, byrow = T) %>% # Switch from list to dataframe
data.frame(row.names = factors)
# alphas # To see the alphas (optional)
```

We obtain the vector of $\alpha$ values from Equation (3.5). Below, we format these figures along with $p$-value thresholds and export them in a summary table. The significance levels of coefficients is coded as follows: 0 < (***) < 0.001 < (**) < 0.01 < (*) < 0.05.

```r
results <- matrix(NA, nrow = length(factors), ncol = length(factors) + 1) # Coefs
signif <- matrix(NA, nrow = length(factors), ncol = length(factors) + 1) # p-values
for(j in 1:length(factors)){
form <- paste(factors[j],
' ~ MKT_RF + SMB + HML + RMW + CMA', factors[j]) # Build model
fit <- lm(form, data = FF_factors) %>% summary() # Estimate model
coef <- fit$coefficients[,1] # Keep coefficients
```

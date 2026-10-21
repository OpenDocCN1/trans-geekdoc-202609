
NIPO_{t-1}, NIPO_{t-2}, NIPO_{t-3} are the number of IPOs issued in time periods NIPO_{t-1}, NIPO_{t-2}, NIPO_{t-3}; β₀ is the standard slope coefficient associated with a regression analysis; ε is an error term.

Lowry and Schwert (2002) provided an interesting historical review of the relationship between IPO issuance and performance, which we will use as a benchmark comparison. In Table 67.3, the IR variable is the investor’s average initial return in a given month and the NIPO variable is the number of IPOs issued in a given month. In Lowry et al. (2002) they found that higher IPO returns lead to more IPO issuance; however, the number of IPOs issued in a particular month does not explain future performance. Smith et al. (2018) extend this analysis forward from April 1996 to January 2008 and found a similar pattern of behavior.

```
IR_t = β₀ + β₁ IR_{t-1} + β₂ IR_{t-2} + β₃ IR_{t-3} + β₄ NIPO_{t-1} + β₅ NIPO_{t-2}
    + β₆ NIPO_{t-3} + β₇ D_{Heat} + β₈ D_{Cold} + ε, (67.4)
```

where the β₇ D_{Heat} and β₈ D_{Cold} variables are incorporated into equation 67.4 as defined in equations 67.1 and 67.2. The new hot and cold variables are based on the quartile sorting procedure explained by Smith et al. (2018) and in equation 67.1 and using the average volume over the 10-month period preceding time t. Whereas the old hot and cold variables are based on the three-month average volume and reviewing the entire sample to identify hot (i.e., quartile 1) and cold (i.e., quartile 4) issuance month.

A comparison of the results from Lowry et al. (2002), after integrating the definition of hot and cold equity markets defined in Helwege et al. (2004), to the model of estimation of hot and cold equity markets presented in Smith et al. (2018) provides us with a new perspective about how we might be able to think about and measure hot and cold IPO markets, in terms of performance. In Table 67.4, specifically looking at Models I and II, the Helwege et al. (2004) and the Smith et al. (2018) models of hotness and coldness in terms of IPO performance are compared and both models seem to have a similar fit and both metrics produce statistically significant coefficients associated with hot and cold markets. In Models III, IV, and V in the table presented above, Smith et al. (2018) compare the performance of their method of hot and cold performance with the Helwege et al. (2004) model and it allows us to place this comparison within the context of the results

## Table 67.3: Comparison of the composition of IPOs issuing shares over time.

| Variable | ISR 1960-97 IR Coef | ISR 1960-97 IR t-stat | ISR 1960-97 NIPO Coef | ISR 1960-97 NIPO t-stat | ISR 1985-97 IR Coef | ISR 1985-97 IR t-stat | ISR 1985-97 NIPO Coef | ISR 1985-97 NIPO t-stat | SDC 1985-97 IR Coef | SDC 1985-97 IR t-stat | SDC 1985-97 NIPO Coef | SDC 1985-97 NIPO t-stat |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Regressors |  |  |  |  |  |  |  |  |  |  |  |  | |
| Constant | 7.426 | 5.18 | 0.321 | 0.41 | 11.643 | 4.03 | -6.810 | -1.86 | 5.029 | 4.54 | 0.069 | 0.03 |
| IR_t-1 | 0.510 | 5.66 | 0.094 | 2.85 | 0.286 | 3.33 | 0.565 | 3.52 | 0.359 | 4.08 | 0.418 | 2.60 |
| IR_t-2 | 0.136 | 1.91 | 0.025 | 0.81 | 0.039 | 0.47 | 0.046 | 0.26 | 0.152 | 1.73 | 0.120 | 0.63 |
| IR_t-3 | 0.014 | 0.24 | 0.037 | 1.24 | -0.048 | -0.58 | 0.337 | 2.07 | 0.002 | 0.02 | 0.224 | 1.23 |
| NIPO_t-1 | -0.023 | -0.61 | 0.596 | 9.31 | -0.016 | -0.62 | 0.528 | 6.00 | 0.001 | 0.03 | 0.485 | 6.16 |
| NIPO_t-2 | -0.027 | -0.71 | 0.111 | 1.57 | -0.019 | -0.63 | 0.036 | 0.37 | 0.015 | 0.44 | 0.063 | 0.71 |
| NIPO_t-3 | -0.012 | -0.33 | 0.204 | 3.69 | -0.003 | -0.09 | 0.292 | 3.75 | -0.012 | -0.39 | 0.203 | 2.66 |
| R^2 | 0.373 |  | 0.760 |  | 0.072 |  | 0.622 |  | 0.173 |  | 0.580 |  |
| S(u) | 14.643 |  | 12.261 |  | 6.886 |  | 14.826 |  | 5.987 |  | 12.712 |  |
| Granger F-tests: |  |  |  |  |  |  |  |  |  |  |  |  | |
| Lagged NIPO (p-value) | 1.87 (0.132) |  |  |  | 0.70 (0.551) |  |  |  | 0.09 (0.964) |  |  |  |
| Lagged IR (p-value) |  |  | 7.22 (0.0001) |  |  |  | 7.07 (0.0001) |  |  |  | 4.90 (0.002) |  |
| Sample Size, T | 428 |  | 430 |  | 156 |  | 156 |  | 156 |  | 156 |  |

Source: Lowry and Schwert (2002).

## Table 67.4: Monthly returns — April 1996 to January 2008.

|  | Model I | Model II | Model III | Model IV | Model V |
|---|---|---|---|---|---|
| Intercept | 0.0737*** | 0.0724*** | 0.0154 | 0.0299 | -0.0037 |
| Hot_Old | 0.1246*** |  |  | 0.0699*** |  |
| Cold_Old | -0.0639*** |  |  | -0.0374 |  |
| Hot_New |  | 0.1211*** |  |  | 0.1000*** |
| Cold_New |  | -0.0893*** |  |  | -0.0564** |
| NIPO_t-1 |  |  | -0.0004 | -0.0006 | -0.0006 |
| NIPO_t-2 |  |  | -0.0012 | -0.0017 | -0.0006 |
| NIPO_t-3 |  |  | 0.0032** | 0.0034*** | 0.0033*** |
| IR_t-1 |  |  | 0.7784*** | 0.6464*** | 0.6793*** |
| IR_t-2 |  |  | -0.3987*** | -0.3859*** | -0.3151*** |
| IR_t-3 |  |  | 0.2402*** | 0.1754** | 0.1506* |
| n | 140 | 132 | 132 | 132 | 132 |
| r²_adj | 0.2503 | 0.2524 | 0.4359 | 0.4835 | 0.5832 |

Notes: This table reports the results of estimation of IRs for the April 1996 to 2008 time-period. This table presents the estimation results associated with our comparison sample. Models I and VI use the Helwege and Liang (2004) methodology to identify hot and cold markets and Models II and IV use the method developed in this paper. The lagged volume of IPOs and IRs are used as control variables in Models III through V to determine whether the hot and cold variables are stable and whether the dummy and spline variables have predictive power over IPO returns. *, **, and *** are significant at 0.10, 0.05, and 0.01.

Source: Smith and Mumtaz (2018).

that were presented in Lowry et al. (2002). Although the Helwege et al. (2004) model of hot and cold markets improves the model's predictive power over the Lowry et al. (2002) model, the statistical significance associated with the cold market coefficient fades to insignificance when the variables are incorporated in the Lowry et al. (2004) model. As a comparison, the model of hot and cold IPO performance presented in Smith et al. (2018) improved the predictive power of the model provided in Lowry et al. (2004) and the coefficients associated with hot and cold markets remain statistically significant.

```
IR_t = β0 + β1 IR_{t-1} + β2 IR_{t-2} + β3 IR_{t-3} + β4 NIPO_{t-1}
    + β5 NIPO_{t-2} + β6 NIPO_{t-3} + β7 D_{Heat} + β8 D_{Cold}
    + β9 D_{2008} + β10 D_{JOBS} + β11 D_{Change} + ε, (67.5)
```

where the dummy variables associated with D_{2008}, D_{JOBS}, and D_{Change} are activated at their event dates (i.e., the binary variable reads ‘1’) and

deactivated after their event dates (i.e., the binary variable reads ‘0’). The D2008 variable was coded as a ‘1’ from January 2008 to March 2009, the DJOBs variable was coded as a ‘1’ after April 2012, and the DChange variable was coded ‘1’ from April 2014 to December 2015.

Interestingly, as we move forward to evaluate the IPO performance during the January 2005 to December 2015 time period, presented in Table 67.5, based on statistical analysis conducted in Smith et al. (2018), we see that the hot and cold variable created in Smith et al. (2018) seems to improve the predictive power over IPO performance as compared against the Lowry et al. (2004) model, as indicated in Models VI and VII. As illustrated in Table 67.5, the variables used in Lowry et al. (2002) do not seem to describe the performance of IPOs during this time. It seems evident that Model XI, which incorporates the Smith et al. (2018) technique of hotness and coldness, exceeds the performance of Model X significantly, which includes the Lowry (2004) et al. model of hot and cold markets. Finally, the market events that Smith et al. (2018) incorporated into their model do not significantly improve the final model’s predictive power; however, the dummy variable associated with the 2007 to 2008 financial collapse had a significant influence over IPO performance.

## 67.6 Estimating IPO Volume

Developing an understanding of the relationship between performance and the volume of IPOs issued in a given period are of interest to both academics and practitioners. Moreover, researchers such as Ibbotson (1975), Ibbotson et al. (1975), Ritter (1984), Ibbotson et al. (1994), Loughran et al. (1994), Lowry et al. (2002), Lowry (2003), Helwege et al. (2004), Alti (2005), Benninga et al. (2005), Pastor et al. (2005), Yung et al. (2008), Gao et al. (2013), and Hu et al. (2013) have explored this relationship and in this section we will provide a critical review of the current state of the literature and illustrate how integrating general market events into our models used to estimate issuance could provide practitioners and researchers alike with a better understanding of IPO issuance.

```
NIPO_t = β₀ + β₁IR_t + β₂IR_{t-1} + β₃IR_{t-2} + β₄IR_{t-3}
       + β₅NIPO_{t-1} + β₆NIPO_{t-2} + β₇NIPO_{t-3}
       + β₈D_{Heat} + β₉D_{Cold} + ε.   (67.6)
```

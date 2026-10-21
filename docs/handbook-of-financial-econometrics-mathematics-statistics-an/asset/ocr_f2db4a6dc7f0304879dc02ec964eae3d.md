# Table 112.3: (Continued)

| Company | Mean | Maximum | Minimum | Standard dev | Variance | Median |
|---|---|---|---|---|---|---|
| MSFT | 7.85 | 14.20 | 0.43 | 3.96 | 0.16 | 8.42 |
| MU | 10.79 | 19.58 | 1.91 | 3.94 | 0.16 | 11.15 |
| MYL | 5.86 | 12.28 | 0.10 | 3.69 | 0.14 | 6.28 |
| NOK | 4.26 | 13.32 | 0.00 | 2.74 | 0.08 | 3.89 |
| NTT | 1.60 | 5.13 | 0.09 | 1.01 | 0.01 | 1.45 |
| PCAR | 8.27 | 14.34 | 0.01 | 4.48 | 0.20 | 8.49 |
| PG | 4.49 | 7.06 | 0.11 | 1.69 | 0.03 | 4.64 |
| RF | 17.94 | 43.78 | 0.41 | 12.01 | 1.44 | 17.97 |
| RIG | 6.16 | 13.05 | 0.06 | 3.56 | 0.13 | 0.42 |
| SCHW | 9.12 | 18.50 | 0.40 | 5.37 | 0.29 | 7.63 |
| SLB | 15.04 | 24.66 | 0.06 | 8.16 | 0.67 | 14.44 |
| SPG | 3.33 | 10.07 | 0.13 | 2.26 | 0.05 | 3.05 |
| SYMC | 9.73 | 15.39 | 0.42 | 3.88 | 0.15 | 10.86 |
| T | 1.35 | 3.54 | 0.01 | 0.82 | 0.01 | 1.26 |
| USB | 9.23 | 17.52 | 0.25 | 5.06 | 0.26 | 9.23 |
| VCO | 1.27 | 3.30 | 0.01 | 0.79 | 0.01 | 1.27 |
| VMC | 8.73 | 20.36 | 2.43 | 5.38 | 0.29 | 5.93 |
| WHR | 6.18 | 11.54 | 0.63 | 2.90 | 0.08 | 6.43 |
| XOM | 8.13 | 13.18 | 0.06 | 3.99 | 0.16 | 9.27 |
| YHOO | 10.76 | 14.69 | 0.21 | 3.28 | 0.11 | 11.46 |

standard deviation of MAPE greater than 10% and 39 have standard deviation less than 5%. The results are marginally better than those from the B–J models. Since it is more difficult to identify the precise autoregressive and moving average orders in B–J modeling, the simple H/W models could be the preferred choice. Although ForecastX can help researchers identify some optimum model specifications, there is no guarantee that they are truly the best specifications. However, based on the excellent fits to the both within and out of sample data, ForecastX has shown its accuracy and easiness to use, and so both H/W and B–J methods can be practically applied. From time-series decomposition the similar statistics are shown in Table 112.4.

We are surprised to discover that TSD beyond sample results are much worse than those from B–J and H/W models while the within sample fits are slightly better. From TSD only 9 stocks have mean MAPE under 5% and another 13 between 5% and 10% and 4 have mean MAPE over 40% (NOK 40.71%, KYO 41.40%, MU 41.69%, and RF 52.35%). From B–J models the highest mean MAPE is 19.22% for HIBB, a sporting goods company, and from H/W models HIBB also has the highest MAPE at 19.01%. For practical applications the beyond sample predictability is more relevant and therefore one may opt for H/W or B–J.
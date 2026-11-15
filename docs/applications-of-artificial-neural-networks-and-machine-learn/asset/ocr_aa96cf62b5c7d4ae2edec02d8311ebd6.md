# Table 8.7 Effect of the number of Kohonen units on the net response

| D | N | N_win | Error% |
|---|---|---|---|
| 4 | 990 | 9 | 5.5 |
| 4.1 | 984 | 12 | 6.42 |
| 4.2 | 975 | 9 | 6.32 |
| 4.3 | 963 | 10 | 7.63 |
| 4.4 | 946 | 10 | 7.63 |
| 4.5 | 928 | 8 | 7.63 |
| 4.6 | 886 | 7 | 7.59 |
| 4.7 | 833 | 7 | 8.16 |
| 4.8 | 777 | 7 | 9.73 |
| 4.9 | 711 | 7 | 8.35 |
| 5 | 661 | 8 | 7.51 |
| 5.1 | 588 | 8 | 7.55 |
| 5.2 | 523 | 8 | 8.16 |
| 5.3 | 461 | 6 | 12.9 |
| 5.4 | 405 | 6 | 10.3 |
| 5.5 | 348 | 4 | 10.61 |
| 5.6 | 298 | 6 | 8.13 |
| 5.7 | 252 | 4 | 13.47 |
| 5.8 | 215 | 4 | 11.42 |
| 5.9 | 194 | 3 | 9.58 |
| 6 | 154 | 5 | 11.38 |

this amount is not significant. The values given in Tables 8.6 and 8.8 indicate that the average error on the output units of CPN is about 5% as compared to 2% for the BPN. However, the training time of the CPN is much less than that of the BPN. When large-scale problems are involved, that is, the number of input and output units is high, and the training time becomes significant. The CPN can be used in structural optimization since the process is numerical, and implementing the net with a few percent error in structural response does not affect the result considerably [6].

# 8.5 Concluding Remarks

The improved CPN in general, performs faster than the Backpropagation net. When neuro-optimization of large-scale problems is involved, The CPN can be trained in a reasonable CPU time. The accuracy of the results can be increased by decreasing the Kohonen unit classifier, D. Application of this approach to problems in structural
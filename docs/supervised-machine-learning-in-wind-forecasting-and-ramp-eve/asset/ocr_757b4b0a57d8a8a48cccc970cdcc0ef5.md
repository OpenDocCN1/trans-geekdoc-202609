# Table 7.4 Performance metrics of ramp prediction models (Onshore sites).

| Dataset | Model | RMSE U2 | NMSE Rup | R2 Rdown | U1 CPU time |
|---|---|---|---|---|---|
| a | LSSVR | 0.3602 | 0.0177 | 0.9856 | 0.0024 |
| | | 0.5678 | 0.0236 | NA | 1.46082 |
| | TSVR | 0.3525 | 0.0177 | 0.9899 | 0.0001 |
| | | 0.0519 | 0.0016 | NA | 57.41689 |
| | ε-TSVR | 0.3475 | 0.0178 | 0.9701 | 0.0046 |
| | | 0.6538 | 0.0036 | NA | 7.3946 |
| | RFR | 0.3436 | 0.1251 | 0.9506 | 0.5633 |
| | | 0.6276 | 0.0789 | NA | 4.2693 |
| | GBM | 0.1197 | 0.0044 | 0.9705 | 0.0115 |
| | | 0.1539 | 0.0043 | NA | 0.7119 |
| | Persistence | 0.4399 | 0.0221 | 1.0145 | 0.0259 |
| | | 0.6296 | 0.2800 | NA | 0.02545 |
| | ε-SVR | 0.3620 | 0.0178 | 1.0004 | 0.0029 |
| | | 6.6035 | 0.0862 | NA | 238.8274 |
| b | LSSVR | 0.0403 | 0.00057 | 0.9748 | 0.0044 |
| | | 0.5716 | 0.1169 | 0.1498 | 0.76059 |
| | TSVR | 0.0268 | 0.0002 | 0.9832 | 0.0029 |
| | | 0.444 | 0.0881 | 0.1228 | 23.9192 |
| | ε-TSVR | 0.0486 | 0.0008 | 0.9758 | 0.0053 |
| | | 0.6978 | 0.1098 | 0.1332 | 3.3806 |
| | RFR | 0.06991 | 0.00121 | 0.9730 | 0.0660 |
| | | 0.7191 | 0.1112 | 0.1421 | 32.11 |
| | GBM | 0.0651 | 0.0017 | 0.9986 | 0.0078 |
| | | 0.0219 | 0.0235 | 0.0307 | 45.93 |
| | Persistence | 0.4399 | 0.0108 | 1.0068 | 0.0190 |
| | | 0.6429 | 0.2350 | 0.2000 | 0.04356 |
| | ε-SVR | 0.0593 | 0.0013 | 0.9556 | 0.0065 |
| | | 0.6517 | 0.1876 | 0.2367 | 84.4812 |

model gives an R2 value greater than 1, which suggests overfitting when performed on an unseen data. The problem of overfitting as discussed in Chapter 5 can be eliminated by using a boosting algorithm like XBoost. Also it is worth noting that the error in predicting ramp-down event is greater than that in predicting ramp-up event. This observation remains true for most of the datasets.

Consider dataset Aa. The RMSE value is minimum for ε-TSVR followed by TSVR and LSSVR. The decision tree ensemble methods give a
# Linear Regression

# 253

```
signLevels:convertPDict each binr[(1.282;1.645;2.326;3.091);abs
  tStats];
// log-likelihood
log:neg[log[2*acos(-1*count[y]%2]+neg[log[sqrt(RScount[y]]]*
  count[y]];
  AIC from log-likelihood
  aic:(2*count[beta]-2.ol];
  AIC with sample correction - depends upon heavy assumptions
  aic:aic(f"$2*(k+k)*(f"$count[y]-l-k:count[beta]);
// output bucket
bucket:bucket('beta' varcov'observations'df'tStats'TSS'RSquared'
  adjRSquared'signLevels'log'aic'acc);
  (beta;varcov:count[y];count[beta];tStats;TSS;RSS;RSquared;
  adjRSquared;signLevels;log;aic;acc));
bucket:
```

Let us run the example:

```
quant.Q_ols.fit[tabData['x1'x2'x3'const]]
```

with results in a comprised form that:

```
('beta' varcov'observations'df'tStats'TSS'RSquared'adjRSquared
  signLevels'log'aic'acc')(0.9998791 -0.997415 1.996675
  1.10413:0.00320863 0.0318716 0.0030975 0.0826293;1.022845e-05
  3.473233-07 -3.667938e-07 -9.23826e-06 3.473233-07 9.851538e-06
  3.973202-07 1.015557-06 -3.667938-07 -3.972302-07 5.960856e-06
  -1.941069e-05;-9.23826e-06 1.015557-06 -1.941069e-05 6.827689e-05)
  [1000;4];3986;495;1049.4 20683.69
  3.521562;6084;9.577583;0.998363;0.9983947;****(99.9 c.l.)
  ****(99.9 c.l.)";****(99.9 c.l.)";****(99.9 c.l.)
  8995121;-1783.824;-1783.484)
```

The output contains all the information in a comprised and easy-to-retrieve way, but still beyond reach of human user. For that purpose, we summarise the results in a more convenient and standardised form:

```
quant.Q_ols.fit[tab]
// tab - table with data
// names
yname:first cols tab
xnames:1_cols tab
// running regressions
reg.:quant.Q_ols.fit[tabname];tab[xNames]
// regression of part
tabReg:[] name:xNames;coeff:reg[beta];error:reg[errors];tStat:reg[
tStats];
  significance:reg[signLevels]);
// stats per part
tabStats:[] name:STATISTICSnObservations'TSS'RSquared
  RSquaredAdjusted'AIC LogLikelihoodAIC AICC;coeff:(0;f"$count[y];y
  "$reg"dfn;
```
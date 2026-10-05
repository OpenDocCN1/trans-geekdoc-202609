# 396

# MACHINE LEARNING

In conclusion, the ridge regression is a friendly and easy to implement method to deal with bias-variance trade-off. The method imposes a penalty in terms of shrinking the regression coefficients. The ridge regression shrinks the entire vector of parameters at the same time, trying to balance the proper mixture of re-weighted parameters. Ridge regression is not functional when our objective is to select a subset of regressors.

# 20.4 IMPLEMENTATION OF THE RIDGE REGRESSION

We implement the ridge regression suite of functions within the namespace quantQ, reg. We first start with the data set we will employ. Upon the data set created in Chapter 13, we will add another feature, `x4`, which is identical to feature `x3`. The data set contains perfectly collinear data, where features are linearly dependent. Let us denote the data name tabData2 and define it as follows:

```
tabData2:([ y:y; x1:x1; x2:x2; x3:x3; x4:x3;);
```

We have to add a constant term as well:

```
tabData2: update:const.1 from tabData2;
tab2
```

| y | x1 | x2 | x3 | x4 | const |
|---|---|---|---|---|--|
| 11.82699 | 2.454263 | -3.583155 | 1.456235 | 2.456235 | 1 |
| 8.805473 | 3.91833 | -0.758861 | 1.390334 | 1.390334 | 1 |
| 5.11374 | 0.595565 | 0.1658444 | 2.04283 | 2.04283 | 1 |
| 4.694372 | -1.856926 | -2.036408 | 3.506369 | 3.506369 | 1 |
| 9.29502 | -0.670472 | -1.952683 | 3.506369 | 3.506369 | 1 |
| 6.65504 | 0.317425 | -2.000512 | 1.560693 | 1.560693 | 1 |
| 7.12083 | 0.0147587 | -1.554944 | 2.233064 | 2.233064 | 1 |
| 8.331946 | 2.104604 | -1.420832 | 1.810523 | 1.810523 | 1 |
| 8.30803 | 1.870071 | -1.473924 | 1.935104 | 1.935104 | 1 |
| 13.5147 | 2.348974 | -2.671633 | 3.728308 | 3.728308 | 1 |

The consequence of linear dependence among features is that the rank of the xtx matrix is not the number of features and this matrix cannot be inverted. The OLS fails in such a case, and the algorithm for the OLS coefficient cannot be used. Let us illustrate it as follows:

```
ytx: enlist tabData2[`const`] mmu flip[tabData2[`const` `x1` `x2` `x3` `x4`]];
xtx: x mmu flip[tabData2[`const` `x1` `x2` `x4`]];
```

and we can solve it:

```
solution: ytx lsq xtx;
beta:first solution;
beta
```

On On On On Onf
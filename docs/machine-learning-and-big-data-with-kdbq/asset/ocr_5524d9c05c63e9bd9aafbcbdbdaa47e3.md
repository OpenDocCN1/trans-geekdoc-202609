# Linear Regression with Regularisation

Viewing the 10 rows of the table pathLAR2:

-1@pathLAR2

| arcLength beta0 | beta1 | beta2 | beta3 | beta4 |
| 2.1305 | 1.49716 | 1.11546 | -0.947515 | 0.0675325 | 0 |
| 2.1306 | 1.49716 | 1.11546 | -0.947561 | 0.0675524 | 0 |
| 2.1307 | 1.49716 | 1.11517 | -0.947607 | 0.0675726 | 0 |
| 2.1308 | 1.49716 | 1.11548 | -0.947664 | 0.0675921 | 0 |
| 2.1309 | 1.49716 | 1.11579 | -0.947710 | 0.0676117 | 0 |
| 2.1310 | 1.49716 | 1.11569 | -0.947759 | 0.0676312 | 0 |
| 2.1311 | 1.49716 | 1.11564 | -0.947803 | 0.0676508 | 0 |
| 2.1312 | 1.49716 | 1.11571 | -0.947859 | 0.0676703 | 0 |
| 2.1313 | 1.49716 | 1.11501 | -0.947906 | 0.0676999 | 0 |
| 2.1314 | 1.49716 | 1.11532 | -0.947952 | 0.0677094 | 0 |

We have obtained the same result. There is a 0 coefficient on the constant term, which means the function operating on the demeaned time series does not assign any value to the constant feature. This can ignore irrelevant features. This shows that though the constant feature is not in fact demanded, the algorithm performs well.

Following the previous sections, we develop a function which tests the validity of regularisation on the out-of-sample data. The function performs the same regularisation as the LAR function using the in-sample data while the validity of the given regularisation is assessed using the RMSE on the out-of-sample part of the data. The outcome of the function is a table with a regularisation path, where each point of the path is assigned the RMSE value.

```
quant0_reg_LAR(tab;step;inOutFlag)
// tab table with data, (y,x)
// step step of the LAR algorithm
// inOutFlag = atom/array to form in sample, i=out
// dependent variable - first column of tab
y: tab first cols of tab
// independent variables - remaining columns
x:(tab_1_cols) cols;
whereMissing:=raze(where y!=0; raze(where x!=0) each x);
// remove the missing values
y:y([tile count y) except whereMissing];
S:[:where whereMissing] S([tile count x) except whereMissing])
whereMissing:= each x;
// inOutFlag is atom, in sample is randomly chosen inOutFraction of sample
if(1<count(inOutFlag));
// split sample: OUT
xOUT:flip ceiling([inOutFlag+count y] flip x;
yOUT:ceiling([inOutFlag+count y] - y;
// split sample: IN
xS:flip ceiling([inOutFlag+count y])flip xS;
y:ceiling([inOutFlag+count y])wy
// inOutFlag is Boolean array with 1 being in/0 out
if([1<count[inOutFlag]]):
inOutFlag:inOutFlag([tile count inOutFlag]) except whereMissing);
```
ing all and dividing them by the total parameters count (in this example is “n”) will yield the mean value of the considered parameter. It is referred as “ASK Point” (ASKP) i.e. $\mu_c$.

```
$ASKP = \mu_c = \frac{\int C_1+\int C_2+\int C_3+\int C_i...+\int C_n}{n}$
```

```
$ASKP = \mu_c = Parameters^1 Mean$
```

```
$n = number of parameters$
```

```
$i = importance of parameter$
```

In summarized form; formula can be re-written as:

```
$ASKP = \mu_c = \sum_{1}^{n} \frac{\int C_n}{n}$
```

# ASK Confidence Level

Calculate the standard deviation using the same data. Standard deviation is referred as **ASK Confidence Level (ACL)**. ACL is calculated by adding the square of the value after subtracting ASKP for each parameter value, summed value when divided by the total number of parameters gives standard deviation $\sigma_c$ i.e. ACL.

```
$ACL = \sigma_c = \frac{\left(\int C_1 - \mu_c\right)^2 + \left(\int C_2 - \mu_c\right)^2 + \left(\int C_3 - \mu_c\right)^2 + ... \left(\int C_n - \mu_c\right)^2}{n}$
```

```
$ACL = \sigma_c = Parameters^1 Standard Deviation$
```

```
$ASKP = \mu_c = Parameters^1 Mean$
```

```
$n = number of parameters$
```

In summarized form formula can be re-written as:
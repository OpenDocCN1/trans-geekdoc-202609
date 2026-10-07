# Research Design and Statistical Analysis

than the $n$ are used in these weights because this yields an unbiased estimate of $\sigma_{	ilde{Y}_1-	ilde{Y}_2}^2$. The pooled-variance estimate can also be written as

```
$s_{pooled}^2 = \frac{SS_1 + SS_2}{n_1 + n_2 - 2} \quad (6.5)$
```

when the $SS$ for a group is a sum of squared deviations of the scores about the mean of the group; that is,

```
$SS_i = \sum (Y_{ij} - 	ilde{Y}_i)^2 \quad (6.6)$
```

This quantity is usually referred to as the *sum of squares*, and it will play an important role in the remaining chapters.
We now state the expression for the estimate of the $SE$ of the sampling distribution of the difference between two independent means:

```
$s_{	ilde{Y}_1-	ilde{Y}_2} = s_{pooled} \sqrt{\frac{1}{n_1} + \frac{1}{n_2}} \quad (6.7)$
```

When $n_1 = n_2 = n$, as is frequently the case in experimental research, Equation 6.7 leads us to

```
$s_{pooled} = \sqrt{s_1^2 + s_2^2} / 2 \quad (6.8)$
```

and Equation 6.8 becomes

```
$s_{	ilde{Y}_1-	ilde{Y}_2} = s_{pooled} \sqrt{2/n} \quad (6.9)$
```

For the TC data, from Equation 6.8,

```
$s_{pooled} = \sqrt{(2246.51 + 1581.75) / 2} = 43.75$
```

and from Equation 6.9,

```
$s_{	ilde{Y}_1-	ilde{Y}_2} = 43.75\sqrt{2/36} = 10.31$
```

With this estimate of the standard error, we can now proceed to draw inferences about the difference between the means of the control and diet populations.

# 4.4.2 Confidence Intervals for the Independent-Groups Design

The general form of the confidence interval, with confidence level $1-\alpha$, is

```
$P[V - (t_{df,\alpha/2V}V) \leq E(V) \leq V + (t_{df,\alpha/2V}V)] = 1-\alpha \quad (6.10)$
```
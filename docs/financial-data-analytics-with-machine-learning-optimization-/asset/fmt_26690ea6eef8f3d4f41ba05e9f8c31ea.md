
Note that the fitted values in the output have `r` columns, and the probability (final output) of the `i`‐th observation, of a sample of size `n`, belonging to the `j`‐th group is

`o′ij = exp(oij) / Σ(k=1 to r) exp(oik), i = 1, 2, ..., n, j = 1, 2, ..., r.`

Instead of looking for the least squares estimates for the weights and biases as in the linear output case in [Section 15.3](#c15.xhtml#c15-sec-0004), we here aim to minimize the so‐called `categorical cross‐entropy loss function`:

`E := -1/n Σ(i=1 to n) Σ(j=1 to r) 1{yi = cj} ln o′ij.`

Normally speaking, we predict that the `i`‐th observation belongs to group `j` if `o′ij` is maximum in the `i`‐th row of (`o′i1`, `o′i2`, ..., `o′ir`). It is clear that `o′ij` is the maximum if and only if `oij` is the maximum. For `R` in particular, we assign the label to the `pred` column according to the maximum `o′ij` among all `j = 1, ..., r` in each row of `iris.nn$fit`, and notably, the resulting model yields no error out of 150 cases and the error rate is 0%!

Since in the Iris flower example, the output has three levels, the diagram for this ANN with logistic output is shown in [Figure 15.7](#c15.xhtml#c15-fig-0007):

![FIGURE 15.7 Illustration of a 4‐2‐3 ANN.](images/c15f007.png)

[**FIGURE 15.7**](#c15.xhtml#R_c15-fig-0007) Illustration of a 4‐2‐3 ANN.

Note that for logistic output, the output of the `i`‐th record is

`o′ij = e^oij / (1 + e^oij) = P(yi = cj), j = 1, 2, ..., r.`

We next illustrate with the HSI example. For this example, the output variable is binary (`r = 2`). The fitted value in the output can only have one column, say the probability of belonging to Group 1, then the probability of belonging to Group 2 is the one minus the former.

We assign the label to the `pred` column according to the probability given in `fin.nn$fit`. Note that there are only 2 error cases out of a total of 680 cases and the error rate is only `0.29%`!

## 15.5 ADAPTIVE LEARNING RATE

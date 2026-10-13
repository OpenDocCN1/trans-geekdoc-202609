
## 6.5. Numerical Example and Code Comparison of Gradient Boosting for Classification

Next, as per the Input step of the gradient boosting algorithm, we must check whether the loss function is differentiable with respect to `F(xi)`:

```
∂L(yi, F(xi)) / ∂F(xi) = -yi + (1 / (1 + e^F(xi))) * e^F(xi)
                        = -yi + e^F(xi) / (1 + e^F(xi))
                        = -yi + e^log(odds_i) / (1 + e^log(odds_i))
                        = -yi + Pi
```

Always bear in mind that `P = e^log(odds) / (1 + e^log(odds))` when reading this section of gradient boosting classification.

As can be seen from the first-order differentiation of `L(yi, F(xi))` with respect to `F(xi)`, it finally leads to a very concise expression (i.e., `-yi + Pi`), where `Pi` is the predicted probability (∈ [0, 1]) for the ith sample, and `yi` is the true output (0 or 1) for the ith sample.

Suppose we have a small training dataset presented in **Table 6.4** with only 3 samples (i.e., n=3), which has one feature, the total number of bedrooms in the house (abbreviated as `num_bedrooms`), as well as one output about whether it is easy to sell the house (abbreviated as `is_easy_sell`) in the property market. The output is dichotomous with only two possible outputs (i.e., 0 and 1), where 0 means No (not easy to sell) and 1 means Yes (easy to sell). In other words, for this example, `X` is `num_bedrooms`, and `Y` is `is_easy_sell`. Our task is to build a gradient boosting classification model that maps the `X` and `Y`.

**Table 6.4 The small dataset for gradient boosting classification.**

| ![](Images/9789815136982-C6-T4.jpg) |

Using this small training dataset, we will break down the pseudocode into bite-sized chunks and execute it step by step.

![](Images/9789815136982-C6-P17.jpg)

To find the minimum using the first-order derivative:

```
d(∑(i=1 to n) L(yi, ã)) / dã = 0

∴ -y1 + e^ã/(1+e^ã) - y2 + e^ã/(1+e^ã) - y3 + e^ã/(1+e^ã) = 0

3 * e^ã/(1+e^ã) = y1 + y2 + y3

e^ã/(1+e^ã) = (y1+y2+y3)/3 = (1+0+1)/3 = 2/3

3e^ã = 2(1+e^ã)

e^ã = 2

ã = log(2) = 0.693
```

Bear in mind that `F0(x)` is the `ã` value that minimizes the total loss, so initially `F0(x) = ã = 0.693`.

```
∵ F(x) = log(odds)
∴ F0(x) = initial log(odds) = 0.693, which is a constant value for all samples initially.
```

Hence,

```
F0(x1) = initial log(odds1) = 0.693
F0(x2) = initial log(odds2) = 0.693
F0(x3) = initial log(odds3) = 0.693
```

Find the predicted probability `Pi` based on the computed initial `log(odds_i)`:

```
∵ Pi = e^log(odds_i) / (1 + e^log(odds_i))

∴ P1 = e^0.693 / (1 + e^0.693) = 0.667
P2 = e^0.693 / (1 + e^0.693) = 0.667
P3 = e^0.693 / (1 + e^0.693) = 0.667
```

Append the `F0(x) = initial log(odds)` and `Pi` to the table:

![](Images/9789815136982-C6-P18.jpg)

Here, `m` is the index of decision tree; `rim` is the residual of the ith sample in the mth decision tree.

```
∵ ∂L(yi, F(xi)) / ∂F(xi) = -yi + Pi
∴ -∂L(yi, F(xi)) / ∂F(xi) = yi - Pi
```

When `m=1` (i.e., the first decision tree):

```
ri1 = yi - Pi
```

Here, the `Pi` must be corresponding to `F0(xi)` since dealing with the first decision tree.

By plugging in all the `Pi` values identified from Step 1:

```
r11 = y1 - P1 = 1 - 0.667 = 0.333
r21 = y2 - P2 = 0 - 0.667 = -0.667
r31 = y3 - P3 = 1 - 0.667 = 0.333
```

![](Images/9789815136982-C6-P19.jpg)

`squared_error` is used as the measure of the quality/purity of the split. The optimal value of the child node after split is 0 (i.e., the purest child node), e.g., for the leaf node on the right (i.e., the 2nd leaf node), it is calculated as follows:

```
mean = (0.333 + (-0.667)) / 2 = -0.167

squared_error = ((0.333 - (-0.167))^2 + (-0.667 - (-0.167))^2) / 2 = 0.25
```

Next, before diving into **Step 2(c)**, let us quickly review the Taylor series.

```
f(x) = f(a) + f'(a)/1! (x-a) + f''(a)/2! (x-a)^2 + f'''(a)/3! (x-a)^3 + …
```

Here, `a` is a constant number, and `x` represents the independent variable.

Take a simple function, `f(x) = e^x`, for demonstration:

```
f'(x) = e^x
f''(x) = e^x
f'''(x) = e^x
```

Let `a=0`, then `f(a)=1`, `f'(a)=1`, `f''(a)=1`, `f'''(a)=1`.

Apply the Taylor series formula:

```
∴ f(x) = 1 + 1/1! x + 1/2! x^2 + 1/3! x^3 + …
```

A quick validation can be conducted for the Taylor series expansion. If using the original function `f(x)=e^x`, when `x=0.5`, `e^0.5=1.649`. If using the Taylor Series expansion:

```
1 + 1/1! x + 1/2! x^2 + 1/3! x^3 = 1 + 0.5 + 1/2(0.5^2) + 1/6(0.5^3) = 1.646
```

As can be seen, a good approximation is obtained when using Taylor Series.

Now, let us continue with the **Step 2(c)** of the gradient boosting classification.

![](Images/9789815136982-C6-P20.jpg)

Here, `Rjm` denotes the jth leaf node of the mth tree. In the first decision tree (i.e., `m = 1`), there are only 2 leaf nodes, `R11` and `R21` as shown below.

![](Images/9789815136982-C6-P21.jpg)

To find the minimum using the first-order derivative:

```
dL(y3, F0(x3) + ã) / dã = 0

L'(y3, F0(x3)) + L''(y3, F0(x3)) * ã = 0

ã = -L'(y3, F0(x3)) / L''(y3, F0(x3))
```

As derived previously, the first-order differentiation of the loss function:

```
∵ ∂L(yi, F(xi)) / ∂F(xi) = -yi + Pi
∴ L'(yi, F(xi)) = -yi + Pi
∴ L'(yi, F0(xi)) = -yi + Pi = -ri1
```

Here, the `Pi` must be corresponding to `F0(xi)` since dealing with the first decision tree.

```
L'(y3, F0(x3)) = -y3 + P3 = -r31
-L'(y3, F0(x3)) = y3 - P3 = r31
```

Second-order differentiation is nothing but the first-order differentiation of the first-order derivative. Besides, always bear in mind that `Pi = e^log(odds_i) / (1 + e^log(odds_i))` and `F(xi) = log(odds_i)` when reading this section of gradient boosting classification. So, the differentiation with respect to `F(xi)` is the same as the differentiation with respect to `log(odds_i)`.

![](Images/9789815136982-C6-P22.jpg)

Do not forget the first order differentiation derived above:

```
L'(yi, F0(xi)) = -yi + Pi = -ri1
```

So, finally gamma value for the 1st leaf `R11`:

```
ã = -L'(y3, F0(x3)) / L''(y3, F0(x3)) = r31 / (P3(1-P3)) = 0.333 / (0.667(1-0.667)) = 1.5
```

∴ `ã11 = 1.5`

![](Images/9789815136982-C6-P23.jpg)

Let us summarize our findings and simplify the calculations of the `ã` value for each leaf node. As observed from the final `ã` expression right above, the numerator is just the sum of residuals of the samples allocated to the leaf node (e.g., `r11 + r21`), and the denominator is just the sum of `Pi(1-Pi)` of the samples allocated to the leaf node (e.g., `P1(1-P1) + P2(1-P2)`). We can straightway apply these relationships directly from the next decision tree onwards.

![](Images/9789815136982-C6-P24.jpg)

By now, we have finished the first decision tree (i.e., `m=1`) of Step 2.

Assume a total of 2 decision trees (i.e., `M=2`) are to be built for the gradient boosting model in this simple numerical example. Let’s continue the computation for the 2nd decision tree.

![](Images/9789815136982-C6-P26.jpg)
![](Images/9789815136982-C6-P27.jpg)
![](Images/9789815136982-C6-P28.jpg)

Since we assumed the gradient boosting classifier comprises 2 decision trees only in this example, we have completed the whole Step 2 and the model training. Then, in the end, the calculated probability needs to be mapped to class/label (i.e., 0 or 1). Similar to Chapter 4 for logistic regression, the default threshold of 0.5 is then employed. If `P ≥ 0.5`, it will be rounded up to 1 and predicted as class 1; whereas, if `P < 0.5`, it will be rounded down to 0 and predicted as class 0.

![](Images/9789815136982-C6-P29.jpg)
![](Images/9789815136982-C6-P30.jpg)

Looking back, we used the following expression in Step 2(d) when `m=2`:

```
F2(xi) = F1(xi) + á(ãj2 | xi ∈ Rj2)
```

Do not forget that we applied this expression in Step 2(d) when `m=1`:

```
F1(xi) = F0(xi) + á(ãj1 | xi ∈ Rj1)
```

If concatenating them together, we can get this expression:

```
F2(xi) = F0(xi) + á(ãj1 | xi ∈ Rj1) + á(ãj2 | xi ∈ Rj2)
```

Then, converting `F2(xi)` to predicted probability by:

```
Pi = e^log(odds_i) / (1 + e^log(odds_i)) = e^F2(xi) / (1 + e^F2(xi))
```

This will be our trained gradient boosting classification model for this simple example!

Here, `(ãj1 | xi ∈ Rj1)` and `(ãj2 | xi ∈ Rj2)` are the values we can find from the first and second decision trees, respectively. `á` is the learning rate, and we set it as 0.5 in this example.

Visually, the model is like this:

**Step 3. Output Fm(x)**

![](Images/9789815136982-C6-P31.jpg)

Finally, we come to the 3rd and last step of the algorithm, making predictions for previously unseen data (i.e., new data) using the trained gradient boosting classification model. For instance, if there is a house with 3 bedrooms, the predicted class by the model will be:

```
0.693 + 0.5 * 1.5 + 0.5 * -0.973 = 0.9565

P = e^0.9565 / (1 + e^0.9565) = 0.7224
```

Since `P ≥ 0.5`, the predicted class will be 1, which means it is easy to sell this house with 3 bedrooms.

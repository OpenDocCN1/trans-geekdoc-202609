
averaged and added to the latest gradient. The resulting smoothed out composite gradient is then used to establish the direction of the next step. The new update equation for \(\boldsymbol{w}\) after applying momentum is

```
\(\boldsymbol{w}^{(t+1)} = \boldsymbol{w}^{(t)} - \ell \times \boldsymbol{m}_{dw}^{(t+1)}.\) (10.4.3)
```

Initially, \(\boldsymbol{m}_{dw}^{(0)} = \boldsymbol{0}\) in Eq. (10.4.2). Then, it increases as the gradients are computed and a history is developed. The use of momentum in conjunction with gradient descent has been found to be highly effective in neural networks and is the foundation of the Adam optimizer.

**Exercise:** Given that \((dJ(\boldsymbol{w})/d\boldsymbol{w})^{(0)} = 5\), \(\boldsymbol{m}_{dw}^{(0)} = 0\), and \(w^{(0)} = 0.1\), compute the value of \(w^{(1)}\) using the momentum equation with \(\alpha_1 = 0.9\) and \(\ell = 0.05\).

**Ans.:** The momentum term is given by

```
\(m_{dw}^{(1)} = \alpha_1 m_{dw}^{(0)} + (1 - \alpha_1) d\boldsymbol{w}^{(0)} = 0.9 \times 0 + 0.1 \times 5 = 0.5.\)
```

Therefore, \(w^{(1)} = 0.1 - 0.05 \times 0.5 = 0.075\). (Without momentum, it would be \(w^{(1)} = 0.1 - 0.05 \times 5 = -0.15\).)

## 10.4.2 rmsprop Approach

While the momentum adjustment to gradient descent is quite effective, it does not account for the fact that different parameters will produce gradients that range in size from the very small to the very large. Ideally, we would like to have **a different learning rate for each parameter** but as the parameter space increases, this can become an unwieldy and expensive task, especially if the learning rate is varied from one iteration to another. Instead, this problem can be handled by simply dividing the learning rate by the absolute value of the derivative as follows:

```
\(\boldsymbol{w}^{(t+1)} = \boldsymbol{w}^{(t)} - \ell \left( \frac{dJ(\boldsymbol{w})/d\boldsymbol{w}}{|dJ(\boldsymbol{w})/d\boldsymbol{w}|} \right)^{(t)}.\) (10.4.4)
```

Therefore, the final term is essentially the sign of each of the gradients rather than the actual gradient. This is similar in principle to the aLASSO penalty function of Chapter 5.

This approach, while simple in nature, has a number of problems, one of which has to do with the absence of the magnitudes of the gradients and the second having to do with absence of the exponentially weighted aspect of the gradients seen in the momentum approach. The rmsprop approach resolves both issues. Rather than using the absolute value term in the denominator, it is more effective to replace it by a root-mean-square value, where the mean is actually the exponentially weighted value. That is, take the square of the gradients of past iterations and then average them and take the square root to obtain the correct scale. In particular, let us define a new term as follows:

```
\(\boldsymbol{r}_{dw}^{(t+1)} = \alpha_2 \boldsymbol{r}_{dw}^{(t)} + (1 - \alpha_2) \left( \frac{dJ(\boldsymbol{w})}{d\boldsymbol{w}} \right)^{(t)} \times \left( \frac{dJ(\boldsymbol{w})}{d\boldsymbol{w}} \right)^{(t)},\) (10.4.5)
```

where \(\alpha_2 \in [0, 1]\) and is typically set to 0.999. Then, the updated equation becomes

```
\(\boldsymbol{w}^{(t+1)} = \boldsymbol{w}^{(t)} - \ell \frac{(dJ(\boldsymbol{w})/d\boldsymbol{w})^{(t)}}{\sqrt{(\boldsymbol{r}_{dw})^{(t+1)}}}.\) (10.4.6)
```

In this form, the derivative is being scaled by \(\sqrt{\boldsymbol{r}_{dw}}\) rather than the absolute value of the gradient. Since the new formulation is intended to modify the learning rate, we could conveniently rewrite it for better understanding as follows:

\(\boldsymbol{w}^{(t+1)} = \boldsymbol{w}^{(t)} - \frac{\ell}{\sqrt{(\boldsymbol{r}_{dw})^{(t+1)}}} \left( \frac{\partial J(\boldsymbol{w})}{\partial \boldsymbol{w}} \right)^{(t)}.\) (10.4.7)

Now the square root of the exponentially weighted squared gradients is in the denominator of the learning rate and implies that each parameter adjusts the learning rate based on its own exponential history of gradients. This has been found to be a very effective update equation. However, if the derivative is 0, the equation goes to infinity. To resolve this issue, we can add a small value, such as \(\varepsilon = 10^{-8}\), to the denominator as follows:

\(\boldsymbol{w}^{(t+1)} = \boldsymbol{w}^{(t)} - \frac{\ell}{(\sqrt{(\boldsymbol{r}_{dw})^{(t+1)}} + \varepsilon)} \left( \frac{\partial J(\boldsymbol{w})}{\partial \boldsymbol{w}} \right)^{(t)}.\) (10.4.8)

**Exercise:** Given that \(dw^{(0)} = (\partial J(w)/\partial w)^{(0)} = 5\), \(r_{dw}^{(0)} = 0\), and \(w^{(0)} = 0.1\) compute the value of \(w^{(1)}\) using the rmsprop equation with \(\alpha_2 = 0.999\), \(\varepsilon = 0\), and \(\ell = 0.05\).

**Ans.:** The rmsprop term is given by

\(r_{dw}^{(1)} = \alpha_2 r_{dw}^{(0)} + (1 - \alpha_2) dw^{(0)} \times dw^{(0)} = 0.999 \times 0 + 0.001 \times 5^2 = 0.025\)

Therefore, \(w^{(1)} = 0.1 - \frac{0.05}{\sqrt{0.025}} \times 5 = -1.48\). \(\square\)

## 10.4.3 Optimizer Warm-Up Phase

When applying momentum or rmsprop, there is a startup problem due to the fact that there is no history to draw from for the exponentially weighted gradients at the beginning. In fact, it is not until roughly 10 iterations have been computed that the requisite amount of history is available (assuming \(\alpha_1 = 0.9\)). Therefore, some mechanism is needed to "warm-up" the two methods until enough iterations of history exist. One way to do this is to divide the corresponding terms for each method by a quantity that starts with a large fraction of the initial gradients and then reaches the steady-state value when enough history exists; i.e. the corrected values are

\(\boldsymbol{m}_{dw}^{\text{corr}} = \frac{\boldsymbol{m}_{dw}^{(t+1)}}{1 - \alpha_1^{t+1}}\)

and

\(\boldsymbol{r}_{dw}^{\text{corr}} = \frac{\boldsymbol{r}_{dw}^{(t+1)}}{1 - \alpha_2^{t+1}},\)

respectively. Assuming \(t = 0\) at the start, the denominator for momentum is initially \((1 - \alpha_1)\). Then for \(t = 1\), we use \((1 - \alpha_1^2)\), for \(t = 2\), we use \((1 - \alpha_1^3)\), and so on. The same holds for rmsprop with \(\alpha_2\). Eventually, the denominator approaches 1 in both cases (given that \(\alpha_1\) and \(\alpha_2\) are always less than 1), thereby ending the warm-up phase.

**Exercise:** Compute the correction terms for momentum and rmsprop for the previous two problems.

**Ans.:** The corrected terms are

\( m_{dw}^{corr} = \frac{0.5}{1 - 0.9} = 5 \)

and

\( r_{dw}^{corr} = \frac{0.025}{1 - 0.999} = 25 \).

**Exercise:** Given that \( dw^{(0)} = 5 \), compute \( w^{(1)} \) using the corrected values of \( m_{dw} \) and \( r_{dw} \) of the previous two exercises.

**Ans.:** Using the corrected terms above, we obtain for momentum,

\( w^{(1)} = 0.1 - 0.05 \times 5 = -0.15 \)

and for rmsprop,

\( w^{(1)} = 0.1 - 0.05 \times 5 / \sqrt{25} = 0.05 \).

They are different even in the warm-up phase.

## 10.4.4 Adam Optimizer

Each of the three methods above was presented as separate approaches. However, the Adam (ADAptive Minimizer) optimizer combines all of them into one tool. It applies rmsprop to the momentum update equation along with the warm-up correction to produce a very powerful method that has proven to be extremely efficient at finding a regional minimum in deep neural networks. The combination of the methods produces the following update equation:

\( w^{(t+1)} = w^{(t)} - \ell \times \frac{m_{dw}^{corr}}{\sqrt{r_{dw}^{corr}} + \varepsilon} \). (10.4.9)

**Exercise:** Given that \( (\partial J(w) / \partial w)^{(0)} = 5 \), \( r_{dw}^{(0)} = 0 \), and \( w^{(0)} = 0.1 \), compute the value of \( w^{(1)} \) using Eq. (10.4.9) with \( \alpha_1 = 0.9 \), \( \alpha_2 = 0.999 \), \( \epsilon = 0 \), and \( \ell = 0.05 \).

**Ans.:** Using the results from prior exercises, we find that

\( m_{dw}^{corr} = 5 \) and \( r_{dw}^{corr} = 25 \).

Therefore, \( w^{(1)} = 0.1 - \frac{0.05}{\sqrt{25}} \times 5 = 0.05 \).

As shown in Algorithm 10.1, the Adam optimizer begins by initializing \( \alpha_1 \), \( \alpha_2 \), and \( w^{(0)} \) to the appropriate values. In addition, the starting values for \( m_{dw} \) and \( r_{dw} \) are set and the learning rate is specified. The algorithm then enters the convergence loop where the momentum, rmsprop, and warm-up terms are

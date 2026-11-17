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

# 10.4.2 rmsprop Approach

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
$\prod_{i=1}^{n}\prod_{k=1}^{K}p_{ik}^{y_{ik}},$(4.4)

where we recall that $a_0 = 1$ and $a_1 = a$.

As an exercise, you can compare this to Equation 2.22 and confirm that the binomial likelihood corresponds to Equation 4.4 in the case where $K = 2$ (noting that the definition of $y_i$ has changed from a scalar number to a binary vector of length 2).

Taking the log of Equation 4.4 and multiplying by $-2$ yields the multinomial deviance:

$\text{dev} = -2\sum_{i}\sum_{k}y_{ik}\log(p_{ik})\ .$(4.5)

Finally, applying the logit link of Equation 4.3 to get $p_{ik}$ as functions of the regression coefficients $B = [\beta_1\dots\beta_K]$, we obtain

$\begin{gathered} \text{dev}(B) = -2\sum_{i=1}^{n} y_{ik}\log p_{ik}(x_i'B) \\ = -2\sum_{i=1}^{n}\left[\sum_{k=1}^{K}y_{ik}\ \ x_i'\beta_k - m_i\log\left(\sum_{k=1}^{K}e^{x_i'\beta_k}\right)\right],\end{gathered}$(4.6)

where $m_i = \sum_{k}y_{ik}$ is the total number of "successes" for observation $i$. (It is a good math exercise to derive the second line from first line here.) In the current classification examples, $m_i = 1$ because only one outcome is possible. However, Equation 4.6 will be useful in other settings where $y_{ik}$ instances are counts and can be any positive integer. For example, in text analysis the $y_{ik}$ will be counts for words in a document.

As always, we will estimate our multinomial logistic regressions through penalized deviance minimization:

$\hat{B}_{\lambda}=\operatorname{argmin}\left\{-\frac{2}{n}\sum_{i=1}^{n}y_{ik}\log p_{ik}\left(x_i'B\right)+\lambda\sum_{k}\sum_{j}\left|\beta_{kj}\right|\right\}.$(4.7)

Here, we have a single penalty $\lambda$ across all classes $k$; we'll relax this in later estimation strategies.
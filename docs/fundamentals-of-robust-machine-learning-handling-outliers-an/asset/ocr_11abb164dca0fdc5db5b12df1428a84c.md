![](bbox=[0.11, 0.1, 0.88, 0.38])

Figure 7.14 PDFs of the quantile function for five different values of \(\tau\). The five plots are all combined in the bottom-right panel.

A graph of \(\kappa\) vs. \(\tau\) is provided in Figure 7.13 using a number of different values of \(\tau\). The distributions can now be plotted to reveal their characteristics.

Starting with Eq. (7.8.3) and the normalizing constants \(\kappa\) given in Figure 7.13, different values of \(\tau\) were selected and their associated distributions plotted in Figure 7.14. The cases shown are for \(\tau = 0, 0.25, 0.5, 0.75,\text{and } 1.0\). There is a one-to-one correspondence between Figures 7.14 and 7.5. The distributions for \(\tau = 0.25\) and \(\tau = 0.75\) are mirror images, as are distributions for \(\tau = 0.0\) and \(\tau = 1.0\). The only symmetric distribution is associated with \(\tau = 0.5\).

Since we now have the equations for the PDFs, we can find the expected values and variances. For example, setting \(\tau = 0.5\), we find that

\(\mathbb{E}[X] = 0\) (7.8.4)

and noting that \(\mathbb{E}[X^2] = 8.29\) via integration, we have

\(\text{Var}(X) = \mathbb{E}[X^2] - \mathbb{E}[X]^2 = 8.29 - 0^2 = 8.29\). (7.8.5)

However, for \(\tau = 0.75\), we obtain

\(\mathbb{E}[X] = -3.7\) (7.8.6)

and

\(\text{Var}(X) = \mathbb{E}[X^2] - \mathbb{E}[X]^2 = 34.4 - (-3.7)^2 = 20.7\). (7.8.7)

All of the distributions encountered in this book thus far have a mean that is 0 but in quantile regression, the associated PDFs do not have a mean of 0 except for \(\tau = 0.5\). From the above, the mean of the distribution for \(\tau = 0.75\) is negative rather than 0 and for \(\tau = 0.25\) it would be positive rather than 0. This can be seen in Figure 7.14. Furthermore, the variance is not constant but increases as \(\tau\) approaches either 1 or 0.
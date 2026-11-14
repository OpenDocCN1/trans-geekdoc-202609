\(\epsilon\)-SVR, then we have \(e_{LS-SVR} < e_{SVR}\), that is,

\(\hat{P}_{h1} - P_h - \hat{P}_{g1} + P_g > \hat{P}_{h2} - P_h - \hat{P}_{g2} + P_g.\) (7.13)

Let us denote \(\beta_h = \alpha_h - \alpha_h^*\) and \(\beta_g = \alpha_g - \alpha_g^*\), and simplifying (7.13), we get

\(\beta_h k(x, x_h) + b - \beta_g k(x, x_g) - b > \eta_h k(x, x_h) + b_1 - \eta_g k(x, x_g) - b_1.\) (7.14)

Since the kernel matrix elements \(k(x, x_i)\) are equal for \(\epsilon\)-SVR and LS-SVR, the equation can be further simplified as

\(k(x, x_h)\big(\beta_h - \eta_h\big) - k(x, x_g)\big(\beta_g - \eta_g\big) > 0.\) (7.15)

Thus, if (7.15) is satisfied, then LS-SVR will outperform \(\epsilon\)-SVR during ramp events.

# ## 7.2.2 Ramp event error analysis for TSVR and \(\epsilon\)-TSVR

Similarly, TSVR and \(\epsilon\)-TSVR can be compared based on the same approach. Let \(e_{TSVR}\) and \(e_{\epsilon-TSVR}\) denote the errors in the wind ramp power between points \(g\) and \(h\) based on TSVR and \(\epsilon\)-TSVR, respectively. We have

\(\hat{P}_{g3} = \frac{1}{2}(w_1 + w_2)k(x, x_g) + \frac{1}{2}(b_1 + b_2),\) (7.16)
\(\hat{P}_{h3} = \frac{1}{2}(w_1 + w_2)k(x, x_h) + \frac{1}{2}(b_1 + b_2),\) (7.17)
\(\hat{P}_{g4} = \frac{1}{2}(u_1 + u_2)k(x, x_g) + \frac{1}{2}(b_3 + b_4),\) (7.18)
\(\hat{P}_{h4} = \frac{1}{2}(u_1 + u_2)k(x, x_h) + \frac{1}{2}(b_3 + b_4),\) (7.19)

where \(b_1\), \(b_2\) and \(b_3\), \(b_4\) are bias terms, and \(\hat{P}_{g3}\), \(\hat{P}_{h3}\) and \(\hat{P}_{g4}\), \(\hat{P}_{h4}\) are the predicted values of wind power using TSVR and \(\epsilon\)-TSVR, respectively. The forecasted ramp power \(\hat{\Delta P}_{gh}\) is then compared, and the errors in \(\Delta P_{gh}\) for TSVR and \(\epsilon\)-TSVR are

\(e_{TSVR} = \hat{P}_{h3} - P_h - \hat{P}_{g3} + P_g, \quad e_{\epsilon-TSVR} = \hat{P}_{h4} - P_h - \hat{P}_{g4} + P_g.\) (7.20)

Comparing the ramp power errors, if \(e_{TSVR} > e_{\epsilon-TSVR}\), then we get

\(\hat{P}_{h3} - P_h - \hat{P}_{g3} + P_g > \hat{P}_{h4} - P_h - \hat{P}_{g4} + P_g.\) (7.21)
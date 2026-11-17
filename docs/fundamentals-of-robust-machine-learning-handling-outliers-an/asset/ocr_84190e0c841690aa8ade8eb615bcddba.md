this approach, the crossing problem can be reduced or removed entirely depending on the selection of the robustness coefficient, \( a \). Notably, the loss function can be optimized using gradient descent, which is routinely used in machine learning.

A number of qualitative and quantitative techniques were presented to compare different methods of carrying out quantile regression. The number of non-monotonic events, called dips, can be detected using a QP plot as a measure of the severity of the crossing problem. Other metrics such as the maximum error, average error, and sum of errors can also be computed. These values can be used to select the robustness coefficient suitable for the smooth check function since there is an inherent monotonicity-error trade-off which needs to be balanced.

The use of the log-cosh formulation also leads to a deeper understanding of quantile regression. The source of the crossing problem can be identified as partially due to the kinks in the check function and partially due to infinite solutions possible when solving the standard quantile loss function using linear programming methods. In addition, the maximum-likelihood procedure can be applied to explore the distributions associated with the quantiles in the log-cosh case. Furthermore, the PDFs of different quantiles can be plotted and statistical quantities, such as expectation and variance, can be computed. Indeed, this formulation is a promising approach for use in robust machine learning for quantile regression.

# Problems

+   7.1 Plot the loss terms for \( L_1 \), the check function of Eq. (7.4.2) using \( \tau = 0.5 \) and the log-cosh quantile term of Eq. (7.5.7) using \( \tau = 0.5 \). Compare and contrast the three cases.

+   7.2 For the QP plot below, compute the number of dips (non-monotonic events), the maximum error, the average error, and the sum of errors.

![](bbox=[0.109, 0.588, 0.477, 0.798])

+   7.3 Let \( a = 10 \) in Eq. (7.5.6). Plot the \( \rho_{SMQ}(x; \tau) \) loss term for the same \( \tau \) values as in Figure 7.5. Plot \( \psi_{SMQ}(x; \tau) \) for the same cases. Compare the results obtained for \( a = 10 \) with the results for \( a = 1.5 \).
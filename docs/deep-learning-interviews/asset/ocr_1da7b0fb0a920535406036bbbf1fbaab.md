| 0.95= .05 | hereditary-disease is NOT present $\lbrack \ddot{A}\rbrack$ (probability of false alarm). |
| --- | --- |
| P(B|A)= 0.95 | The probability that the test will yield a positive result [B] if hereditary-disease is present [A] (probability of detection). |
| $P( \overline{B}\lvert A)=1-0.95=.05$ | The probability that the test will yield a negative result [$\overline{B}$] if hereditary-disease is present [A]. |

TABLE 3.1: Probability values of hereditary-disease detection.

# **SOL-45 ☐ CH.SOL-3.16.**

*We first enumerate the probabilities one by one:*

$P(\mathit{Dercum}\mid \mathit{female}) = 0.05,\tag{3.36}$

$P(\mathit{Dercum}\mid \mathit{male}) = 0.0025,\tag{3.37}$

$P(\mathit{male}) = P(\mathit{female}) = 0.5.\tag{3.38}$

*We are asked to find $P(\mathit{female}\mid\mathit{Dercum})$. Using Bayes Rule:*

$P(\mathit{female}\mid\mathit{Dercum}) = \dfrac{P(\mathit{Dercum}\mid\mathit{female})P(\mathit{female})}{P(\mathit{Dercum})}.\tag{3.39}$

*However we are missing the term $P(\mathit{Dercum})$. To find it, we apply the Law of Total Probability:*

$\begin{aligned} P(\mathit{Dercum}) & = P(\mathit{Dercum}\mid \mathit{female})P(\mathit{female}) \\
& + P(\mathit{Dercum}\mid \mathit{male})P(\mathit{male}) \\
& = \\
& 0.05 \cdot 0.5 + 0.0025 \cdot 0.5 = 0.02625. \end{aligned}$

*And finally, returning to eq. (3.39):*

$P(\mathit{female}\mid\mathit{Dercum}) = \dfrac{0.05 \cdot 0.5}{0.02625} \approx 0.9524\tag{3.40}$

*Note: How could this result be reached with one mathematical equation?*
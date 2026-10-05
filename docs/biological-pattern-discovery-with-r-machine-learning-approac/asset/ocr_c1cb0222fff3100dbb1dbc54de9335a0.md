The above sequences were used again to examine whether this is true. Figure 7.8 shows the frequency pattern of three sequences (SARS-CoV, SARS-CoV-2 and Yersinia pastis) based on 3-mer words. The frequency of some 3-mer words demonstrated a significant difference between three sequences.

![](bbox=[0.335, 0.239, 0.664, 0.401])

Fig. 7.8. 3-mer pattern for MT042778 (M), AB889999 (A) and QANK01002681 (Q).

Table 7.20 shows the correlation coefficients, it can be seen that the correlation coefficient between the 3-mer vector ($X_{SARS-CoV}$) of the SARS-CoV and the 3-mer vector ($X_{SARS-CoV-2}$) of the SARS-CoV-2 sequences was small, being 0.868. The correlation coefficient between $X_{SARS-CoV}$ and the 3-mer vector ($X_{Yersinia}$) of the Yersinia pastis was small, being 0.192. The correlation coefficient between $X_{SARS-CoV-2}$ and $X_{Yersinia}$ was the least, being 0.079.

Table 7.20. Correlation coefficients for MT042778, AB889999 and QANK01002681.

| MT042778 | AB889999 | QANK01002681 |
|---|---|--|
| MT042778 | 1.000 | 0.868 | 0.079 |
| AB889999 | 0.868 | 1.000 | 0.192 |
| QANK01002681 | 0.079 | 0.192 | 1.000 |

A hierarchical cluster model was constructed for this 3-mer data calculated from three sequences. The model shows that MT042778 (M for SARS-CoV-2) and AB889999 (A for SARS-CoV) were merged first while QANK01002681 (Q for *Yersinia pastis*) was merged with the subtree of MT042778 and AB889999 with a larger distance. Figure 7.9
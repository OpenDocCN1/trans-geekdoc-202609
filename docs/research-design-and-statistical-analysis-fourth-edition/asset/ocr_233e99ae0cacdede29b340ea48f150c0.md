# 332 Research Design and Statistical Analysis

than the repeated-measures design if the column variability makes a large contribution to the total variability. We can see this in the following estimate of the mean square error for the repeated-measures design ($MSE_{RM}$) derived from the Latin square ANOVA results:

```
$MSE_{RM} = \frac{(a-1)MSE_{LS}+MSE_C}{a} \quad (12.2)$
```

where on the right are the residual and column mean squares from the Latin square ANOVA. Notice that if $MSE_C=0$, $estMSE_{RM}=(a-1)/MSE_{LC}$ and the repeated-measures design is more efficient. However, as $MSE_{LC}$ increases, the point at which $estMSE_{RM}>MSE_{LC}$ is quickly reached. Clearly, the loss of four degrees of freedom, the Latin square design will usually provide greater power and more precise estimates of population parameters than the repeated-measures design.

# 12.7 Summary

Chapter 12 has introduced four approaches to designing experiments and analyzing the data. Each approach seeks to reduce error variance with corresponding benefits for power and parameter estimates.

+   * *The × blocks design* attempts to remove some sources of individual differences relevant to establishing blocks of participants using a concomitant variable.
* *ANCOVA assigns participants randomly to conditions using a concomitant variable to statistically remove some sources of individual differences.
* *The repeated-measures design* involves testing participants in all the conditions of the experiment with the result that individual difference variance may be entirely removed from the error term of the design.
* *The Latin square design is a design in which the sequence of conditions is counterbalanced across participants. This procedure permits not only the contribution of individual differences from the error mean square, but also the contribution of temporal (sequential) effects due to fatigue or practice.

When successfully executed, both the $T \times B$ and ANCOVA reduce error relative to the completely randomized design; the $RM$ design reduces error further; and the Latin square design reduces error further still.

Although we have emphasized the increased efficiency of these four designs and analysis, efficiency is not the only consideration in selecting a research design. We have noted that designs differ in how effort and expense they require to implement. In addition, more complex designs typically involve more stringent assumptions and more complex statistical models. We will consider these issues thoroughly when we study each of these alternative design.

# Exercises

12.1 [Comparing CR and $T \times B$ designs] A teacher compared three types of instructional methods (A) on mathematics final exam scores (Y). In the research design, students were first divided into four blocks (B) of 15 each based on a pretest (X), then assigned to the three conditions. In summary, the design had three levels of A
# 9.5 Interpreting hypothesis tests

evidence to say so.” In other words, there is an absence of enough proof. However, the absence of proof is not proof of absence.

To shed light on this distinction, let's use the United States criminal justice system as an analogy. A criminal trial in the United States is a similar situation to hypothesis tests whereby a choice between two contradictory claims must be made about a defendant who is on trial:

+   1. The defendant is truly “innocent” or “guilty.”
2. The defendant is presumed “innocent until guilty.”
3. The defendant is found guilty only if there is strong evidence that the defendant is guilty. The phrase “beyond a reasonable doubt” is often used as a guideline for cutoff for determining when enough evidence exists to find the defendant guilty.
4. The defendant is found to be “not guilty” or “guilty” in the ultimate verdict.

In other words, not guilty verdicts are not suggesting the defendant is innocent, but instead that“while the defendant may still actually be guilty, there was not enough to prove this fact.” Now let's make the connection with hypothesis tests:

+   1. Either the null hypothesis $H_0$ or the alternative hypothesis $H_A$ is true.
2. Hypothesis tests are conducted assuming the null hypothesis $H_0$ is true.
3. We reject the null hypothesis $H_0$ in favor of $H_A$ if the evidence found in the sample suggests that $H_A$ is true. The significance level $\alpha$ is used as a guideline to set the threshold on how strong of evidence we require.
4. We ultimately decide to either “fail to reject $H_0$” or “reject $H_0$”.

So while gut instinct may suggest “failing to reject $H_0$” and “accepting $H_0$” are equivalent statements, they are not. “Accepting $H_0$” is equivalent to finding a defendant not “innocent”, but rather they find them “not guilty.” Putting things differently, defense attorneys do not need to prove that their clients are innocent, rather they need to prove that clients are “guilty beyond a reasonable doubt.”

So going back to our songs in Section 9.4, recall that our hypothesis test was $H_0: p_m - p_d = 0$ versus $H_A: p_m > p_d$ and that we used a pre-specified significance level of $\alpha = 0.1$. We found a $p$-value of $0.065$. Since the $p$-value was smaller than $0.1$, we rejected $H_0$. In other words, we found needed levels of evidence in this particular sample to say that $H_0$ is false at the $\alpha = 0.1$ significance level. We also state this conclusion using non-statistical language: we found enough evidence in this data to suggest that there was a difference in the popularity of our two genres of music.
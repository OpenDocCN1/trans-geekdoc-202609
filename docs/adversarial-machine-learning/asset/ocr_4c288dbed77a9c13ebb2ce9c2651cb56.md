![](bbox=[0.203, 0.115, 0.902, 0.646])

Figure 5.5 Effect of the focused attack on three representative emails—one graph for each target. Each point is a token in the email. The x-axis is the token's spam score in Equation (5.2) before the attack (0 indicates ham and 1 indicates spam). The y-axis is the token's spam score after the attack. The x's are tokens that were included in the attack, and the o's are tokens that were not in the attack. The histograms show the distribution of spam scores before the attack (at bottom) and after the attack (at right).

on the test spam email (y-axis). The solid line shows the fraction of target spam classified as ham or unsure spam, while the dashed line shows the fraction of spam classified as ham. In the absence of attack, SpamBayes only misclassifies about 10% of the target spam emails (including those labeled unsure). If the attacker can insert a few hundred attack emails (1% of the training set), then SpamBayes misclassifies more than 80% of the target spam emails.

Further, the attack has a minimal effect on regular ham and spam messages. Other spam email messages are still correctly classified since they do not generally have the
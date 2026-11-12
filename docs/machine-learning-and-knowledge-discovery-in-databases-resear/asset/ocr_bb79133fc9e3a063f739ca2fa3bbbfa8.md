(assuming that population variance of SLN and Veto+SLN are the same)

\(S_d^2 = \frac{(n-1)S_s^2 + (n-1)S_v^2}{2n-2} = \frac{S_s^2 + S_v^2}{2}\)

where, \(S_s^2\) and \(S_v^2\) are sample variance for SLN and Veto+SLN variants respectively. Then, the test statistic is given by

\(T = \frac{\bar{d} - 0}{\sqrt{S_d^2 \left(\frac{1}{n} + \frac{1}{n}\right)}} = \frac{\sqrt{n}\bar{d}}{\sqrt{S_s^2 + S_v^2}}\)

The significance level \(\alpha\) test is to \(reject\) \(H_0\) if \(T \ge t_{\alpha, 2n-2}\); not reject \(H_0\), otherwise. Here \(t_{\alpha, 2n-2}\) denotes t-distribution with degree of freedom \(2n - 2\). Significance level \(\alpha\) means that the probability of \(H_0\) getting rejected when it is actually true is never greater than \(\alpha\). In our experiment, we expected the data to support the alternative hypothesis \(H_1\), but do not want to make the assertion unless the data really gives convincing support. So, we have set up the test so that the alternate hypothesis is the one that we expect data to support and we hope to prove. Alternate hypothesis in such setup is also called the research hypothesis. By choosing a small \(\alpha\) as the significance level, we minimize the risk of incorrectly concluding that the data supports the research hypothesis when it is actually false [29]. Common choices for \(\alpha\) are 0.1, 0.05, and 0.005; here, we choose \(\alpha = 0.05\).

# Illustrative Examples.

(A) Let us look at a few examples. For Citeseer data set, GCN architecture in presence of 5% noise, we have \(\bar{x}^s = 73.92, \bar{x}^v = 72.27, S_s = 1.1, S_v = 0.7\) (from Table 2), and thus, \(T = \frac{\sqrt{10} \times (73.92-72.27)}{\sqrt{1.1^2+0.7^2}} = 4.00184\). For significance level \(\alpha = 0.05\), the value of \(t_{\alpha, 18} = 1.734\). As, \(T > t_{0.05, 18}\) so we reject \(H_0\). It means for the Citeseer dataset at 5% noise, GCN performs worse in the presence of Veto + SLN as compared to SLN, and the probability of incorrectly concluding this is at most 5%. In fact, in this case, \(T > t_{0.0005, 18} = 3.921643\), so the probability of incorrectly concluding rejection of \(H_0\) is at most 0.05%.

(B) For Citeseer data set, GIN architecture in presence of 45% noise, we have \(\bar{x}^s = 42.29, \bar{x}^v = 37.98, S_s = 8.8, S_v = 5.4\) (from Table 2), and hence, \(T = 1.32\). This means, \(T < t_{0.05, 18}\) and we accept \(H_0\).

# Analysis of Hypothesis Tests:

We perform hypothesis testing for all datasets, for all GNN architectures and all noise robust algorithms and the results are presented in Table 5. We divide noise levels into three subclass, Low (5% – 15% noise levels), Medium (20% – 35% noise levels), and High (40% – 50% noise levels). Overall represents aggregate across all noise levels. We revisit questions asked in Sect. 4.4 through the lens of hypothesis testing. For GCN architectures, we have 10 noise levels \(\times\) 3 datasets \(\times\) 2 sub-variants (SLN and PWN) = 60 hypothesis tests. Out of 60, we were able to reject 32 null hypotheses with
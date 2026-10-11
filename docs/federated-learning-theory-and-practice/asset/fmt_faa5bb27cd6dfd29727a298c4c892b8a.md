
For all experiments, pixel pattern backdoor attacks are performed in which the adversary aims to influence the model to misclassify inputs from a base label as a target label upon the presence of an attacker's chosen pattern (trigger). We set the adversarial trigger as a white square located at the top left corner of the image which roughly covers 9% of the entire image. The objective of backdoor attacks in GTSRB and SVHN datasets is to mispredict images of “Speed limit 80 miles per hour” as “Speed limit 50 miles per hour” and images of “digit 6” as “digit 1”, upon the presence of the white box trigger.

In the rest of the chapter, we denote each Meta-FL framework by two parameters as `MFL-i-j`, where `i` and `j` indicate the number and size of training cohorts, respectively. We also use a similar notation `FL-k` to describe baseline FL systems, where `k` indicates the size of the training cohort.

Similar to the analysis in [\[26\]](#Chp009_161-179_B978044319037700017X.xhtml#br0130), we consider fixed-frequency attack models to explore a wide range of attack scenarios. In the baseline FL, `Attack-f-k` describes a scenario where `k` sybils appear at every `f` rounds of training to mount their attack. For the case of Meta-FL setting, `Attack-f-k` describes the case where at every `f` round of training, `k` training cohorts contain an adversarial client.

### 9.5.2 Utility of meta-FL

In this section, we compare the utility of Meta-FL against the baseline setting in terms of model accuracy. In this experiment, we evaluate the utility of baseline and Meta-FL frameworks across various FL configurations and aggregation rules. Note that for a fair comparison, we make sure the number of clients participating in each round of model training is equal across both frameworks. [Fig. 9.2](#Chp009_161-179_B978044319037700017X.xhtml#f0020) reports the test accuracy of models trained in Meta-FL and baseline settings deploying different defenses and aggregation rules. As reflected, federated training with Meta-FL results in more accurate models compared to the baseline setting. All defenses and aggregation rules offer better utility in our framework. Even the Krum aggregation rule which has been known to cause a large drop in performance of the learned model in baseline FL [\[1\]](#Chp009_161-179_B978044319037700017X.xhtml#br0005),[\[2\]](#Chp009_161-179_B978044319037700017X.xhtml#br0010) can train models with comparable performances in Meta-FL.

![Figure 9.2 Comparing utility of Meta-FL against baseline FL in terms of model accuracy.](OEBPS/images/B978044319037700017X/gr003_u3.jpg)

[Figure 9.2](#Chp009_161-179_B978044319037700017X.xhtml#cf0205) Comparing utility of Meta-FL against baseline FL in terms of model accuracy.

### 9.5.3 Robustness of meta-FL

In this section, we systematically compare the capabilities of contemporary defenses against backdoor attacks in both baseline and meta federated learning. Our empirical evaluation in this section shows that all defenses benefit from the advantages discussed in Section [9.4](#Chp009_161-179_B978044319037700017X.xhtml#s0040) and offer better robustness in Meta-FL.

Figs. [9.3](#Chp009_161-179_B978044319037700017X.xhtml#f0025) and [9.4](#Chp009_161-179_B978044319037700017X.xhtml#f0030) report the performance of contemporary defenses against backdoor attacks on GTSRB and SVHN benchmarks, respectively. We extend our experiments to both Meta-FL (`MFL-15-5`) and baseline FL (`FL-5`) frameworks for each dataset. In our evaluations, we consider defenses such as Krum, coordinate-wise median (CWM), trimmed mean (TM), norm bounding (NB), differential privacy (DP), and RFA. Hyperparameter and implementation details of these techniques are as follows:

1.  For Krum, to meet the convergence condition `n ≥ 2f + 3`, we set `f = 6`.
2.  For trimmed mean, the parameter `β` is set to 0.20.
3.  For RFA, the maximum iteration of the Weiszfeld algorithm and the smoothing factor is set to 10 and `10^(−6)`, respectively.
4.  In norm bounding defense, as the original work [\[26\]](#Chp009_161-179_B978044319037700017X.xhtml#br0130) did not provide a recipe to decide the norm threshold `M`, we developed our own approach to determine `M`. In our experiments, at each round, we set the norm threshold `M` to the norm of the smallest aggregand to ensure all aggregands will have an equal `l2` norm before aggregation. In federated learning, as the global model converges, model updates (and therefore cohort aggregates) start to fade out and have smaller norms, and thus, setting a constant norm threshold for all training rounds would not be effective, which is why we took a dynamic approach to decide `M`.
5.  For differential privacy, the hyperparameter `M` is set similar to norm bounding and then a Gaussian noise `𝒩(0.0, 0.001²)` is added to the aggregate of updates (or cohort aggregates) before updating the global model.

![Figure 9.3 Evaluating performance of contemporary defenses against naive and model replacement backdoor attacks on GTSRB model.](OEBPS/images/B978044319037700017X/gr004_u1.jpg)

Figure 9.3 Evaluating performance of contemporary defenses against naive and model replacement backdoor attacks on GTSRB model.

![Figure 9.4 Evaluating performance of contemporary defenses against naive and model replacement backdoor attacks on SVHN model.](OEBPS/images/B978044319037700017X/gr005_u1.jpg)

Figure 9.4 Evaluating performance of contemporary defenses against naive and model replacement backdoor attacks on SVHN model.

We experiment with several attack scenarios to systematically evaluate the performance of each defense against adversaries with a wide range of resources at hand. As we move along the attack scenarios denoted on the horizontal axis of diagrams in Figs. [9.3](#Chp009_161-179_B978044319037700017X.xhtml#f0025) and [9.4](#Chp009_161-179_B978044319037700017X.xhtml#f0030), the adversary becomes more and more powerful and appears more frequently with more sybils at each round.

For a fair evaluation of contemporary defense across Meta-FL and baseline FL, we make sure the defender faces similar challenges in both frameworks. Throughout our experiments in this section, we set the number of training cohorts in Meta-FL equal to the number of selected clients in baseline FL to ensure that the server sees the same number of aggregands (client updates in baseline FL and cohort aggregates in Meta-FL) across both cases. Moreover, the way our attack scenarios are defined ensures that the same number of aggregands are adversarial across both frameworks.

Across both Meta-FL and baseline FL frameworks, the scaling factor for model replacement attack is set equal to the size of training cohorts to ensure that submissions from adversarial clients survive the averaging procedure and overpower the aggregate of their corresponding cohort. For attack scenarios in which multiple sybils appear in the same round, we assume they coordinate and divide the scaling factor among themselves evenly.

Figs. [9.3](#Chp009_161-179_B978044319037700017X.xhtml#f0025) and [9.4](#Chp009_161-179_B978044319037700017X.xhtml#f0030) show that *Meta-FL puts all defense at an advantage in mitigating against backdoor attacks.* Attack success rate of both the naive and model replacement approach in Meta-FL (solid lines) is lower than in baseline FL (dashed lines) when the same defense is in place across both frameworks. Therefore, our empirical evaluations show that existing defenses are more robust to backdoor attacks in Meta-FL compared to baseline FL across.

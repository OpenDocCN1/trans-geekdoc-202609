AutoML methods in the benchmark test, we added a decision tree and a constant predictor. Following Gijsbers et al. [31], we used Area Under the Receiver Operator Curve (AUROC) for scoring. All tests have been run on Amazon Web Services using m5.2xlarge machines (32 GB memory, 8 vCPUs (Intel Xeon Platinum 8000 series Skylake-SP processor with a sustained all core Turbo CPU clock speed of up to 3.1 GHz). The OS used is Amazon Linux (https://aws.amazon.com/ec2/instance-types/m5/) to get constant circumstances and enough computing power for the AutoML methods. In our research we only used the AutoML methods available in the benchmark set to create an even playing field. Hence, no industrial tools were considered in this research.

To understand the needs of domain experts we elicited requirements using semi-structured interviews. We selected semi-structured interviews as the best method for requirements elicitation for three reasons. First, semi-structured interviews are considered to be the most effective way for requirements elicitation [36]. Second, it is an accepted method for conducting qualitative research in healthcare [37]. Third, semi-structured interviews have the benefits of eliciting people’s own views and uncovering issues or concerns that have not been considered beforehand by the researcher [38]. For our interviews, we constructed an interview protocol following the guidelines for interview research [39]. The sample consisted of five domain experts who were active in the scientific department of a regional hospital in the Netherlands. The interviewees have decided to participate voluntarily and hold different roles and medical expertise within non-academic hospitals in the Netherlands. The interviewees are active in the research fields of cancer, orthopedy, and cardiology and participate in medical research, either full-time or part-time. The sample consists of three women and two men. We evaluated the capabilities of the AutoML methods to the requirements of the domain experts. Based on the requirements we created two artefacts and evaluated these with the interviewees. The first artefact had a graphical user-interface, the second artefact had a code-based interface. We used artificial summative evaluation as part of the framework for evaluating design science research [40]. We evaluated the artefacts on the user story categories from the previous research question. To be able to evaluate the artefact properties, we used refined hypotheses [41].

# 4. Results

This section describes the result of the benchmark test, the requirements evaluation and artefact evaluation.

# 4.1. Benchmark Test

The benchmark test was ran using a time budget of one hour with a total of 160 hours of computational time. Figure 3 contains the visualization of results; the datasets are on the X-axis, the Y-axis shows the AUROC score. A colored dot marks the score for an AutoML method on each of the ten folds. A Kruskal–Wallis H test indicated that there was a statistically significant difference in the distribution for the Breast (H = 11.36, p < 0.001), Diabetes (H = 18.64, p < 0.001), Liver (H = 17.93, p < 0.001), and Sick dataset (H = 27.87, p < 0.001) between the AutoML methods, see Table 1 for statistics.

Table 1. Statistics for Kruskall Wallis test.

| | Breast | Diabetes | Liver | Sick |
|---|---|---|---|---|
| H-statistic | 11.36 | 18.64 | 17.93 | 27.87 |
| P-value | 0.995 ** | 0.324 ** | 0.455 ** | 0.386 ** |

** p < 0.001.

What is noteworthy in Figure 3 is that on the Liver dataset, the decision tree and Hyperopt-Sklearn do not always outperform the constant predictor. On the Diabetes dataset, Hyperopt-Sklearn lags compared the three other methods, but performs better than the constant predictor and has a similar performance to the decision tree. On the Breast dataset, all AutoML methods have the maximum score in at least one fold. All methods perform well on the Breast set, given their median scores and distribution. The performance of the decision tree indicates that it is not a hard prediction problem. For the results on the Sick dataset, we see that TPOT and Auto-Sklearn outperform the other

any pre-processing steps based on the scikit-learn and the XGBoost library. Pipelines are built using a stacking mechanism based on an evolutionary algorithm and should generalize well to new data [27].

### 2.5. Distributed Methods

Two AutoML methods can process data in a distributed manner: Autostacker [27] and ATM [29]. It is remarkable, that there are only two systems that can run in a distributed manner, when taking the computing cost of creating a pipeline in mind. Autostacker can use parallel processing as it proposes the best pipelines to its user. Hence it needs the performance scores of the pipelines. ATM is the only method which can run in parallel on different machines and is set up to be distributed and scalable. ATM is developed to support a multi-user machine learning platform in a cloud or cluster. The aim is to provide standardized abstractions in a library to become as influential for the AutoML community with a library as scikit-learn is to the machine learning community [29]. The development of ATM and integration with the methods described above is one of the most attractive developments in AutoML. An incentive to spur this development could be having a separate performance challenge for distributed AutoML methods.

### 2.6. Overview of Methods

Figure 2 visualizes the relations between AutoML methods discussed in this section. It makes a distinction between methods that build NNs and methods that use traditional classifiers or regressors in their pipeline. Arrows between methods point out a relationship between methods. The colors of the methods indicate the search strategy that is applied in a method to create a pipeline. A tabular overview of the discussed AutoML methods is available in Appendix A, including the prediction tasks, a link to the code repository and more information about the pipeline creation.

![](img/87e48d9f4f7ed15b2cf1b43ac15a4529_3_0.png)

Figure 2. Overview of AutoML methods.

## 3. Research Method

We used the Design Science research framework [30] to answer the research questions. To do so, we first performed a benchmark test using the framework of Gijsbers and colleagues [31] on all available medical datasets from the OpenML100 [32] to find out if one AutoML method performed best on medical tasks. We ran medical binary-classification tasks on four datasets: Breast cancer [33], Diabetes [34], Indian Liver Patient [34], and Sick dataset [35]. All selected methods received a time budget of one hour in a 10-fold cross-validation set-up to create the best pipeline on the given datasets. The time limit is set on one hour, as longer runs do not significantly provide better results [31], a finding that was also confirmed during our experiments. To baseline the performance of the AutoML methods in the benchmark test, we added a decision tree and a constant predictor. Following Gijsbers et al. [31], we used Area Under the Receiver Operator Curve (AUROC) for scoring. All tests have been run on Amazon Web Services using m5.2xlarge machines (32 GB memory, 8 vCPUs) (Intel Xeon Platinum 8000 series Skylake-SP processor with a sustained all core Turbo CPU clock speed of up to 3.1 GHz). The OS used is Amazon Linux (https://aws.amazon.com/ec2/instance-types/m5/) to get constant circumstances and enough computing power for the AutoML methods. In our research we only used the AutoML methods available in the benchmark set to create an even playing field. Hence, no industrial tools were considered in this research.

To understand the needs of domain experts we elicited requirements using semi-structured interviews. We selected semi-structured interviews as the best method for requirements elicitation for three reasons. First, semi-structured interviews are considered to be the most effective way for requirements elicitation [36]. Second, it is an accepted method for conducting qualitative research in healthcare [37]. Third, semi-structured interviews have the benefits of eliciting people’s own views and uncovering issues or concerns that have not been considered beforehand by the researcher [38]. For our interviews, we constructed an interview protocol following the guidelines for interview research [39]. The sample consisted of five domain experts who were active in the scientific department of a regional hospital in the Netherlands. The interviewees have decided to participate voluntarily and hold different roles and medical expertise within non-academic hospitals in the Netherlands. The interviewees are active in the research fields of cancer, orthopedy, and cardiology and participate in medical research, either full-time or part-time. The sample consists of three women and two men. We evaluated the capabilities of the AutoML methods to the requirements of the domain experts. Based on the requirements we created two artefacts and evaluated these with the interviewees. The first artefact had a graphical user-interface, the second artefact had a code-based interface. We used artificial summative evaluation as part of the framework for evaluating design science research [40]. We evaluated the artefacts on the user story categories from the previous research question. To be able to evaluate the artefact properties, we used refined hypotheses [41].

## 4. Results

This section describes the result of the benchmark test, the requirements evaluation and artefact evaluation.

### 4.1. Benchmark Test

The benchmark test was ran using a time budget of one hour with a total of 160 hours of computational time. Figure 3 contains the visualization of results; the datasets are on the X-axis, the Y-axis shows the AUROC score. A colored dot marks the score for an AutoML method on each of the ten folds. A Kruskal–Wallis H test indicated that there was a statistically significant difference in the distribution for the Breast (H = 11.36, p < 0.001), Diabetes (H = 18.64, p < 0.001), Liver (H = 17.93, p < 0.001), and Sick dataset (H = 27.87, p < 0.001) between the AutoML methods, see Table 1 for statistics.

Table 1. Statistics for Kruskal Wallis test.

| | Breast | Diabetes | Liver | Sick |
|---|---|---|---|---|
| H-statistic | 11.36 | 18.64 | 17.93 | 27.87 |
| P-value | 0.995 ** | 0.324 ** | 0.455 ** | 0.386 ** |

** p < 0.001.

What is noteworthy in Figure 3 is that on the Liver dataset, the decision tree and Hyperopt-Sklearn do not always outperform the constant predictor. On the Diabetes dataset, Hyperopt-Sklearn lags compared the three other methods, but performs better than the constant predictor and has a similar performance to the decision tree. On the Breast dataset, all AutoML methods have the maximum score in at least one fold. All methods perform well on the Breast set, given their median scores and distribution. The performance of the decision tree indicates that it is not a hard prediction problem. For the results on the Sick dataset, we see that TPOT and Auto-Sklearn outperform the other

![](img/87e48d9f4f7ed15b2cf1b43ac15a4529_5_0.png)

Figure 3. One hour benchmark test results.

two methods in both consistency and score of their predictions despite the fact that the set has missing values. Hyperopt-Sklearn is again not better than the decision tree.

Overall, TPOT registered the highest median score after running for one-hour on all sets but the Breast dataset, in which autosklearn registered the best median performance. A Mann–Whitney U test indicated that autosklearn significantly outperforms the decision tree (U = 2.0, p < 0.001) and hyperoptsklearn (U = 17.5, p < 0.01) on the Breast set. TPOT significantly outperforms the decision tree on the datasets Diabetes (U = 0.0, p < 0.001), Liver (U = 8.0, p < 0.001) and Sick (U = 0.0, p < 0.001). Furthermore, TPOT outperforms hyperoptsklearn significantly on the datasets Diabetes (U = 2.0, p < 0.001), Liver (U = 7.0, p < 0.001) and Sick (U = 0.0, p < 0.001). Finally, AutoWEKA is significantly outperformed on the Sick dataset by TPOT (U = 0.0, p < 0.001). This is probably because AutoWEKA does not impute data for missing values. Autosklearn and TPOT do impute values for missing data and have significantly better results. The statistics for the Mann–Whitney U test are available in Table 2. The table shows the p-values and U statistics for each method compared to the best performing method on each dataset. TPOT and autosklearn do not significantly differ in performance for any of the datasets.

From the benchmark test we can conclude that no method consistently outperforms all others. However, we see that TPOT records the highest median scores on three of the four tasks in this test but this performance is not significantly better than the performance of other methods. Autosklearn and AutoWEKA get similar results to TPOT, only AutoWEKA is outperformed on the Sick dataset.

Table 2. P-values and U statistic for Mann–Whitney U test compared to best performer.

| | Breast | | Diabetes | | Liver | | Sick | |
|---|---|---|---|---|---|---|---|---|
| | p | U | p | U | p | U | p | U |
| DecisionTree | 0.164 ** | 2.0 | 0.908 ** | 0.0 | 0.895 ** | 8.0 | 0.913 ** | 0.0 |
| TPOT | 0.236 | 40.0 | | | | | | |
| AutoWEKA | 0.395 | 46.0 | 0.455 | 48.0 | 0.263 | 40.0 | 0.913 ** | 0.0 |
| Autosklearn | | | 0.425 | 47.0 | 0.213 | 39.0 | 0.5 | 49.5 |
| Hyperoptsklearn | 0.8 * | 17.5 | 0.164 ** | 2.0 | 0.657 ** | 7.0 | 0.913 ** | 0.0 |

* p < 0.01 ** p < 0.001.

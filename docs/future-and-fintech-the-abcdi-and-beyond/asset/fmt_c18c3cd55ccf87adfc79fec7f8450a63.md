
## 4.8 Appendix 4.1: Fairness Tools

There are many tools available in the markets, and many of them are open sourced. [Table 4.9](#chap4.xhtml#tab4-9) lists some relatively matured tools, mainly from Github.

### Table 4.9. Some open-source tools

| **Name** | **Functionality** | **Github** |
| --- | --- | --- |
| Fairness Measures | Framework to test given algorithm on variety of datasets and fairness metrics. | [https://github.com/megantosh/fairness\_measures\_code](https://github.com/megantosh/fairness_measures_code) |
| Fairness Comparison | Extensible test-bed to facilitate direct comparisons of algorithms with respect to fairness measures. Includes raw and pre-processed datasets. | [https://github.com/algofairness/fairness-comparison](https://github.com/algofairness/fairness-comparison) |
| Themis-ML | Python library built on scikit-learn that implements fairness-aware ML algorithms. | [https://github.com/cosmicBboy/themisml](https://github.com/cosmicBboy/themisml) |
| FairML | Looks at significance of model inputs to quantify prediction dependence on inputs | [https://github.com/adebayoj/fairml](https://github.com/adebayoj/fairml) |
| Aequitas | Web audit tool as well as Python library. Generates bias report for given model and dataset. | [https://github.com/dssg/aequitas](https://github.com/dssg/aequitas) |
| Fairtest | Tests for associations between algorithm outputs and protected populations. | [https://github.com/columbia/fairtest](https://github.com/columbia/fairtest) |
| Themis | Takes a black-box decision-making procedure and designs test cases automatically to explore where the procedure might be exhibiting group-based or causal discrimination. | [https://github.com/LASER-UMASS/Themis](https://github.com/LASER-UMASS/Themis) |
| Audit-AI | Python library built on top of scikit-learn with various statistical tests for classification and regression tasks. | [https://github.com/pymetrics/audit-ai](https://github.com/pymetrics/audit-ai) |
| AIF360 | Comprehensive bias metrics and mitigation toolbox (including unique algorithms from IBM Research). | [https://github.com/ibm/aif360](https://github.com/ibm/aif360) |
| Interpret ML | Fit interpretable models. Explain black-box machine learning. | [https://github.com/interpretml](https://github.com/interpretml) |
| fairlearn | Assess and improve fairness of machine learning model. | [https://fairlearn.github.io/](https://fairlearn.github.io/) |
| fairness indicators | Evaluating, improving, and comparing models for fairness concerns in partnership with the broader Tensor flow toolkit. | [https://github.com/tensorflow/fairness-indicators](https://github.com/tensorflow/fairness-indicators) |

## Checklist for AI System Assessment

### Data

*   Are there missing values for a large number of observations?
*   Are there missing features that might impact the output and/or affect other features?
*   Are there any unexpected feature values, which might be considered as outliers?
*   Is the training dataset sufficient for diversity and reliability? Is there only necessary data collected, e.g., respecting privacy and data rights?
*   Are there any understandable security methods for data?
*   Which datasets was the service trained and tested on? (Provide links to datasets that were used for testing, along with corresponding datasheets)
*   Was the dataset checked for bias used by the service? What types of statistical data skew observed?
*   What is the data lifecycle from data ingestion to the model serving?
*   What efforts were made to ensure that it is fairly representative?

### Model

*   Do we need new laws (not disparate impact/treatment) to address these systems?
*   Is automated decision making ethically different than human decision making?
*   Can there be unfair models for reasons other than group differences?
*   Should we study fairness *with* privacy, security, transparency…or not?
*   Is data or model the cause of bias in ML decisions? What are the potential worst scenarios of the model output?
*   What algorithms or techniques is this mode applied with?
*   Are testing methodology and test results clearly explained?
*   Are the service outcomes or model outputs explainable and/or interpretable?
*   Does the service have any mechanism for bias detection and remediation?
*   Does the service have any expectation or implement any mechanism to handle unseen data or data with different distributions?

### Deployment and Maintenance

*   Is the service robust enough against adversarial attacks?
*   How frequent is the model updated and when were the its last updated?
*   Is the updated automatically or manually (who is the approver)?
*   Is there any feedback on bias, ethical or other risks issues when using the service?
*   Are the straightforward and interpretable monitoring systems provided?
*   Is there a regular policy defined for model improvements to meet human needs and technical standards? Any model retain and model decommission policies?
*   Is the AI system robust, valid, and reliable?

### Governance

*   Do we identify the full range of risks (harmful, malicious use and consequences) and benefits (good, beneficial use and consequences)?
*   Is there any plan for the misuse/abuse of the AI system, including the communication plans to share pertinent information with all affected people, and the mitigation plans for managing the identified speculative risks?
*   Is there a proper pipeline to make sure that the data, algorithms and models are appropriate and verifiable? Are the overall procedures properly reviewed and approved?
*   Are confidence and context presented for humans to make proper decisions?
*   Is transparent justification for recommendations and outcomes provided?

## References

[1](#chap4.xhtml#ref1). T. Grote and B. Philipp, “On the ethics of algorithmic decision-making in healthcare,” *Journal of Medical Ethics,* Vol. 46, No. 3, November 2020.

[2](#chap4.xhtml#ref2). N. Arvind, “Tutorial: 21 fairness definition and their politics,” ACM FAT (Fairness, Accountability and Transparency) Conference, 2018.

[3](#chap4.xhtml#ref3). C. O’Neil, “Weapon of mass destruction,” Broadway Books, 2016.

[4](#chap4.xhtml#ref4). A. Ouaddah, A. A. Elkalam and A. A. Ouahman, “FairAccess: A new blockchain-based access control framework for the internet of things,” *Security and Communication Networks,* Vol. 18, No. 9, pp. 5,943–5,964, February 2017.

[5](#chap4.xhtml#ref5). A. Das and P. Rad, “Opportunities and Challenges in Explainable Artificial Intelligence (XAI): A Survey,” arXiv:2006.11371, 2020.

[6](#chap4.xhtml#ref6). J. Dodge, V. Q. Liao, Y. Zhang, R. K. Bellamy and C. Dugan, “Explaining models: An empirical study of how explanations impact fairness judgment,” in *ACM International Conference on Intelligent User Interfaces,* 2019.

[7](#chap4.xhtml#ref7). R. K. E. Bellamy *et al.,* “AI fairness 360: An extensible toolkit for detecting, understanding, and mitigating unwanted algorithmic bias,” [https://arxiv.org/abs/1810.01943](https://arxiv.org/abs/1810.01943), 2018.

[8](#chap4.xhtml#ref8). E. Wall, L. M. Blaha, L. Franklin and A. Endert, “Warning, bias may occur: A proposed approach to detecting cognitive,” in *IEEE Conference on Visual Analytics Science and Technology (VAST),* 2017.

[9](#chap4.xhtml#ref9). S. Moro, P. Cortez and P. Rita, “A data-driven approach to predict the success of bank telemarketing,” *Decision Support Systems,* Vol. 62, pp. 22–31, June, 2014.

[10](#chap4.xhtml#ref10). A. M. Ozbayoglu, M. U. Gudelek and O. B. Sezer, “Deep learning for financial applications: A survey,” *arXiv:2002.05786,* 2020.

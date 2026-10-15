
机器学习系统，尤其是深度学习模型，并非传统意义上的工程设计——它们是被优化的。这一区别正是其脆弱性的核心所在。这些模型并不遵循程序化逻辑，而是从数据中学习统计规律。因此，它们对世界的内部表征可能与人类直觉有着巨大差异。一个模型可能在评估时对数百万个示例进行准确分类，但在面对精心设计的、几乎不可察觉的微小改动时却会失败。这种表面表现与底层稳定性之间的差距并非实现缺陷，而是现代人工智能的结构性真理。[Table 1.1](#c01.xhtml#c01-tbl-0001) 将对抗性风险与人工智能系统生命周期的关键阶段进行映射，以展示防御措施应在何处及时、持续地应用。

[Table 1.1](#c01.xhtml#c01-tbl-0001) maps adversarial risks to key phases in the AI system lifecycle to illustrate where defenders must apply security controls early and continuously.

| Lifecycle Phase || Key Activities || Adversarial Exposure || Primary Risk Types |
| --- | --- | --- | --- |
| Data Collection || Acquiring Raw Input Data || Open to Contaminated or Biased Sources || Poisoning Embedding Backdoors |
| Preprocessing || Filtering Normalizing Labeling || Trust in Input Transformation Logic || Feature Injection Label Manipulation |
| Training || Model Fitting and Optimization || Model Internalization of Vulnerabilities || Backdoors Memorization Gradient Manipulation |
| Validation || Model Benchmarking and Tuning || Overfitting to Public Test Sets || Evasion Confidence Misuse Test Leakage |
| Deployment || Model Serving and API Exposure || Direct Input Access by Users || Evasion Prompt Injection Output Control |
| Operational Use || Live Environment Interaction || Dynamic Contexts and Real-Time Inputs || Cascading Failures Jailbreaking Emergent Behaviors |
| Monitoring and Updates || Logging Retuning Fine-Tuning || Adversarial Drift via Updates || Undetected Drift Inference Leakage |

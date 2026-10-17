
For continuous cases such as regression, bias metrics can be built around aggregate functions of errors produced by the model on different types of individuals (such as Mean Squared/Absolute (Percentage) Error, i.e., `MSE`, `MSPE`, `MAE`, `MAPE`), or by testing the distributional similarity of these errors across subgroups. The continuous outcomes produced by predictions add complexity to fairness definitions, requiring consideration of the magnitude of errors. For example, we need to choose between a model with large errors on minority groups versus one with relatively small errors on majority groups.

```
![](img/p126.jpg)
```

**Figure 4.6.** General points of fairness pipeline in ML lifecycle

**Table 4.1.** Fairness pipeline considerations

| **Stage** | **Fairness Considerations** |
| --- | --- |
| Design | * Task, scope, business domain, end users<br>* Stakeholders, product owners<br>* Potential errors and harms |
| Data | * Data provenance, ETC compliance<br>* Data representation, privacy, security<br>* Data validation procedures through qualitative and experimental surveys and other research<br>* Data EDA for historical/representation bias |
| Model | * Feature engineering and selection readiness for protected data and non-privileged classes<br>* Explainable mechanisms of the model<br>* Logic behind model decisions<br>* Supporting evidence, consistency between human and machine decisions<br>* Twyman's Law: The more unusual the result, the more likely it is to be wrong |
| Deployment | * Appropriate audit processes<br>* Ensure optimization and guardrail metrics align with responsible practices and harm prevention |
| Maintenance | * Identification and response as failures and harms occur<br>* Continuous monitoring, including feedback channels from end users<br>* Feedback loops for model adjustment |

**Table 4.2.** Key modeling points

| **Pre-modeling/processing (mainly for data)** | **In-modeling/processing (mainly for modeling)** | **Post-modeling/processing (mainly for deployment and maintenance)** |
| --- | --- | --- |
| Data quality (completeness, accuracy, etc.) | Model and feature selection | Performance and fairness testing and validation |
| Data bias | Model fairness metrics | Audit conditions |
| Data fairness metrics | Model explainability | Performance and fairness triggers |
| Protected features (privileged/non-privileged) | Model regularization for bias | Sensitivity analysis |
| Data preprocessing (fairness, augmentation, etc.) | Model mitigation (trade-offs) | Maintenance strategies |

```
![](img/p128.jpg)
```

**Figure 4.7.** Common fairness methods and metrics

Once bias is detected (e.g., fairness metrics do not meet certain standards), debiasing and risk mitigation procedures should be applied. For example, during model training, the trade-offs between business needs, model performance, and fairness must be carefully evaluated.

Human judgment within an appropriate framework is also a key factor in maintaining fair models, such as human expert decision systems, audit procedures, human-in-the-loop, etc.

### 4.4.1 Design

Product/project designers, managers, and owners should consider the impact of fairness on customers. Several general considerations are as follows [[3]](#chap4.xhtml#rref3):

*   **Harm:** Will it harm customers' lives or damage the company's reputation? Are price changes for products or services affordable for customers? Are products or services favored only by specific groups?
*   **Scale:** Will the financial product or service change the lives of large populations (e.g., credit scoring models)?
*   **Opacity:** Are the model's underlying assumptions clearly explained and validated? Is the model created in a black box? If the model's decision process is questionable and difficult to understand, fairness is likely to be an issue.

### 4.4.2 Data

Data bias manifests in various phenomena. Examples include:

*   Data from large-scale historical human decisions naturally carries societal biases, which models learn as unfairness.
*   Data is dirty and often simply wrong.
*   Large-scale data often encodes protected characteristics such as race, ability, health markers, etc.
*   Restricted options or menu-driven identity misidentification produces useless or dirty data.
*   There is no ground truth to validate our hypotheses against big data. For protected classes, big data is often not big data. Less data for protected classes means larger margins of error and worse predictions [[4]](#chap4.xhtml#rref4).

Sometimes, bias hides in available samples (observations). A famous example is the statistics of surviving bombers in WWII. When engineers tried to find vulnerable spots from bombers that survived the war, they did not include the engines, which was counterintuitive. This is because bombers with engine damage rarely returned safely. Therefore, observing only "survivor" data is inappropriate. Similarly, when models are built based on the mainstream population in financial institutions, there may be problems for minority groups. For example, when a local bank primarily serves locals, it may not handle loan applications from foreigners well. In this sense, in addition to considering known protected features as described in Section 4.3, we should also check for unknown protected features.

In fact, certain variables may implicitly act as protected variables. For example, demographic variables used for modeling are often available for statistical methods of bias. However, modelers instead use proxy variables that implicitly provide the same signals. Zip code is one such case; it may correlate with income and neighborhood; in turn indicating wealth and class, and even race in some places.

To systematically measure data bias, we can consider both statistical properties and certain distortions. In addition to the general privacy and security of data attributes (see Table 4.3), we should also consider factors listed in Table 4.4, such as biases in population, behavioral activity, content, association, and temporal events. More specifically, we can further categorize data bias into seven types, as shown in Table 4.5.

**Table 4.3.** Data privacy goals [[4]](#chap4.xhtml#rref4)

| **Goal** | **Explanation** |
| --- | --- |
| Transparency | Consensus on who can access, the meaning of data, how data will be used, with whom data is shared, how long it is held by users, etc. |
| User-driven | Users have full and fine-grained access control over their own data wherever it is shared. |
| Anonymity | User identity is not disclosed through IoT applications. |
| Pseudonymity | Trade-off between anonymity and accountability. In practice, an individual's actions are not linked to their identity but to a pseudonym (random identifier). Pseudonymity can be used for various purposes, including addressing privacy and accountability in financial institutions. |

### 4.4.3 模型

一旦数据偏差被移除或缓解，AI/ML 模型将被构建或训练以预测设计目标。图 4.8 说明了建模过程中的一般概念，其中左侧显示了用户参与公平性应用的常见步骤，右侧选择了循环中的一些常见规则及其问题和职责。由于模型可能是灰盒或黑盒，我们通常对模型应用 XAI 技术。

```
![](img/p132.jpg)
```

**图 4.8.** 模型公平性概念

#### 可解释 AI (XAI)

模型可解释性对于实现模型透明度、问责制和公平性至关重要。通常有两大类别 [[5]](#chap4.xhtml#rref5)：

*   **类别 1：设计并生成可解释的 AI 模型**，这通常是内在的。
    *   某些模型具有自我解释性，例如 `logistic regression`、`decision trees`、`decision lists and sets`、`generalized additive models (GAMs)`。
*   **类别 2：对 AI 模型的事后解释**，这与模型无关。
    *   **局部解释** 试图解释模型如何针对给定实例进行预测，涉及输入特征、有影响力的样本、局部特征重要性、局部决策规则等。
    *   **全局解释** 通常试图解释整个模型的整体问题，例如模型如何预测以及数据集如何影响决策。它通常可以应用诸如 `partial dependence plots`、`global feature importance`、`global decision rules` 等术语，从“平均”意义上进行解释。

通过提高模型的透明度和信任度，XAI 可用于改善对模型偏差和公平性的理解 [[5]](#chap4.xhtml#rref5)。例如，受保护特征的特征重要性直接说明了模型公平性，例如，如果受保护特征（如 `age` 和 `gender`）的重要性指数非常小，则意味着模型对受保护特征不敏感，因此通常是公平的。

#### 训练

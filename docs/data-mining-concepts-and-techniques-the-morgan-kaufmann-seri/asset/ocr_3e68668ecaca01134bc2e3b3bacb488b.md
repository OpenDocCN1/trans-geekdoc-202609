essentially correlation analysis and much less has been done on causality analysis. In general terms, correlation analysis is to study the statistical associations between different observed variables, whereas causal analysis focuses on the causality relation between them. We use the following example to illustrate the difference between these two kinds of analyses.

**Example 12.4.** Suppose the temperature is low in winter. Both the electric bill and food expense are very high. In this scenario, we have observed three variables, including low temperature, high electric bill, and high food expense. There exists a correlation between the high electric bill and the high food expense. However, it is not the high electric bill that has caused the high food expense and vice versa. The causality might instead lie in the low temperature for both the food expense and the electric bill.

Compared with correlation analysis, the challenges for causality analysis could be explained by its main tasks, including causality inference and causality discovery.

+   - *Causality discovery* is qualitative: analysis. For example, if we want to change the value of some specific variable(s), which variables should we manipulate?
+   - *Causality inference* is quantitative: analysis. For instance, if we modify some variable’s value, what kind of quantitative changes will happen to some specific variable(s)?

For causality discovery, it is more difficult than correlation analysis and may need some prior expert knowledge; as for causality inference, it needs well-designed complex experiments like A/B test, where other variables are kept same.

Causality analysis can be applied to different aspects of data mining models. For example, with a good causality discovery, the interpretability of black-box deep learning models will be enhanced. In some intelligent systems (e.g., university admission system), causality analysis can help avoid unfair results related to some sensitive variables (e.g., gender). In addition, causality analysis could improve the robustness of models.

The taxonomy of causality analysis is shown in Fig. 12.8. We divide existing methods according to their tasks. For causality discovery, traditional methods include constraint-based algorithms, score-based algorithms, and functional causal models. The Peter-Clark (PC) Algorithm tests the conditional

![](bbox=[0.17, 0.66, 0.8, 0.85])

**FIGURE 12.8**
The taxonomy of causality analysis. Adapted from Guo et al. [GCL+20].
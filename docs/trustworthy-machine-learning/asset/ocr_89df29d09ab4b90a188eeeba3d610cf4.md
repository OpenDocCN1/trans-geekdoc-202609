> “Most of this work is narrow in scope, focusing on fine-tuning specific models, making datasets more inclusive/representative, and ‘debiasing’ datasets. Although such work can constitute part of the remedy, a fundamentally equitable path must examine the wider picture, such as unquestioned or intuitive assumptions in datasets, current and historical injustices, and power asymmetries.”
> 
> —Abeba Birhane, cognitive scientist at University College Dublin

> “I continue to worry that in CS (as in psychology), debates about bias have become a powerful distraction—drawing attention away from what’s most important toward what’s more easily measurable.”
> 
> —J. Nathan Matias, behavioral scientist at Cornell University

The second issue is as follows. Have we too easily swept the important considerations of algorithmic fairness under the rug of mathematics? Yes and no. If you have truly thought through the different sources of inequity arising throughout the machine learning lifecycle utilizing a panel of diverse voices, then applying the quantitative metrics and mitigation algorithms is actually pretty straightforward. It is straightforward because of the hard work you’ve done before getting to the modeling phase of the lifecycle and you should feel confident in going forward. If you have not done the hard work earlier in the lifecycle (including problem specification), blindly applying bias mitigation algorithms might not reduce harms and can even exacerbate them. So don’t take shortcuts.

# 10.7 Summary

+   - Fairness has many forms, arising from different kinds of justice. Distributive justice is the most appropriate for allocation decisions made or supported by machine learning systems. It asks for some kind of sameness in the outcomes across individuals and groups.
+   - Unfairness can arise from problem misspecification (including inappropriate proxy labels), feature engineering, measurement of features from the construct space to the observed space, and sampling of data points from the observed space to the raw data space.
+   - There are two important worldviews in determining which kind of sameness is most appropriate for your problem.
+   - If you believe there are social biases in measurement (not only representation biases in sampling), then you have the “we’re all equal” worldview; independence and statistical parity difference are appropriate notions of group fairness.
+   - If you believe there are no social biases in measurement, only representation biases in sampling, then you have the “what you see is what you get” worldview; separation, sufficiency, average odds difference, and average predictive value difference are appropriate notions of group fairness.
+   - If the favorable label is assistive, separation and average odds difference are appropriate notions of group fairness. If the favorable label is non-punitive, sufficiency and average predictive value difference are appropriate notions of group fairness.
# ## 7.5 Conclusions

In this chapter, we learned what explainability means from the context of ML. We started with a discussion on the need for explainable models and then visited some of the main methods that can be applied and adopted to explain ML models. In general, explainability hopes to provide us with sufficient insights into the inner workings of ML models. We also covered a few examples to supplement to dig into the reasoning behind model predictions.

The opaque nature of ML, along with the limited knowledge of this front, could make it a bit difficult to trust and adopt ML. Realizing explainable models can help ease<sup>86</sup> engineers into ML. In lieu of the presented methods, engineers are also likely to require additional methods to explain their ML models. Such methods could be best suited for this task if they can be augmented with engineering principles or engineering reasoning.<sup>87</sup>

Keep in mind that methods of explainability can satisfy users to varying degrees. For example, two engineers may or may not be satisfied with the same level of explainability [25–27]. It is possible that there is a threshold or potentially a trade-off between an acceptable degree of explainability to the expected level of satisfaction an engineer may require depending on an engineer’s background, sophistication, and goals (i.e., need to comply with codal provisions or societal expectations, etc.).

# ### Definitions

+   - **Explainability** Entails relating the inner mechanisms of a model and their influence on the model’s prediction. Also, assume that a model is capable of summarizing or producing insights to their decisions.
+   - **Feature importance** The degree to which a ML model relies on a particular feature to arrive at correct predictions.
+   - **Interpretability** The science of understanding what a model did (or might have done).
+   - **Partial dependence** Depicts an individual feature’s marginal (average) effect on the response/target variable while holding other features constant.
+   - **Summary plot** A plot that summarizes information similar to that obtained from feature importance.

# ### Questions and Problems

+   - 7.1 What are the qualities of the traditional methods of investigation?
+   - 7.2 Contrast explainability and interpretability.
+   - 7.3 Discuss the main differences between model predictions and model explanations.
+   - 7.4 Write one paragraph to describe why explainable ML is important to your area of civil and environmental engineering. Supplement your write-up with a practical example.
+   - 7.5 Redo Example no. 1 in DataRobot.
+   - 7.6 Repeat Example no. 1 in Dataiku.
+   - 7.7 Build a regression model and a classifier in a programming language of your choice and compare your analysis to that provided in Example no. 1.
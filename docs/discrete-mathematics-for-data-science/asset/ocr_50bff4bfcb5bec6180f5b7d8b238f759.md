When data fields are not independent from one another, then their respective relationships with the dependent variable is less clear. In such cases, unless you isolate the true important factors, you may have to keep the redundant ones just to maintain the model's predictive efficacy, minimizing the model's error. This is not necessarily a severe problem, as noted by Neter and Wasserman in their classic text, *Applied Linear Statistical Models*:

> The fact that some or all predictor variables are correlated among themselves does not, in general, inhibit our ability to obtain a good fit nor does it tend to affect inferences about mean responses or predictions of new observations, provided these inferences are made within the region of observations.¹

While keeping redundant data fields may not directly harm our conclusions, using more data than necessary wastes computing resources. Furthermore, if data is not available to ensure that the number of fields do not exceed the number of records, then statistically sound analysis is jeopardized. Such complications and related complexities in isolating key attributes in highly dimensional data is known as *the curse of dimensionality.*²

If any of the following occur, we likely have excess data dimensions:

+   - Removing some variables reduces regression standard errors.
+   - Variable pairs generally show strong correlation.
# Detailed Prediction Model Flowchart

![](bbox=[0.18, 0.115, 0.89, 0.69])

Figure 1: Proposed framework.

Step 5: All continuous features are normalized using min-max scaling to [0, 1] to ensure equal weight across AI models:

```
$$x' = \frac{x - X_{min}}{X_{max} - X_{min}}$$
```

Step 6: One-hot encoding is used for categorical data such as gender and ethnicity. For example, male = [1,0] and female = [0,1].
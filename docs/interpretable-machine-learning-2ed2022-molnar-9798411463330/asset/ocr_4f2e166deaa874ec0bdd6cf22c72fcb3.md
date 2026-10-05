# 8.6 SHAP (SHAPley Additive EXPlanations)

Coalitions of $h_i(z) \rightarrow$ Image

Instance x

![](bbox=[0.368, 0.195, 0.465, 0.315])

Instance x with absent features

![](bbox=[0.368, 0.32, 0.465, 0.44])

Figure 8.23: Function $h_i$ maps coalitions of superpixels (sp) to images. Superpixels are groups of pixels. For present features (1), $h_i$ returns the corresponding part of the original image. For absent features (0), $h_i$ greys out the corresponding area. Assigning the average color of surrounding pixels or similar would also be an option.

We can be a bit smarter about the sampling of coalitions: The smallest and largest coalitions take up most of the weight. We get better Shapley value estimates by using some of the sampling budget K to include these high-weight coalitions instead of sampling blindly. We start with all coalitions 1 and M-1 features, which make 2 times M coalitions in total. When we have enough budget left (current budget is K-2M), we can include coalitions with 2 features and M-2 features and so on. From the remaining coalition sizes, we use readjusted weights.

We have the data, the target and the weights; Everything we need to build our weighted linear regression model:

```
$g(z') = \phi_0 + \sum_{j=1}^{M} \phi_j z'_j$
```

We train the linear model g by optimizing the following loss function L:
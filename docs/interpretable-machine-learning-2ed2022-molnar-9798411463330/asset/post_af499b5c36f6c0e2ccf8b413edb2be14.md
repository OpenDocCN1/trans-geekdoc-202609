
# CHAPTER 8 LOCAL MODEL-AGNOSTIC METHODS

![](img/9c9dbc65e26f4c97aa064cc82205fc4c_243_0.png)

Figure 8.24: SHAP values to explain the predicted cancer probabilities of two individuals. The baseline – the average predicted probability – is 0.06. The first woman has a low predicted risk of 0.06. Risk increasing effects such as SHAPs are offset by decreasing effects such as age. The second woman has a high predicted risk of 0.71. Age of 51 and 34 years of smoking increase her predicted cancer risk.

## 8.6.5 SHAP Feature Importance

The idea behind feature importance is simple: Features with large absolute Shapley values are important. Since we want the global importance, we average the absolute Shapley values per feature across the data:

```
I_j = \frac{1}{n} \sum_{i=1}^{n} |\phi_j^{(i)}|
```

We, sort the features by decreasing importance and plot them. The following figure shows the SHAP feature importance for the random forest before predicting cervical cancer.

SHAP feature importance is an alternative to permutation feature importance. There is a big difference between both measures: Permutation feature importance is based on the difference in model performance. SHAP is based on magnitude of feature attributes.

The feature importance plot is useful, but contains no information beyond the importances. For a more informative plot, we will next look at the summary plot.

## 8.6 SHAP (SHAPLEY Additive EXPlanations)

![](img/9c9dbc65e26f4c97aa064cc82205fc4c_244_0.png)

Figure 8.25: SHAP feature importance measured as the mean Shapley Values. The number of years with hormonal contraceptives was the most important feature, changing the predicted absolute cancer probability on average by 2.4 percentage points (0.024 on x-axis).

## 8.6.6 Summary Plot

The summary plot combines feature importance with feature effects. Each point on the summary plot is a Shapley value for a feature and an instance. The position on the y-axis is determined by the feature and on the x-axis by the Shapley value. The color represents the value of the feature from low to high. Overlapping points are jittered in y-axis direction, so we get a sense of distribution of the Shapley values per feature. The features are ordered according to their importance.

In the summary plot, we see first indications of the relationship between the value of a feature and the impact on the prediction. But to see the exact form of the relationship, we have to look at SHAP dependency plots.

## 8.6.7 SHAP Dependence Plot

SHAP feature dependence might be the simplest global interpretation plot: 1) Pick a feature. 2) For each data instance, plot a point with the feature value on the x-axis and the corresponding Shapley value on the y-axis. 3) Done.

Mathematically, the plot contains the following points: $\{(x_j^{(i)}, \phi_j^{(i)})\}_{i=1}^n$

# CHAPTER 8 LOCAL MODEL-AGNOSTIC METHODS

![](img/9c9dbc65e26f4c97aa064cc82205fc4c_245_0.png)

Figure 8.26: SHAP summary plot. Low number of years on hormonal contraceptives reduce the predicted cancer risk, a larger number of years increases the risk. Your regular reminder: All describes the behavior of the model and are not necessarily causal in the real world.

The following figure shows the SHAP feature dependence for years on hormonal contraceptives:

SHAP dependence plots are an alternative to partial dependence plots and accumulated local effects. While PDP and ALE plot show average effects, SHAP dependence also shows the variance on the y-axis. In case of interactions, the SHAP dependence plot will be much more dispersed in the y-axis. The dependence plot can be improved by highlighting these feature interactions.

## 8.6.8 SHAP Interaction Values

The interaction effect is the additional combined feature effect after accounting for the individual feature effects. The Shapley interaction index from game theory is defined as:

```
$$\phi_{i,J} = \sum_{S \subseteq {i,J}} \frac{|S|!(M - |S| - 2)!}{2(M - 1)!} \delta_{ij}(S)
```

when $i \neq j$ and:

# 8.6 SHAP (SHAPley Additive EXPlanations)

![](img/9c9dbc65e26f4c97aa064cc82205fc4c_246_0.png)

Figure 8.27: SHAP dependence plot for years on hormonal contraceptives. Compared to 0 years, a few years lower the predicted probability and a high number of years increases the predicted cancer probability.

> $$\delta_{ij}(S) = \hat{f}_x(S \cup \{i, j\}) - \hat{f}_x(S \cup \{i\}) - \hat{f}_x(S \cup \{j\}) + \hat{f}_x(S)$$

This formula subtracts the main effect of the features so that we get the pure interaction effect accounting for the individual effects. We average the values over all possible feature coalitions S, as in the Shapley value computation. When we compute SHAP interaction values for features, we get one matrix per instance with dimensions M x M, where M is the number of features.

How can we use the interaction index? For example, to automatically color the SHAP feature dependence plot with the strongest interaction:

## 8.6.9 Clustering Shapley Values

You can cluster your data with the help of Shapley values. The goal of clustering is to find groups of similar instances. Normally, clustering is based on features. Features are often on different scales. For example, height might be measured in meters, color intensity from 0 to 

# CHAPTER 8 LOCAL MODEL-AGNOSTIC METHODS

![](img/9c9dbc65e26f4c97aa064cc82205fc4c_247_0.png)

Figure 8.28: SHAP feature dependence plot with interaction visualization. Years on hormonal contraceptives interacts with STDs. In cases close to 0 years, the occurrence of a STD increases the predicted risk. For more years on contraceptives, the occurrence of a STD reduces the predicted risk. Again, this is not a causal model. Effects might be due to confounding (e.g. STDs and lower cancer risk could be correlated).

100 and some output between -1 and 1. The difficulty is to compute distances between instances.

## 8.6.10 Advantages

Since SHAP computes Shapley values, all the advantages of Shapley values apply: SHAP has a solid theoretical foundation in game theory. The prediction is fairly distributed among the feature values. We get contrastive explanations that compare the prediction with the average.

# 8.6 SHAP (SHAPley Additive EXPlanations)

![](img/9c9dbc65e26f4c97aa064cc82205fc4c_248_0.png)

8.29: Stacked SHAP explanations clustered by explanation similarity. Each position on the x-axis is an instance of the data. Red SHAP values increase the prediction, blue values decrease it. One cluster stands out: On the right is a group with high predicted cancer risk.

SHAP connects LIME and Shapley values. This is very useful to understand both methods. It also helps to unify the field of interpretable machine learning.

SHAP has a fast implementation for tree-based models. I believe this was key to the popularity of SHAP, because the biggest barrier for adoption of Shapley values is the slow computation.

The fast computation makes it possible to compute the many Shapley values needed for the global model interpretations. The global interpretation methods include feature importance, feature dependence, interactions, clustering and summary plots. With SHAP, global interpretations are consistent with the local explanations, and Shapley values are the “atomic unit” of the global interpretations. If you use LIME for local explanations and partial dependence plus permutation feature importance for global explanations, you will lack a common foundation.

## 8.6.11 Disadvantages

KernelSHAP is slow. This makes KernelSHAP impractical to use when you want to compute Shapley values for many instances. Also all global SHAP methods such as SHAP feature importance require computing Shapley values for a lot of instances.

KernelSHAP ignores feature dependence. Most other permutation based interpretation methods have this problem. By replacing feature values with random instances, it is easily to randomly sample from the marginal distribution. However, if features are dependent, e., correlated, this leads to putting too much weight on unlikely data points. TreeSHAP solves this problem by explicitly modeling the conditional expected prediction.

TreeSHAP can produce unintuitive feature attributes. While TreeSHAP solves the problem of extrapolating to unlikely data points, it does so by changing the value function and therefore slightly changes the game. TreeSHAP changes the value function by relying on

Association with the feature value—The color of the violin plot can help you associate blue areas, where the feature has lower values, and red areas, where the feature has higher values, with specific SHAP contributions. This helps in understanding how the feature is generally related to the outcome.

Outliers Outliers or extreme SHAP values outside the range where the corresponding feature has an unusually strong effect on the prediction.

In the following listing, the violin plot provides useful insights into the distribution and the role of each feature on the model's predictions.

# Listing 7.21 SHAP violin plot

```
shap.summary_plot(shap_values[:,,-1], Xtest,
plot_type='violin',
feature_names=feature_names,
show=False)
plt.yticks(figsize=8)
plt.show()
```

Figure 7.17 shows the resulting violin plot. As for our top important features, we observe out the following:

+   * Numeric_availability_365—Higher availability corresponds to a positive effect on price. Listings with lower availability are usually penalized.

+   * Target_encoding_coordinates—It is difficult to interpret its values are unrelated to a specific direction. We observe that there long tails on both sides with a negative contribution to the pricing of the accommodation.

+   * Numeric_number_of_bedrooms—A higher number of bedrooms implies a higher price, with a skewed tail to the right.

+   * Numeric_number_of_beds—Similarly, a higher number of beds implies a higher price, with a skewed tail to the right.

A glance at other features provides an idea of how the model behaves intuitively. For instance, the the accommodation is not the Imperial Palace or the airports, the higher price.

This concludes our end-to-end example using gradient boosting. In the next chapter, we are going to get back to the Airbnb NYC project and review a set of deep learning stacks (low-level framework, high-level API, and deep learning for tabular data) using these three stacks (fastai, PyTorch with TabNet, and Lightning Flash) to solve it and consider the different solutions.

In this phase, a generative AI tool as ChatGPT could be useful for creating narratives explaining the SHAP values assigned to each example. Being able to create an explanation for each prediction could prove a strong point when demonstrating the potentials of your model or trying to persuade clients and stakeholders.
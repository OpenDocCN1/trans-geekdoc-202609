FIGURE 5.38: The anchors algorithm  s components and their interrelations (simplified)

The approach is a seemingly perfect recipe for efficiently deriving statistically sound information about why any system classified an instance the way it did. It systematically experiments with the model’s input and concludes by observing respective outputs. It relies on well established and researched Machine Learning methods (MABs) to reduce the number of calls made to the model. This, in turn, drastically reduces the algorithm’s runtime.

# ## 5.8.2 Complexity and Runtime

Knowing the anchors approach’s asymptotic runtime behavior helps to evaluate how well it is expected to perform on specific problems. Let \ (B) denote the beam width and \ (p) the number of all features. Then the anchors algorithm is subject to:

```
[\mathcal{O}(O)(B\cdots} {\dots}p^2+p^2\cdots)]
```

This boundary abstracts from problem-independent hyperparameters, such as the statistical confidence \ (\delta). Ignoring hyperparameters helps reduce the boundary’s complexity (see original paper for more info). Since the MAB extracts the \ (B) best out of \ (B \cdot p) candidates in each round, most MABs and their runtimes multiply the \ (p^2) factor more than any other parameter.

It thus becomes apparent: the algorithm’s efficiency decreases with feature abundant problems.

# ## 5.8.3 Tabular Data Example

Tabular data is structured data represented by tables, wherein columns embody features and rows instances. For instance, we use the bike rental data to demonstrate the anchors approach’s potential to explain ML predictions for selected instances. For this, we turn the regression into a classification problem and train a random forest as our black-box model. It is to classify whether the number of rented bicycles lies above or below the trend line.

Before creating anchor explanations, one needs to define a perturbation function. An easy way to do so is to use an intuitive default perturbation space for tabular explanation cases which can be built by sampling from, e.g., the training data. When perturbing an instance, this default approach maintains the features’ values that are subject to the anchors’ predicates, while replacing the non-fixed features with values taken from another randomly sampled instance with a specified probability. This process yields new instances that are similar to the explained one but have adopted some values from other random instances. Thus, they resemble neighbors.
**Table 6.1** Search space (grid) of the RF runoff models.

| Hyperparameter | Domain |
|---|---|
| n_trees* | 40;800;10* |
| max_features | n_features, n_features^(1/2), log₂ (n_features) |
| max_depth* | 40;800;10* |

\*Domain defined by min, max, and increment.

+   2. Optimally splitting of the data selected in step 1 at each node of each tree. This is done by determining a maximum number of features to perform the best split from the total number of predictors in the feature space. This also avoids overfitting by assuring variety and the nonexistence of duplicated models.

+   3. Growth of all the trees constructed in step 1 with the splits defined in step 2 up to a size defined either by a maximum depth parameter or a minimum number of samples expected in the final node. Control of the depth of the trees aims to reduce the structural complexity of the models, leading to model parsimony and noise reduction.

+   4. Determination of the output of the model as the mean response from all regression trees.

According to Contreras et al. (2021), the most-influencing RF hyperparameters for hydrological forecasting applications are the number of trees in the forest (n_trees), the maximum number of features to perform the splits of the data (max_features), and the maximum depth for pruning purposes (max_depth). For all runoff models, we determined the optimal combinations of hyperparameters following a random grid-search procedure implemented with a 10-fold cross-validation process to prevent overfitting. The measure of agreement was evaluated according to the coefficient of determination (R²) between simulations and observations for the training subsets. Table 6.1 presents the domain of the selected hyperparameters, which forms the search space for the optimization task.

# *Model Evaluation*

We used four goodness-of-fit metrics for evaluating the efficiencies of the four runoff models. The Nash-Sutcliffe Efficiency (NSE) coefficient was set as the reference for measuring and comparing the overall model accuracy. To complement the analysis, we relied on the Kling-Gupta Efficiency (KGE), the Percent Bias (PBIAS), and the Root Mean Square Error
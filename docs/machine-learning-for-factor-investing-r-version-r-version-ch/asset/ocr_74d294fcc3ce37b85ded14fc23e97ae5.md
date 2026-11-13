and it is often rescaled so that the sum of $I(k)$ across all $k$ is equal to one. In this case, $I(k)$ measures the relative contribution of feature $k$ in the reduction of loss during the training. A variable with high importance will have a greater impact on predictions. Generally, these variables are those that are located close to the root of the tree.

Below, we take a look at the results obtained from the tree-based models trained in Chapter 6. We start by recycling the output from the three regression models we used. Notice that each fitted output has its own structure and importance vectors have different names.

```
tree_VI <- fit_tree$variable.importance %>%    # VI from tree model
  as_tibble(rownames = NA) %>%    # Transform in tibble
  rownames_to_column("Feature")    # Add feature column
RF_VI <- fit_RF$importance %>%    # VI from random forest
  as_tibble(rownames = NA) %>%    # Transform in tibble
  rownames_to_column("Feature")    # Add feature column
XGB_VI <- xgb.importance(model = fit_xgb)[,1:2]    # VI from boosted trees
VI_trees <- tree_VI %>% left_join(RF_VI) %>% left_join(XGB_VI)    # Aggregate the VIs
colnames(VI_trees)[2:4] <- c("Tree", "RF", "XGB")    # New column names
norm_1 <- function(x)(return(x / sum(x)))    # Normalizing function
VI_trees %>% na.omit %>% mutate_if(is.numeric, norm_1) %>%    # Plotting sequence
  gather(key = model, value = value, -Feature) %>%
  ggplot(aes(x = Feature, y = value, fill = model)) + geom_col(position = "dodge") +
  theme(axis.text.x = element_text(angle = 35, hjust = 1))
```

![](bbox=[0.22, 0.41, 0.72, 0.68])

# Feature

# FIGURE 13.2: Variable importance for tree-based models.

In the above code, tibbles are like dataframes (they are the v2.0 of dataframes, so to speak). Given the way the graph is coded, Figure 13.2 is in fact misleading. Indeed, by construction, the simple tree model only has a small number of features with nonzero importance: in the above graph, there are only 3: capitalization, price-to-book and volatility. In contrast, because random forest and boosted trees are much more complex, they give some importance to many predictors. The graph shows the variables related to the simple tree model only. For scale reasons, the normalization is performed *after* the subset of features is chosen.
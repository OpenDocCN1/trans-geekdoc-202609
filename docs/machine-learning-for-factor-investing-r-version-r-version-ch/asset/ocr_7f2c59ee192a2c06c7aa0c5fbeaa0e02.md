```
# grid_par(train_matrix_xgb, xgb_test, testing_sample$RIM_Usd, 0.1, 3, 0.1) # Possible test
grd <- pmap(list(eta, nrounds, lambda),
            # Parameters for the grid search
            grid_par,
            # Function on which to apply the search
            train_matrix = train_matrix_xgb,
            # Input for function: training data
            test_features = xgb_test,
            # Input for function: test features
            test_label = testing_sample$RIM_Usd
            # Input for function: test labels (returns)
)
grd <- data.frame(eta, nrounds, lambda, error = unlist(grd)) # Dataframe with all results
```

Once the squared mean errors have been gathered, it is possible to plot them. We chose to work with 3 parameters on purpose because their influence can be simultaneously plotted on one graph.

```
grid$eta <- as.factor(eta) # Params as categories (for plot)
grd %>% ggplot(aes(x = eta, y = error, fill = eta)) + # Plot!
    geom_bar(stat = "identity") +
    facet_grid(rows = vars(nrounds), cols = vars(lambda)) +
    theme(axis.text.x = element_text(size = 6))
```

![](bbox=[0.1, 0.36, 0.905, 0.68])

**FIGURE 10.9:** Plot of error metrics (SMEs) for many parameter values. Each row of graph corresponds to nrounds and each column to lambda.

In Figure 10.9, the main information is that a small learning rate (\(\eta = 0.1\)) is detrimental to the quality of the forecasts when the number of trees is small (nrounds=10), which means that the algorithm does not learn enough.

Grid search can be performed in two stages: the first stage helps locate the zones that are of interest (with the lowest loss/objective values) and then zoom in on these zones with refined values for the parameter on the grid. With the results above, this would mean considering many learners (more than 50, possibly more than 100), and avoiding large learning rates such as \(\eta = 0.9\) or \(\eta = 0.8\).
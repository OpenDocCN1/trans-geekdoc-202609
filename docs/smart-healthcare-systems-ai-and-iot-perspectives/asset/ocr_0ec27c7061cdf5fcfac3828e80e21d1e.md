# Smart Healthcare Systems

TABLE 15.3
Contrasting the Suggested Algorithm's Performance Metrics with Those of Benchmark Algorithms

| | LR | DT Classifier | SVC | GBC | Stacking |
|---|---|---|---|---||}{
| Accuracy | 0.78260 | 0.71739 | 0.58695 | 0.73913 | 0.82608 |
| Precision | 0.78571 | 0.72413 | 0.60606 | 0.73333 | 0.8 |
| Recall | 0.84615 | 0.80769 | 0.76923 | 0.84615 | 0.92307 |
| R² Score | 0.11538 | -0.15000 | -0.68076 | -0.06153 | 0.29230 |
| F1 Score | 0.81481 | 0.76363 | 0.67796 | 0.78571 | 0.85714 |

![](bbox=[0.196, 0.353, 0.803, 0.642])

FIGURE 15.4 Precision-Recall curves over the considered dataset for proposed stacking algorithm compared with benchmark ML models.

captured. It is well known that stacking may combine the best features of several models; in this case, it is seems to take advantage of the complimentary features of each model to produce better prediction performance. An important factor in a medical setting is the ability to properly identify people with heart disease, and the stacking model shows a considerable increase in memory in this regard. The combined model appears to explore more of the variation in the data, as indicated by the R² score for stacking, which shows a significant improvement above the separate models. Even if stacking produces encouraging results, it's crucial to evaluate the model on more datasets and take overfitting into account. The efficacy of the stacking ensemble greatly relays on the models selected and their hyperparameters. Precision-Recall curves over the considered dataset for proposed stacking algorithm compared with
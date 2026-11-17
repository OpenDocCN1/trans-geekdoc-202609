![](bbox=[0.13, 0.09, 0.87, 0.47])

Figure 9.5 – Jupyter Notebook kernel selection

+   13. From the notebook, navigate to **Kernel > Restart & Clear Output**. Click on the play icon to run the cells one after another. Please ensure you have run each individual cell and inspect the output from each execution/run.

+   14. You can experiment by adding cells and deleting cells to familiarize yourself with the Jupyter Notebook operations. In one of the paragraphs, there is a bash command that allows you to install the **xgboost** libraries from the notebook.

+   15. The final cell explains how you have compared the different scores of various modeling techniques to draw a conclusion mathematically. _Figure 9.6_ clearly shows that the best model for predicting house prices in Boston is XGBoost:

```
```python
models = pd.DataFrame({
    'Model': ['Linear Regression', 'Random Forest', 'XGBoost', 'Support Vector Machines'],
    'R-squared Score': [acc_linreg*100, acc_rf*100, acc_xgb*100, acc_svm*100],
    'Adjusted R-squared Score': [adj_R2_linreg*100, adj_R2_rf*100, adj_R2_xgb*100, adj_R2_svm*100],
    'MAE': [mae_linreg, mae_rf, mae_xgb, mae_svm],
    'MSE': [mse_linreg, mse_rf, mse_xgb, mse_svm],
    'RMSE': [rmse_linreg, rmse_rf, rmse_xgb, rmse_svm]})
models.sort_values(by='R-squared Score', ascending=False)
```
```

| | Model | R-squared Score | Adjusted R-squared Score | MAE | MSE | RMSE |
|---|---|---|---|---|---|---|
| 2 | XGBoost | 85.799520 | 84.461793 | 2.530958 | 14.828152 | 3.850734 |
| 1 | Random Forest | 82.181317 | 80.502745 | 2.500316 | 18.606282 | 4.313500 |
| 0 | Linear Regression | 71.218184 | 68.506853 | 3.859006 | 30.053993 | 5.482152 |
| 3 | Support Vector Machines | 59.001585 | 55.139415 | 3.756145 | 42.810575 | 6.542979 |

Figure 9.6 – Comparing the models
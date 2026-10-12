
### 4. Add a `Neural Net` node to the stream, connect it to the `Partition` node, and name it `MLP 5`. Use the same configurations as in `MLP 3`.

#### RBF 1

1.  Add a `Neural Net` node to the stream, connect it to the `Partition` node, and name it `RBF 1`. Open the node settings.

2.  **Basics**
    *   Neural network model: `Radial Basis Function (RBF)`.
    *   Hidden layers: Select `Automatically compute number of units`.

3.  **Advanced**: Select `Impute missing values`.

#### RBF 2

1.  Add a `Neural Net` node to the stream, connect it to the `Partition` node, and name it `RBF 2`. Open the node settings.

2.  **Basics**
    *   Neural network model: `Radial Basis Function (RBF)`.
    *   Hidden layers: Select `Custom number of units`; set `Hidden layer 1` to 15.

3.  **Advanced**: Select `Impute missing values`.

#### RBF 3

1.  Add a `Neural Net` node to the stream, connect it to the `Partition` node, and name it `RBF 3`. Open the node settings.

2.  **Basics**
    *   Neural network model: `Radial Basis Function (RBF)`.
    *   Hidden layers: Select `Custom number of units`; set `Hidden layer 1` to 30.

3.  **Advanced**: Select `Impute missing values`.

#### RBF 4

1.  Continue with the `Auto Data Prep` node created for `MLP 5`.
2.  Add a `Type` node to the stream and connect it to the `Auto Data Prep` node.
3.  Add a `Partition` node to the stream and connect it to the `Type` node. Select `Train, test, and validation` and set the partition size to 60–20–20.
4.  Add a `Neural Net` node to the stream, connect it to the `Partition` node, and name it `RBF 4`. Use the same configurations as `RBF 3`.

Run each model separately to generate the corresponding model nugget. Once you have all nine model nuggets, use separate Analysis nodes to obtain the model metrics. You can also attempt model comparison to evaluate the models’ performances. However, since `MLP 5` and `RBF 4` use transformed data, they cannot be compared with the other models. This is because SPSS Modeler requires that all models have the same input with identical field names for model comparison.

In this example, we will compare seven models—`MLP 1`, `MLP 2`, `MLP 3`, `MLP 4`, `RBF 1`, `RBF 2`, and `RBF 3`—as they all have identical input fields. To perform the comparison, follow the approach described in [Chapter 7](#chapter7.xhtml), where the model nuggets are connected for comparison. As shown in the diagram, the `Filler` node is used to rename the models to your preferred names. The `Analysis` node is used to compare the performance of the models, while the `Evaluation Graph` node is used to produce ROC charts and Lift charts for all the models.

![](images/ufig9_23.jpg)

Below are the `Filler` node settings, where we modify the model names for clarity and consistency during the comparison process.

![](images/ufig9_24.jpg)

### Champion Model

We follow the standard result presentation process described in [Chapter 6](#chapter6.xhtml), using the testing sample results for comparison. Refer to [Chapters 7](#chapter7.xhtml) and [9](#chapter9.xhtml) for details on how to extract model fit metrics from the `Analysis` node and calculate other metrics using the confusion matrix. [Table 9.5](#chapter9.xhtml#tbl9_5) compares the model fit metrics for all nine neural network models, while [Figures 9.8](#chapter9.xhtml#fig9_8) and [9.9](#chapter9.xhtml#fig9_9) show the ROC comparison chart and Lift comparison chart, respectively.

**TABLE 9.5** Model Comparison Using the Testing Sample's Results [Return to text.⏎](#chapter9.xhtml#b9tbl9_5)

| Metrics | MLP 1 | MLP 2 | MLP 3 | MLP 4 | MLP 5 | RBF 1 | RBF 2 | RBF 3 | RBF 4 |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| ACC | 77.06% | 77.33% | 78.47% | 78.14% | 78.47% | 70.52% | 70.40% | 73.78% | 73.78% |
| MR | 22.94% | 22.67% | 21.53% | 21.86% | 21.53% | 29.48% | 29.60% | 26.22% | 26.22% |
| Sensitivity or TPR | 0.913 | 0.904 | 0.906 | 0.905 | 0.906 | 0.774 | 0.756 | 0.810 | 0.810 |
| Specificity or TNR | 0.612 | 0.627 | 0.649 | 0.643 | 0.649 | 0.629 | 0.646 | 0.657 | 0.657 |
| F1 | 0.808 | 0.808 | 0.816 | 0.814 | 0.816 | 0.735 | 0.729 | 0.765 | 0.765 |
| Gini | 0.664 | 0.673 | 0.695 | 0.687 | 0.695 | 0.534 | 0.540 | 0.599 | 0.599 |
| AUC (ROC index) | 0.832 | 0.837 | 0.848 | 0.844 | 0.848 | 0.767 | 0.770 | 0.799 | 0.799 |

![FIGURE 9.8 ROC comparison chart. Return to text.⏎](images/fig9_8.jpg)

**FIGURE 9.8** ROC comparison chart. [Return to text.⏎](#chapter9.xhtml#b9fig9_8)

![FIGURE 9.9 Lift comparison chart. Return to text.⏎](images/fig9_9.jpg)

**FIGURE 9.9** Lift comparison chart. [Return to text.⏎](#chapter9.xhtml#b9fig9_9)

Overall, we observe that `MLP 3` and `MLP 5` have the highest accuracy (ACC) and lowest misclassification rate (MR). Keep in mind that these two models use the same configurations for the `Neural Net` node, with the only difference being that `MLP 5` uses normalized data for continuous fields (via the `Auto Data Prep` node), while `MLP 3` uses the original data. Similarly, models `RBF 3` and `RBF 4` share identical model fit metrics, with the only difference being that `RBF 4` uses normalized data, while `RBF 3` uses non-transformed data.

From this, we can conclude that for this dataset, normalizing data does not improve neural network performance, regardless of whether the MLP or RBFN method is used. Additionally, models using MLP generally perform better than those using RBFN. Based on other model fit criteria, `MLP 3` and `MLP 5` show the best model fit, with the highest F1 score, Gini coefficient, and ROC index. Although `MLP 1` has the highest sensitivity, its low specificity results in a lower F1 score.

Regarding ROC charts, `MLP 3` and `MLP 4` have better ROC curves compared to other models, while `RBF 1` and `RBF 2` perform the worst (note that `MLP 5` and `RBF 4` are excluded from this comparison). As for Lift curves, `MLP 3` has the best Lift curve, while `RBF 1` has the worst.

Ultimately, the choice comes down to `MLP 3` and `MLP 5`. I would recommend `MLP 3`, as it uses the original data, avoiding data transformations, which makes result interpretation easier. Therefore, `MLP 3` is selected as the champion model.

### Reliability of the Champion Model

The next step is to evaluate the reliability of the champion model. We have identified `MLP 3` as the champion model. [Table 9.6](#chapter9.xhtml#tbl9_6) presents the model fit results across three samples: training, testing, and validation. The results are very consistent between these samples, with a difference of less than 1%. This indicates that `MLP 3` demonstrates satisfactory model reliability, with no evidence of overfitting.

**TABLE 9.6** Reliability Evaluation of the Champion Model—MLP 3 [Return to text.⏎](#chapter9.xhtml#b9tbl9_6)

| Metrics | Testing | Training | Validation |
| :--- | :---: | :---: | :---: |
| ACC | 78.47% | 78.66% | 78.71% |
| MR | 21.53% | 21.34% | 21.29% |
| Sensitivity or TPR | 0.906 | 0.907 | 0.906 |
| Specificity or TNR | 0.649 | 0.654 | 0.656 |
| F1 | 0.816 | 0.817 | 0.817 |
| Gini | 0.695 | 0.708 | 0.699 |
| AUC (ROC index) | 0.848 | 0.854 | 0.850 |

### Validity of the Champion Model

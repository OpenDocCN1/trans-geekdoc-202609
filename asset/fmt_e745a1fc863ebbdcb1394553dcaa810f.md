
The forest attains a lower out-of-bag or validation error only by variance reduction. Therefore, increasing the number of trees in the ensemble will not have any effect on the bias of your model. A higher number of trees will reduce only the variance of your model. You can achieve a higher variance reduction by reducing the correlation between trees in the ensemble. Note that the convergence rate of forest not only depends on the data set's characteristics but also on other hyperparameters that are discussed ahead.

Parameter tuning of number of trees in forest is summarized in `Figure 6.23`.

### Figure 6.23: Tuning Number of Trees

```
![image](img/f0212-01.jpg)
```

### In-Bag Sample Proportion

Decreasing the in-bag sample proportion leads to more diverse trees and thereby lower correlation between the trees, which has a positive effect on the prediction accuracy when aggregating the trees. However, the accuracy of the single trees decreases, because fewer observations are used for training. Therefore, the choice of the in-bag sample proportion is a trade-off between stability and accuracy of the trees. The optimal value is problem dependent and can be estimated with the out-of-bag predictions. It is generally observed that setting it to lower values gives better results and reduces the runtime (MARTINI-Uriarte and Suarez 2010).

- Parameter tuning of in-bag sample proportion is summarized in `Figure 6.24`.

### Number of Inputs to Consider per Split

The number of inputs to consider per split is one of the most important tuning parameters in a forest. Smaller values produce more diverse, less correlated trees, and aggregating these diverse trees yields a more stable model. A smaller number of inputs also favors the utilization of inputs with moderate effects on the target, rather than being masked by inputs with strong effects. However, a smaller number of inputs also leads to worse performance of individual trees, because they are built based on a randomly drawn subset of candidate variables (which might be non-important variables): non-important variables might be selected. You must trade off stability and accuracy of individual trees (`Probst et al. 2019`).

### Figure 6.24: Tuning In-Bag Sample Proportion

```
![image](img/f0212-02.jpg)
```

The optimal number of inputs is heavily influenced by the number of actually relevant input variables. If there are many relevant predictors, the number of inputs should be set small, so that not only the most influential variables are selected for splitting, but also variables with smaller but still meaningful effects, yielding a small but significant performance gain. Conversely, if there are few relevant variables, the number of inputs should be set large, so that the algorithm can find these relevant variables (`Goldstein et al. 2011`).

Computation time is approximately inversely proportional to the number of inputs (`Wright and Ziegler 2017`), because the majority of the forest's computation time is spent selecting splitting variables.

- In-bag sample proportion tuning within trees is in `Figure 6.25`.

### Minimum Leaf Node Size (Count or Proportion)

The minimum leaf node size tuning parameter specifies the minimum number of observations in a terminal node. Setting it to a smaller value leads to deeper trees, i.e., more splits before terminal nodes. If there are many noise variables in the data, a higher minimum leaf node size is needed (`Segal 2004`).

### Figure 6.25: Tuning Number of Inputs

```
![image](img/f0213-01.jpg)
```

The effect of the minimum leaf node size is quite interesting. If trees are allowed to split until leaves contain single observations, this usually yields the most accurate random forest model. But smaller leaves mean larger (deeper) trees, and accuracy comes at the cost of computation time and memory. Smaller leaves also tend to make the model more prone to capturing noise in the training data.

Computation time decreases approximately exponentially with increasing minimum leaf node size (`Probst et al. 2019`). In large sample datasets, setting this parameter to a value larger than the default might be helpful, as it significantly reduces runtime while usually not harming predictive performance much (`Segal 2004`).

Note that besides the minimum leaf node size, other hyperparameters can also be used to control tree size (for example, a closely related hyperparameter is the maximum depth of the tree, i.e., the maximum number of splits until a terminal node).

- Minimum leaf node size tuning within trees is in `Figure 6.26`.

### Maximum Depth

Deeper trees have more splits and can capture more information about the data. But they can also lead to overfitting of individual trees. If a smaller minimum leaf node size is chosen, a larger maximum depth is recommended to allow trees to grow deeper; and vice versa. Lower tree depth might even fail to identify useful signals in the data. Deeper trees usually take longer to run.

- Maximum depth tuning within trees is in `Figure 6.27`.

### Figure 6.26: Tuning Minimum Leaf Node Size (Count or Proportion)

```
![image](img/f0214-01.jpg)
```

### Figure 6.27: Tuning Maximum Depth

```
```
![image](img/f0215-01.jpg)
```
```

### Automatic Hyperparameter Tuning

Automatic tuning specifies whether to automatically tune any parameters of the forest. You can determine which hyperparameters to tune. `Figure 6.28` lists the forest hyperparameters that can be automatically tuned.

If **Perform Automatic Tuning** is selected, the following options are available:

- **Maximum Depth**: Whether to automatically tune the maximum depth parameter.
- **Minimum Leaf Node Size**: Whether to automatically tune the minimum leaf node size parameter.
- **Number of Bins**: Whether to automatically tune the number of bins parameter.
- **Number of Trees**: Whether to automatically tune the number of trees parameter.
- **In-Bag Sample Proportion**: Whether to automatically tune the in-bag sample proportion parameter.
- **Number of Inputs per Split**: Whether to automatically tune the number of inputs per split parameter.

If any of the above options are selected, the following options are available:

- **Initial Value**: The initial value of the hyperparameter set for automatic tuning. The default value is the default value of the hyperparameter. Use the **From** and **To** options to specify the range. The default From and To values are the default range of the hyperparameter.

> **Note:** Performing automatic tuning significantly increases runtime.

You can perform cross-validation in the **General Options** of **Perform Automatic Tuning**. However, if your data is already partitioned, that partition will be used, and all other options will be ignored: validation method, validation data proportion, cross-validation folds. If not partitioned, you can select **K-Fold Cross-Validation** in the **Automatic Tuning** options and specify the number of partition folds.

### FOREST Procedure

```
PROC FOREST < options > ;
CROSSVALIDATION < options > ;
GROW criterion ;
ID variables ;
INPUT variables < / LEVEL=NOMINAL | INTERVAL > ;
OUTPUT OUT=CAS-libref.data-table < option > ;
PARTITION partition-option ;
TARGET variable < / LEVEL=NOMINAL | INTERVAL > ;
```

- `PROC FOREST` statement initiates the procedure.
- `CROSSVALIDATION` statement performs k-fold cross-validation to obtain an average estimated validation error. This statement cannot be used if `AUTOTUNE` statement or `PARTITION` statement is also specified.
- `GROW` statement specifies the criterion used to split a parent node into child nodes. As the tree grows, `PROC FOREST` computes the specified criterion for each predictor variable and selects the variable that optimizes the criterion for splitting.
- `ID` statement lists variables to be copied from the input data table to the output data table (in the `OUT=` option and the `RSTORE=` option of the `SAVESTATE` statement).
- `INPUT` statement names input variables that share the same options. The `INPUT` statement can be used multiple times.
- `OUTPUT` statement creates an output data table containing the results of `PROC FOREST`.
- `PARTITION` statement specifies how to logically partition observations in the input data set into disjoint subsets for model training, validation, and testing.
- `TARGET` statement names the target variable, i.e., the variable that `PROC FOREST` attempts to predict.

```
![image](img/Demo.jpg)
```

### Demo 6.2: Tuning a Random Forest Model

- [In this demo, you are improving a previously created default forest model by adjusting specific parameters. You continue using the insurance dataset and try some options in the Forest node.](https://wiki.example.org/feynmans_learning_method)

1. Ensure the `Insurance_ClassTree` project is open in Model Studio, and you are working on the `Forest Models` pipeline.
2. Expand the `Tree-splitting Options` property and observe that `Use default number of inputs to consider per split` is selected by default.

```
![image](img/f0217-01.jpg)
```

`Number of inputs to consider per split` is one of the key aspects of a forest because it typically affects the degree of bias toward the most influential variables. Therefore, the question is how many variables should be considered at each node? This option is only available after clearing `Use default number of inputs to consider per split`.

Unlike manually changing this option in multiple training runs, we will use a programmatic approach to investigate the effect of modifying this option.

3. Right-click the `Data` node, select **Add Child Node** `![image](img/Arrow.jpg)` **Miscellaneous** `![image](img/Arrow.jpg)` **SAS Code**. Rename the SAS Code node to `#Inputs Evaluation`. Your pipeline should look like this.

```
![image](img/f0217-02.jpg)
```

4. With the `#Inputs Evaluations` node selected, click the `Open Code Editor` button on the left.
5. Ensure the cursor is in the `Training code` window, click the leftmost `Load source code file` icon, and navigate to `D:\Workshop\Winsas\VBBF`.

```
![image](img/f0218-01.jpg)
```

6. Select the `Forest_Var_Tries_Evaluation.sas` file containing the following code:

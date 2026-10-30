The leaf-wise algorithm may cause over-fitting with a small set of data, so LightGBM includes a parameter to limit the tree depth which is However, the leaf-wise trees still grow even when the **max_depth** is specified.

The advantages of the histogram-based algorithms include the following:

+   - Reduced cost of calculating the gain for each split.
+   - Uses histogram subtraction for further speedup.
+   - Reduces memory usage.
+   - Reduces communication cost for parallel learning.

For further reading, please go to the following link:

[https://lightgbm.readthedocs.io/en/latest/Features.html](https://lightgbm.readthedocs.io/en/latest/Features.html)

# **Sweeps:**

We will train the LightGBM model to get a first good model, and then we will use Weights & Biases to do the hyperparameter sweep. Here, in this example, we will do a grid search for the LightGBM Framework algorithm over some of the most important
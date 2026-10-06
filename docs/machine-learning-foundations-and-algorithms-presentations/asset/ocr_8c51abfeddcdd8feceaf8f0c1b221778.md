# # Takeaway messages

## What have we learned today?

+   - Kernels estimate the similarity between samples
- They represent an inner product in a feature space
  - Allows to use potentially infinite dimensional
  - That's ok due to the kernel trick and regularization
- Many standard ML algorithms can be “kernelized"
  - i.e. rewritten in terms of inner products
  - **Regression**: Kernel Ridge regression, Gaussian Processes (to be covered), Support Vector Regression (not decovered)
  - **Classification**: SVMs, Kernel Logistic Regression (not covered)

+   - Very flexible representation that adapts to the complexity of the data
- Works well with small data sets

+   - Hard to scale to more complex (high-D) problems or large datasets
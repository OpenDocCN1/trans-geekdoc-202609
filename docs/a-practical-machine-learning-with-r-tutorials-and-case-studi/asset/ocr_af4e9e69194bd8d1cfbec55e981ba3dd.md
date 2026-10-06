172 7 Ridge, Lasso, and Elastic-Net — Regularization Explained

+   * The basic idea behind regularization (see Section 7.4)

+   * The difference between the penalty terms for Lasso and Ridge regression models (see Section 7.4)

+   * How the target function for Lasso regularized regression models differs from the MSE (see Section 7.4.1)

+   * How to create a workflow for Lasso regularized regression using the R tidymodels framework (see Section 7.4.1)

+   * How Lasso regularized parameter estimates are affected by the value of the penalty hyper-parameter (see Section 7.4.1)

+   * How the target function for Ridge regularized regression model differs from the MSE of an unregularized model (see Section 7.4.2)

+   * How to create a workflow for Ridge regularized model using the R tidymodels framework (see Section 7.4.2)

+   * How regularized parameter estimates are affected by the value of the Ridge penalty hyper-parameter (see Section 7.4.2)

+   * Elastic-Net regularization combines elements of both Lasso and Ridge to create a more flexible regularization function (see Section 7.5.3)

+   * How to create a workflow for an Elastic-Net regularized model using the R tidymodels framework (see Section 7.5.3)

+   * How to tune Elastic-Net hyper-parameters and how to measure the final predictive performance (see Section 7.5.4)

# 7.2 R Packages Required for the Chapter

This section lists the R packages that you need to load and execute code in the interactive sections in RStudio. Please install the following packages using Tools -> Install Packages ... from RStudio (you can find more information about installing and loading packages in Section 7.3.4):

+   * The rio package (Chan et al. (2021)) to enable the loading of various data formats with one import() command. Files can be loaded from the user's drive or the Internet.

+   * The janitor package (Firke (2023)) to rename variable names to Upper-Camel and substitute spaces and special characters in variable names.

+   * The tidymodels package (Kuhn and Wickham (2020)) to streamline data engineering and machine learning tasks.
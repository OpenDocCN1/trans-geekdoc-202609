als science, hyperparameters play a critical role throughout the entire pipeline from modeling and feature attribution to material design and the analysis of structure–function relationships. Bayesian optimization treats hyperparameter tuning as a probabilistic search problem, typically modeling the objective function as a Gaussian process. It iteratively updates this model as new observations are made, thereby refining the search and identifying optimal hyperparameter configurations. Figure 6 illustrates the Bayesian optimization workflow, showing how it explores hyperspace to improve model performance in material science applications.

![](bbox=[0.1, 0.27, 0.48, 0.6])

Figure 6: Bayesian optimization for hyperparameter tuning in material models.

# 4.1.1 Application related to material science

From a material perspective, Bayesian optimization has been especially useful in model refinement for material property modeling and engineering. Since the evaluation of functions in experimental material science is generally costly and time-consuming, the benefits of Bayesian optimization in reducing the number of function evaluations are indeed critical. For instance, in contexts like developing predictive models for mechanical properties and thermal stability of materials, Bayesian optimization determines which set of hyperparameters, such as learning rates and regularization strengths, lead to improved and more reliable models. This is particularly essential where the search space is large and where grid search methods are unresponsive and computationally costly.

In this work, the following research methodology, based on Bayesian optimization, is used.
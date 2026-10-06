# 10

# # Tree-Based Models — Bootstrapping Explained

*Tree-based models* are a type of machine learning technique that uses tree-like structures to make predictions. The most basic type of a *tree-based model* is a *Decision Tree*. A Decision Tree gives observation through a specific observation ends up tree-like structure with many branches. The location where a specific observation determines the prediction (more about *Decision Trees* in Section 10.3).

Other tree-based models are based on a combination of *Decision Trees*. They combine an ensemble of machine learning models (i.e., *Decision Trees*), *Tree-based models* can be used for classification and regression tasks.

Since tree-based models are built on *Decision Trees*, you will learn about *Decision Trees* in Section 10.3. Section 10.3.1 introduces the idea behind *Decision Trees*, and in the interactive Section 10.5.2, you can create your own *Decision Tree* model for a classification task. In that section, you will use a Decision Tree model to predict survival of passengers on the Titanic.

How an *ensemble* of *Decision Trees* can be combined into a *Random Forest* will be covered in Section 10.4. While the idea behind a *Random Forest* model is introduced in Section 10.4.1, we will show a real-world application in Section 10.4.2. There, we will use a *Random Forest* model with tidymodels to estimate the COVID-19 vaccination rate for each country in the U.S.

In Section 10.5, we will introduce Boosting Trees algorithms, which are also ensemble models that combine multiple *Decision Trees*. *Bootstrapping* are more advanced and more recent algorithms based on *Decision Trees*. We will freely introduce the idea behind algorithms such as AdaBoost, LightGBM, and CatBoost in Section 10.5. Later, in Section 10.5.1, we will explain *Gradient Boosting* in more detail, and in the interactive Section 10.5.2 you will use XGBoost, which is a computational advanced version of *Gradient Boosting* for a real-world application. You will again estimate the COVID-19 vaccination rate for the continental U.S. counties.
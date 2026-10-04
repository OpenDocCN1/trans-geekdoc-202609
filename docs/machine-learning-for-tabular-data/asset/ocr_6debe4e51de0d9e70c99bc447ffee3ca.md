# Introduction to tree-based methods

boosting. We will especially focus on a machine learning ensemble algorithm, gradient boosting, and its implementations Extreme Gradient Boosting (XGBoost) and Light Gradient Boosted Machines (LightGBM), which are considered state-of-the-art solutions for tabular data.

# 5.1 Introduction to tree-based methods

Tree-based models are a family of ensemble algorithms of different kinds and the favored methods for handling tabular data because of their performance and low requirements in data preprocessing. Ensemble algorithms are sets of machine learning models that contribute together a single prediction. All tree-based models are based on decision trees, a popular algorithm dating back to the 1960s. The basic idea behind decision trees, no matter they are used for classification or regression, is that you can train your tree to have subsets where your prediction is more favorable because there is a dominant output (in a classification problem) or there is a decreased variability of the target values (i.e., they are all near; this refers to a regression problem).

Figure 5.1 shows a schema of the key elements that make up a decision tree. The problem decision tree is trying to solve is classifying an animal on the number of legs and eyes. You start from the root of the tree, branches, and which corresponds to the entire dataset you have available, and set a condition for split. The condition is usually true/false—a so called binary split. Still, some variants of decision trees allow applied at the same node, resulting in multiple splits, each based on a different value or label from the feature. Each branch leads to another node, where a new condition may be applied, or to a terminal node, which is used for predictions based on the instances that terminate there.

![](bbox=[0.187, 0.597, 0.822, 0.866])

Figure 5.1 The key elements, such as roots, branches, and leaves, constituting a decision tree classifying animals based on the number of legs and eyes
integrating the validity in conformal prediction within concepts of interestingness within EMM presents another significant challenge. To address these issues, we propose a novel model class called mSMoPE (multiplex Soft Model Performance Evaluation), which introduces the average size of uncertainty sets as a new target variable for the EMM framework. This allows input attributes to be leveraged in forming cohesive subgroups that capture the relationship between the attributes and the target variable.

In this work, we utilize conformal prediction across various tasks, including classification and regression on tabular data [3]. Based on these applications, we introduce a general framework that demonstrates how conformalized exceptional models can be applied to diverse data mining scenarios to uncover meaningful cohesive patterns. These patterns, represented as conjunctions of attribute-value conditions, offer valuable insights into the behavior of machine learning models. Furthermore, by incorporating deep learning models such as multilayer perceptrons (MLPs), our framework enables a deeper understanding of deep learning models for tabular datasets, facilitating comprehensive performance analysis in tabular tasks.

# 1.1 Main Contributions

We propose a general framework for exceptional model mining with conformal prediction named conformalized exceptional model mining. This framework allows the user to generate a rigorous output about the model's performance with uncertainty measurement. Our main contributions are:

+   - we present mSMoPE: multiplex Soft Model Performance Evaluation, a new model class for EMM. This model class processes the input attributes, distilling a rigorous uncertainty set that captures the uncertainty of the model's output;
+   - based on the proposed new model class, we define a new quality measure that measures the average uncertainty loss between subgroups and the entire dataset. The proposed quality measure allows us to represent the discrepancy quantitatively so that the exceptional interplay between the input attributes and the uncertainty set can be revealed;
+   - we conduct experiments qualitatively and quantitatively on several public datasets. The results effectively demonstrate the interpretable subgroups that are exceptional in terms of predictive uncertainty.

# 2 Related Work

Exceptional Model Mining (EMM) [12,17,34] is a subfield of pattern mining, itself a branch of data mining, that focuses on identifying patterns in subsets of data rather than the dataset as a whole. Pattern mining is distinct in that it seeks to describe only specific portions of the data, often with a predefined
for the next chapter. Some learning techniques make use of feature selection and feature construction, *internally*, in their regular operation. We can also perform feature selection and feature construction as stand-alone preprocessing steps.

One major reason to select a subset of features is when we have a *very* large dataset with many measurements that could be used to train several different learning systems. For example, if we had data on housing sales, we might care about predicting values of houses, recommending houses to particular users, and verifying that mortgage lenders are complying with financial and anti-discrimination laws. Some aspects of the dataset might be useful for answering all of these questions; other features might only apply to one or two of those questions. Trimming down the unneeded features can simplify the learning task by removing irrelevant or redundant information.

One concrete example of feature construction is body mass index. It turns out that accurately measuring a person’s lean body mass—or, less enthusiastically for some, our nonlean mass—is very difficult. Even in a laboratory setting, taking accurate and repeatable measurements is difficult. On the other hand, there are many well-documented relationships between health concerns and the ratio of lean to nonlean mass. In short, it’s very useful for health care providers to have a quick assessment of that ratio.

While it has limitations, BMI is an easy-to-compute result from easy-to-measure values that has a good relationship with health outcomes. It is calculated as BMI = weight / height² with weight in kilograms and height in meters. Practically speaking, at the doctor’s office, you take a quick step on a scale, they put the little stick on your head, and after two quick operations on a calculator, you have a surrogate value for the hard-to-measure concept of lean mass. We can apply similar ideas to bring hard-to-measure or loosely related concepts to the forefront in learning systems.

# 13.1 Feature Selection

From a high-level viewpoint, there are three ways to pick features:

+   1. Single-step filtering: evaluate each feature in isolation, then select some and discard the rest.
+   2. Select-Model-Evaluate-Repeat: select one or more features, build a model, and assess the results. Repeat after adding or removing features. Compared to single-step filtering, this technique lets us account for interactions between features and between features and a model.
+   3. Embed feature selection within model building: as part of the model building process, we can select or ignore different features.

We’ll talk about the first two in more detail in a moment. For the third, feature selection is naturally embedded in several learning techniques. For example:

+   1. Lasso regression from Section 9.1, and L₁ regularization generally, leads to zeros for regression coefficients which is equivalent to ignoring those features.
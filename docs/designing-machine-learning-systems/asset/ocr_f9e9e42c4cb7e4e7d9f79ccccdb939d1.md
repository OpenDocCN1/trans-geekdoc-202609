XGBoost, a variant of GBM, used to be the algorithm of choice for many winning teams of ML competitions.⁶ It’s been used in a wide range of tasks from classification, ranking, to the discovery of the Higgs Boson.⁷ However, many teams have been opting for LightGBM, a distributed gradient boosting framework that allows parallel learning, which generally allows faster training on large datasets.

# Stacking

Stacking means that you train base learners from the training data then create a meta-learner that combines the outputs of the base learners to output final predictions, as shown in Figure 6-5. The meta-learner can be as simple as a heuristic: you take the majority vote (for classification tasks) or the average vote (for regression tasks) from all base learners. It can be another model, such as a logistic regression model or a linear regression model.

![](bbox=[0.13, 0.35, 0.83, 0.65])

Figure 6-5. A visualization of a stacked ensemble from three base learners

For more great advice on how to create an ensemble, refer to the awesome ensemble guide by one of Kaggle’s legendary teams, MLWave.

6 “Machine Learning Challenge Winning Solutions,” https://oreil.ly/YfS8d.

7 Tianqi Chen and Tong He, “Higgs Boson Discovery with Boosted Trees,” Proceedings of Machine Learning Research 42 (2015): 69–80, https://oreil.ly/ysBYO.
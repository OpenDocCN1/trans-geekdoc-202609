# CHAPTER 3 Machine learning vs. deep learning

coordinates. Using the raw latitude and longitude for each listing as features could lead to overfitting because each listing would have a unique value for the pair (latitude, longitude).

+   - The name and host_name columns are not included as features because they are somewhat arbitrary sets of tokens that allow human readers to identify listings. An interesting exercise would be to include host_name as a feature to see if it provides some kind of signal related to the price of listings that have the same host.

+   - We decided to include availability_365 in the feature set because the column is challenging to interpret.

We have examined the features that we will use to train the model to predict whether an Airbnb will have a price above below the average price. In the next section, we will compare the simplicity of the code for the gradient boosting and deep learning models trained on this dataset.

# 3.1.5 Comparing gradient boosting and deep learning solutions

As we mentioned previously, the two solutions for the Airbnb NYC problem only differ in a few places. Figure 3.5 shows the file structure of the solution again with the files that contain differences between the two approaches highlighted.

![](bbox=[0.268, 0.526, 0.555, 0.778])

Figure 3.5 Airbnb listing files that differ between the XGBoost and Keras solutions

If the solutions only differ in these four files, how can we use this example to contrast the simplicity of XGBoost vs Keras deep learning? Table 3.1 compares the code complexity across several aspects of the application.
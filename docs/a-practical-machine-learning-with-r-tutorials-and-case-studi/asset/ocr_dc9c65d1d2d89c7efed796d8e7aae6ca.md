# 10.5 Boosting Trees Algorithms

When you execute the code block above unchanged in RStudio, your results should be similar to the ones below.

Figure 10.3 shows a visualization for the predictive performance for all tried out hyper-parameter values based on Cross-Validation.

![](bbox=[0.238, 0.253, 0.679, 0.529])

**FIGURE 10.3** Tuning the Tree Depth and the Number of Trees

You can see that the mae (mean absolute error) was lowest for a tree_depth value of two in combination with 50 Decision Trees. This makes sense. A Decision Tree with only two levels is a very weak learner. Therefore, even after processing the errors through many trees, some systematic information was left over that each Decision Tree 50 had enough to contribute.

You can see that the tree_depth values of 10 and 15 did not perform very well. Maybe you should try a few tree_depth values below or slightly above.

The situation is not unclear for the number of trees. It looks like that significantly more than 50 trees cannot considerably lower the error. However, for a Decision Tree with only one level (also called a tree stump), it might make sense to increase the number of trees used to more than 100. This might lower the mae even beyond the current minimum because the red line in Figure 10.3 indicates a falling mae for tree_depth=1.
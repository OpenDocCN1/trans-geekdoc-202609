to your stumps and end up capturing nuances in the training data that a single stump never could. That's bagging.

Well, what bagging does with random selections boosting does with weights. Boosting doesn't take random portions of the dataset. It uses the whole dataset on each training iteration. Instead, with each iteration, boosting focuses on training a decision stump that resolves some of the sins committed by the previous decision stumps. It works like this:

+   - At first, each row of training data counts exactly the same. They all have the same weight. In your case, you have 1,000 rows of training data, so they all start with a weight of 0.001. Thus, the weights sum up to 1 (so cute).
+   - Evaluate each feature on the entire dataset to pick the best decision stump. Except when it comes to boosting instead of bagging, the winning stump will be the one that has the lowest weighted error. Each wrong prediction for a possible stump is given a penalty equal to that row’s weight. The sum of those penalties is the weighted error. Choose the decision stump that gives the lowest weighted error.
+   - The weights are adjusted. If the chosen decision stump accurately predicts a row, then that row’s weight decreases. If the chosen decision stump messes up on a row, then that row’s weight increases. Take a moment with this because it can seem counterintuitive.
+   - A new stump is trained using these new weights. In this way, as the algorithm rolls on, it concentrates more on the rows in the training data that previous stumps haven’t gotten right. Stumps are trained until the weighted error exceeds a threshold.

Some of this may seem a bit vague, but the process will become abundantly clear in a spreadsheet. Off to the data! Away we go!

# Training the Model—Every Feature Gets a Shot

In boosting, each feature is a possible stump on every iteration. You won’t be selecting from four features this time.

To start, create a tab called BoostStumps. On it, paste the possible feature/response value combinations from G2:L5 of the RandomSelection tab. I chose to paste them starting in cell B2. Next to those values, place the feature names in row 2. If you’d like, place a “variables” label in the first row. This gives the sheet shown in Figure 7.23.

![](bbox=[0.13, 0.8, 0.85, 0.93])

Figure 7.23: The initial portions of the BoostStumps tab
# CHAPTER 15 NOT A CRYSTAL BALL: MACHINE LEARNING

class 1 and class 2 (which is just 1 minus the class 1 probability) and then uses a threshold (by default, 0.5) to apply the appropriate label. Above 0.5 goes with class 1.

If we look at another real example, we have another dataset with heights, this time of kids. We've got gender, height, and age and we want to predict gender based on the other two. Although it's true that boys are taller than girls, there's still a lot of overlap over our model won't be great with just these two features, but it should be better than chance. I created the model and then plotted the values of height only (I could only plot the target and along with what's called the logistic curve, and one feature in a 2D plot) basically the decision boundary. See Figure 15-9 for what it looks like, with the curve in red. In datasets with more clearly delineated data, the curve is S-like, flatter at the top and bottom and a sharper diagonal in the middle.

![](bbox=[0.113, 0.458, 0.843, 0.646])

**Figure 15-9.** The logistic curve for height and gender in the kids dataset

# Nonlinear Regression

Nonlinear regression is a regression that generates a nonlinear function that combines the model parameters in a nonlinear combination. Some data may not lie in a straight line, but it still fits a recognizable and
An example of what this model might look like is shown in figure 4.7. With two predictor variables, we can represent the model as a plane, with the log odds shown on the vertical axis. The same principal applies for more than two predictors, but it’s difficult to visualize this on a 2D surface!

![](bbox=[0.1, 0.3, 0.8, 0.5])

Figure 4.7 Visualizing a logistic regression model with two predictors. Copper content and lead content are plotted on the x and z axes, respectively. Log odds are plotted on the y axis. The plane shown inside the plot represents the linear model that combines the intercept, and the slopes of copper content and lead content to predict log odds.

Now for any painting we pass into our model, the model:

+   1. Takes its copper content and multiplies it by the slope for copper
+   2. Takes the lead content and multiplies it by the slope for lead
+   3. Adds these two values and the y intercept together to get the log odds of that painting being on original
+   4. Converts the log odds into a probability
+   5. Classifies the painting as an original if the probability is > 0.5, or classifies the painting as a forgery if the probability is < 0.5

We can extend the model to include as many predictor variables as we want:



```
ln(p/(1-p)) = β0 + β1x1 + β2x2 ... βkxk
```
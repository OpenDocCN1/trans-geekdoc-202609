with robust loss functions? To illustrate the effect of outliers, we return to the Belgium telephone dataset from Chapter 2. It is a small dataset used throughout this book to illustrate some key features of linear regression with outliers. Here, we examine the ridge and LASSO penalties and show what happens to the slope of the regression line as the estimates shrink when $\lambda$ is increased. Obviously, multicollinearity does not exist when there is only one variable, but the penalty function is still useful for reasons cited earlier.

Consider Figure 5.2. The two plots, one for ridge and one for LASSO, show the change in the slope as $\lambda$ is adjusted using values 0, 50, 500, and 5000. We observe that the lines all rotate around a pivot point. For LS, the pivot point is the centroid. Both ridge and LASSO start at the unbiased estimate and then

![](bbox=[0.16, 0.3, 0.77, 0.86])

Figure 5.2 Ridge and LASSO effect on LS estimates.
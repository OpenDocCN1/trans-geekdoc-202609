case belongs to one class over another.



Take a look at the (imaginary) data in figure 4.2. I’ve plotted the copper content of a sample of paintings we know to be real or forgeries, against their class as if it were a continuous variable between zero and one. We can see that, on average, the forgeries contain less copper in their paint than the originals. We could model this relationship with a straight line as shown in the figure. This approach works well when your predictor variable has a linear relationship with a continuous variable you want to predict (we’ll discover this in the chapter on linear regression), but as you can see, it doesn’t do a good job at modeling the relationship between a continuous variable, and a categorical one.

As shown in the figure, we could find the copper content at which the straight line passes halfway between 0 and 1, and classify paintings with copper content below this value as forgeries, and paintings above the value, as originals. This may result in many misclassifications, and so a better approach is needed.

![](bbox=[0.2, 0.3, 0.8, 0.6])

We can better model the relationship between copper content and class membership using the logistic function, which is shown in figure 4.3. The logistic function is an "s" shaped curve which
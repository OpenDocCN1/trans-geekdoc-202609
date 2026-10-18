maps a continuous variable (copper content, in our case) onto values between zero and one. This does a much better job of representing the relationship between copper content and whether a painting is an original or forgery. Figure 4.3 shows a logistic function fit to the same data as in figure 4.2. As shown in the figure, we could find the copper content at which the logistic function passes halfway between 0 and 1, and classify paintings with copper content below this value as forgeries, and paintings above the value, as originals. This typically results in fewer misclassifications than when we do this using a straight line.

![](bbox=[0.209, 0.235, 0.715, 0.473])

**Figure 4.3 Modelling the data with the logistic function.** The "s"-shaped line represents the logistic function fitted to the data. The center of the curve passes through the mean of copper content and maps it between zero and one.

Importantly, as the logistic function maps our *x* variable between the values of zero and one, we can interpret its output as the probability of a case with a particular copper content being an original painting.

Take another look at figure 4.3. Can you see that as copper content increases, the logistic function approaches one? This is representing the fact that, on average, original paintings have a higher copper content, so if you pick a painting at random and find it has a copper content of 20, it has ~ 0.99 or 99% probability of being an original!

> > **NOTE**  
> > If I had coded the grouping variable the other way around (with forgeries being one and originals being zero), then the logistic function would approach one for low values of copper and approach zero for high values. We would simply interpret the output as the probability of being a forgery, instead.

The opposite is also true: as copper content decreases, the logistic function approaches zero. This

case belongs to one class over another.

Take a look at the (imaginary) data in figure 4.2. I’ve plotted the copper content of a sample of paintings we know to be real or forgeries, against their class as if it were a continuous variable between zero and one. We can see that, on average, the forgeries contain less copper in their paint than the originals. We could model this relationship with a straight line as shown in the figure. This approach works well when your predictor variable has a linear relationship with a continuous variable you want to predict (we’ll discover this in the chapter on linear regression), but as you can see, it doesn’t do a good job at modeling the relationship between a continuous variable, and a categorical one.

As shown in the figure, we could find the copper content at which the straight line passes halfway between 0 and 1, and classify paintings with copper content below this value as forgeries, and paintings above the value, as originals. This may result in many misclassifications, and so a better approach is needed.

![](img/a22105d68c35e8d5bd3c7bafb4644881_93_0.png)

We can better model the relationship between copper content and class membership using the logistic function, which is shown in figure 4.3. The logistic function is an "s"-shaped curve which

maps a continuous variable (copper content, in our case) onto values between zero and one. This does a much better job of representing the relationship between copper content and whether a painting is an original or forgery. Figure 4.3 shows a logistic function fit to the same data as in figure 4.2. As shown in the figure, we could find the copper content at which the logistic function passes halfway between 0 and 1, and classify paintings with copper content below this value as forgeries, and paintings above the value, as originals. This typically results in fewer misclassifications than when we do this using a straight line.

![](img/a22105d68c35e8d5bd3c7bafb4644881_94_0.png)

## Figure 4.3 Modelling the data with the logistic function.

The "s"-shaped line represents the logistic function fitted to the data. The center of the curve passes through the mean of copper content and maps it between zero and one.

Importantly, as the logistic function maps our *x* variable between the values of zero and one, we can interpret its output as the probability of a case with a particular copper content being an original painting.

Take another look at figure 4.3. Can you see that as copper content increases, the logistic function approaches one? This is representing the fact that, on average, original paintings have a higher copper content, so if you pick a painting at random and find it has a copper content of 20, it has ~ 0.99 or 99% probability of being an original!

> > **NOTE**  
> > If I had coded the grouping variable the other way around (with forgeries being one and originals being zero), then the logistic function would approach one for low values of copper and approach zero for high values. We would simply interpret the output as the probability of being a forgery, instead.

The opposite is also true: as copper content decreases, the logistic function approaches zero. This is representing the fact that, on average, forgeries have lower copper content, so if you pick a painting at random and find it has a copper content of 7, it has ~ 0.99 or 99% probability of being a forgery!

So great, we can estimate the probability of a painting being an original by using the logistic function. But what if we have more than one predictor variable? Because probabilities are bounded between zero and one, it’s difficult to combine the information from two predictors. For example, say the logistic function estimates a painting has a 0.6 probability of being an original for one predictor variable, and a 0.7 probability for the other predictor. We can’t simply add these estimates together because they would be larger than one and this wouldn’t make sense.

Instead we can take these probabilities and convert them into their *log odds* (the "raw" output from logistic regression models). To understand log odds, let me first explain what I mean by *odds*, and the difference between odds and probability.

The odds of a painting being an original are:

### Equation 4.1

\[
\text{odds} = \frac{\text{probability of being an original}}{\text{probability of being a forgery}}
\]

You may come across this written as:

### Equation 4.2

\[
\text{odds} = \frac{p}{1-p}
\]

where *p* is the probability of being an original painting (and *1 − p* is the probability of being a forgery).

Odds are a convenient way of representing the likelihood of something occurring. They tell us how much more likely an event is to occur, than how likely it is *not* to occur.

In *The Empire Strikes Back*, C3PO tells us that the odds of *"successfully navigating an asteroid field is approximately 3720 to 1!"* What C3PO was trying to tell Han and Leia, was that the probability of successfully navigating an asteroid field is approximately 3720 times smaller than the probability of *unsuccessfully* navigating it. Simply stating the odds is often a more convenient way of representing likelihood because we know that, for every one asteroid field

that was successfully navigated, 3720 were not! Additionally, whereas probability is bounded between zero and one, odds can take any positive value.

> **NOTE** Despite being a highly intelligent protocol droid, C3PO got his odds the wrong way around (as many people do). He *should* have said the odds of successfully navigating an asteroid field are approximately 1 to 3720!

Figure 4.4 shows copper content plotted against the odds of a painting being an original. Notice that the odds are not bounded between zero and one, and that they take on positive values.

![](img/a22105d68c35e8d5bd3c7bafb4644881_96_0.png)

## Figure 4.4 Plotting the odds of being an original against copper content.

The probabilities derived from the logistic function were converted into odds and plotted against copper content. Odds can take any positive value. The straight line represents a poor attempt to model a linear relationship between copper content and odds.

As we can see though, the relationship between copper content of the paint, and the odds of a painting being an original is not linear. Instead, if we take the natural logarithm (log with a base of *e*, abbreviated as *ln*) of odds, we get the *log odds*:

# Equation 4.3

$$\log\ \text{odds} = \ln\left(\frac{p}{1-p}\right)$$

[PAGE 97]

> **TIP** The function shown above to convert probabilities into log odds is also called the *logit* function. You will often see "logit regression" and "logistic regression" used interchangeably.

I’ve taken the natural logarithm of the odds shown in figure 4.3 to generate their log odds, and plotted these log odds against copper content in figure 4.5. Hurray! We have a linear relationship between our predictor variable, and the log odds of a painting being an original. Also notice, that log odds are completely unbounded: they can extend to positive and negative infinity! When interpreting log odds:

- A positive value means something is more likely to occur than not to occur
- A negative value means something is less likely to occur than to not occur
- A log odds of zero means something is as likely to occur as not to occur

![](img/a22105d68c35e8d5bd3c7bafb4644881_97_0.png)

## Figure 4.5 Plotting the log odds of being an original against copper content.

The odds were converted into log odds by the logit function and plotted against copper content. Log odds are unbounded and can take any value. The straight line represents the linear relationship between copper content and log odds.

When discussing figure 4.4, I highlighted that the relationship between copper content and the odds of being an original painting, was not linear. Next I showed you in figure 4.5 that the relationship between copper content and log odds *was* linear. In fact, linearizing this relationship is the reason why we take the natural logarithm of the odds. So why did I make such a big deal about there being a linear relationship between our predictor variable and its log odds? Well modelling a straight line is easy. Recall from Chapter 1 that all an algorithm needs to learn to model a straight line relationship is the *y* intercept, and the slope of the line. So logistic regression learns the log odds of a painting being an original when copper content is zero (the *y* intercept), and how the log odds change with increasing copper content (the slope).

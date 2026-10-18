> **TIP** The function shown above to convert probabilities into log odds is also called the *logit* function. You will often see "logit regression" and "logistic regression" used interchangeably.

I’ve taken the natural logarithm of the odds shown in figure 4.3 to generate their log odds, and plotted these log odds against copper content in figure 4.5. Hurray! We have a linear relationship between our predictor variable, and the log odds of a painting being an original. Also notice, that log odds are completely unbounded: they can extend to positive and negative infinity! When interpreting log odds:

+   - A positive value means something is more likely to occur than to not
+   - A negative value means something is less likely to occur, than to occur
+   - A log odds of zero means something is as likely to occur as not to occur

![](bbox=[0.137, 0.368, 0.714, 0.655])

**Figure 4.5 Plotting the log odds of being an original against copper content.** The odds were converted into log odds by the logit function and plotted against copper content. Log odds are unbounded and can take any value. The straight line represents the linear relationship between copper content and log odds.

When discussing figure 4.4, I highlighted that the relationship between copper content and the odds of being an original painting, was not linear. Next I showed you in figure 4.5 that the relationship between copper content and log odds *was* linear. In fact, linearizing this relationship is the reason why we take the natural logarithm of the odds. So why did I make such a big deal about there being a linear relationship between our predictor variable and its log odds? Well modelling a straight line is easy. Recall from Chapter 1 that all an algorithm needs to learn to model a straight line relationship is the *y* intercept, and the slope of the line. So logistic regression learns the log odds of a painting being an original when copper content is zero (the *y* intercept), and how the log odds change with increasing copper content (the slope).
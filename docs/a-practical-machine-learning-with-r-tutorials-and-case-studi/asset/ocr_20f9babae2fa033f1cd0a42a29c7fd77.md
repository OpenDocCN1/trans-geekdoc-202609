# 9.4 The Idea Behind Neural Network Models

```
$Price_i = \beta_7 + \beta_8 A_{1,i} + \beta_9 A_{2,i} \quad (9.7)$
```

If we substitute $A_{1,i}$ and $A_{2,i}$ according to Equations (9.5) and (9.6), we get the Neural Network's prediction function:

![](bbox=[0.283, 0.255, 0.715, 0.319])

![](bbox=[0.385, 0.321, 0.762, 0.39])

Again, for readability, the effective inputs $(I_{1,i}^{eff}$ and $I_{2,i}^{eff})$ for the two neurons are highlighted.

Deriving the prediction function in Equation (9.8) was a little tedious. You might want to go back to Steps 1–6 and read again carefully. It is worth the effort because the prediction equation in (9.8) indicates how a Neural Network can predict based on the predictor values when the $eta$ parameters are known. If you understand this concept, you will realize that the predictive quality of the Neural Network only depends on the right choice of the parameters (the $\beta$).

The takeaways so far:

+   1. The Neural Network from Figure 9.1 can be transformed into a prediction equation (see Equation (9.8)).

+   2. The predicted price for a diamond following Equation (9.8) depends only on the predictor values (Carat and Clarity) and the values for the $\beta$ parameters.

+   3. Since we know the values for the $\beta$, either from randomly choosing or as part of the optimization process, we can predict the price for any diamond based on *Carat* and *Clarity*.

+   4. The initial prediction with a random parameter choice is likely not good, but we can gradually improve the prediction by adjusting the $\beta$ parameters iteratively. How this can be done will be explained in Section 9.4.4.

If not all details are clear to you do not worry, we will follow up with a numerical example in the next section.
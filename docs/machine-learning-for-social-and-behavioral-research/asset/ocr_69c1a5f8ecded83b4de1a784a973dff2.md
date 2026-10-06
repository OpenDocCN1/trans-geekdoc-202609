0.196 and 0.414, respectively. Although both sets of analyses see a decrease
in performance across training and test sets, the SEM model still has higher
explained variance values. We note the large decrease in performance from
assessment on the training set versus test set, particularly for Grit2 which
saw the $R^2$ decrease by 0.312. This decrement can most likely be attributed
to the large number of predictors, inflating the $R^2$ estimate in the training
sample.

# 8.4 Using Latent Variables as Outcomes and Predictors

Given the large number of predictors used in the previous example, the
next step is to determine if a dimension reduction, based on the
toretical formulation of the predictors, can improve our interpretation,
and possibly our prediction of both Grit latent variables. More specifically,
what is to be gained by modeling the latent structure of each of the five
facets of personality? Diagrammatically, this is shown in Figure 8.4.

In this model, we are able to hone in on a smaller number of parameters, namely, the regression coefficients from each of the personality latent
variables to both Grit latent variables. The parameter estimates, both-
standardized and standardized, are displayed in Table 8.2.

In Table 8.2, it is clear that the conscientiousness latent variable is the
most influential predictor of both Grit latent variables, with standardized
coefficients of 0.57 and -0.2. As opposed to examining the influence of
each indicator of the big five traits, we can now look at the specific
contributions of each latent variable. What remains to see what is
lost by modeling the latent structure to the predictors. First, our model
evidenced mixtures of model fit, with an RMSE of 0.051, CFI and
TTLI of 0.74 and 0.73, respectively. Secondly, the percentage of variance
accounted for each of the Grit latent variables decreased from the model
with manifest predictors. Our latent variable predictor formulation
explained 45.8% and 60.2% of the variance in Grit latent variables, respectively,
while the manifest formulation explained 48.7% and 63.8% (note that
these values are different from those in the earlier example in the chapter,
as we used a larger sample size for this analysis). To overcome this level of
model misfit, while also attempting to improve our prediction of Grit, we
will test the use of regularized SEM.
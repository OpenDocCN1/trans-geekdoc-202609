time and the data volume the algorithms can handle, but they will not be
covered further in this book.²¹

Both algorithms are currently not directly available through tidymodels, but
they can be used in connection with the trees package.

# 10.5.1 The Idea Behind Gradient Boosting

As mentioned above Gradient Boosting builds Decision Trees based on pre-
diction errors. No such prediction errors are at the starting point
building the Gradient Boosting ensemble, an initial prediction is needed.
Gradient Boosting starts with the mean of the outcome as prediction
for all observations. Afterward, it uses the errors from previous predictions to
build new trees to enrich the ensemble.

To explain the process in detail, let us see step-by-step how Gradient
Boosting works. To keep it simple, limit the ensemble only to three Decision
Trees. In reality Gradient Boosting works with many Decision Trees.²²

Let us assume we want to create an ensemble with Decision Trees $D_1^{Tree},
$D_2^{Tree}$, and $D_3^{Tree}$. The goal is to produce an outcome variable $Y_i$.

As mentioned, the initial prediction is only based on the mean of the
outcome from the following dataset:

```
$$\hat{Y}_i = \bar{Y} = \frac{1}{N} \sum_{i=1}^{N} Y_i$\quad (10.2)
```

Note that Equation (10.2) implies that the predictions for all observations are
the same because the mean of the outcome is a single number. This is
reasonable, but Equation (10.2) represents a very weak learner, and thus
to expect large prediction errors $(u_{0,i})$. We can calculate these errors for
all training observations because we know the true outcome for each training
observation:

```
$u_{0,i} = Y_i - \bar{Y}\quad (10.3)
```

Note that the index 0 in $u_{0,i}$ indicates that the errors for the $i$ observations
are related to the starting prediction in the *ensemble*. Equation (10.3) can also be
written as Equation (10.4), which states that at the initial stage, the known
outcomes from the training dataset $Y$, consist of the predicted outcome $(\hat{Y})$
 the related errors

> ²¹ See Pramoditha (2021) for introduction to LightGBM and Delgado (2022) for Cat-
Boost.
²²For example, the default for the XGBoost algorithm we use in this section is 15 and
be tuned. Using 100 or more trees is not uncommon.
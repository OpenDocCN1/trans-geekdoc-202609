

Predicted probability of surviving
Feature contribution

![](img/2c227bfb3620dc3d159fa5e6598afa30_310_0.png)

FIGURE 7.25: Predicted probability of survival for Jack across all imputed data sets (left) and their corresponding Shapley-based feature contributions (right).

## 7.9.4 Example: class imbalance (the good, the bad, and the ugly)

As discussed in Section 7.2.1, we often don’t want to predict a class label, but rather the probability of belonging to a particular class—the latter has the benefit of providing some indication of uncertainty (e.g., if we predicted Jack to have a 15% chance of surviving his voyage on the Titanic, then we also estimate that he has an 85% chance of not surviving). Some models, however, can give you poor estimates of the class probabilities. *Calibration* addresses the issue by allowing you to better calibrate the probabilities of a fitted model, or provide estimated probabilities for models that are unable to naturally produce them in the first place (support vector machines, for example).

Calibration refers to the degree of agreement between observed and predicted probabilities, and its utility is well-discussed in the statistical literature (even if not commonly practiced); see, for example, Rufibach [2010], Austin and Steyerberg [2014], and Niculescu-Mizil and Caruana [2005]—the latter discusses calibration in a broader context and includes some discussion on calibrating RFs. A well calibrated (binary) probability model should produce accurate class probabilities such that among those probability estimates close to, say, 0.7, approximately 70% actually belong to the positive class, and so on.

Unless the trees are grown to purity, RFs generally produce consistent and well-calibrated probabilities [Malley et al., 2012, Niculescu-Mizil and Caruana, 2005], while boosted trees (Chapter 8) do not*. However, we'll see shortly that that's not always the case. Furthermore, calibration curves can be useful in comparing the performance of fitted probability models.

Real binary data are often unbalanced. For example, in modeling loan defaults, the target class (default on a loan) is often underrepresented. This is expected since we would hope that most people don't default on their loan over the course of paying it off. However, many practitioners perceive class imbalance as an issue that affects “accuracy.” In actuality, the problem is usually that the data are balanced [Matloff, 2017, p. 193].

In this example, I'm going to simulate some unbalanced data. In particular, I'm going to convert the Friedman 1 benchmark regression data (Section 1.4.3) into a binary classification problem using a latent variable model. Essentially, I'll treat the observed response values as the linear predictor of a logistic regression model and convert them to probabilities. We can then use a binomial random number generator to simulate the observed class labels. The important thing to remember about this simulation study is that we have access to the true underlying class probabilities!

A simple function to convert the Friedman 1 regression problem into a binary classification problem, as described above, is given below. (Note that the line d$y <- d$y - 23 shifts the intercept term and effectively controls the balance of the generated 0/1 outcomes—here, it was chosen to obtain a 0/1 class balance of roughly 0.95/0.05.)

```
gen_binary <- function(...) {
  d <- treemisc::gen_friedman1(...) # regression data
  d$y <- d$y - 23 # shift intercept
  d$prob <- plogis(d$y) # inverse logit to obtain class probabilities
  #d$prob <- exp(d$y) / (1 + exp(d$y)) # same as above
  d$y <- rbinom(nrow(d), size = 1, prob = d$prob) # 0/1 outcomes
  d
}

# Generate samples
set.seed(1921) # for reproducibility
trn <- gen_binary(100000) # training data
tst <- gen_binary(100000) # test data
```

Let \(N = N_0 + N_1\) be the number of observations in the learning sample, where \(N_0\) and \(N_1\) represent the number of observations that belong to class 0 and class 1, respectively. If the learning sample is a random (i.e., representative) sample from the population of interest, then we can estimate the true class priors from the data using \(\pi_i = N_i/N\), for \(i = 1, 2\); this was discussed for CART-like decision trees in Section 2.2.4. There are three scenarios to consider:

- a) the data form a representative sample, and the observed class frequencies reflect the true class priors in the population (**the good**);
- b) the class frequencies have been artificially balanced, but the true class frequencies/priors are known (**the bad**);
- c) the class frequencies have been artificially balanced, and the true class frequencies/priors are unknown (**the ugly**).

In the code chunk below I use an independent sample of size \(N = 10^6\) to estimate \(\pi_1\) (i.e., the *prevalence* of observations in class 1 in the population):

```
(pi1 <- proportions(table(gen_binary(1000000)$y))["1"])
```

```
#> 1
#> 0.0498
```

Next, I'll define a simple calibration function that can be used for *isotonic calibration*; for a brief overview of different calibration methods, see Niculescu-Mizil and Caruana [2005], Kull et al. [2017]. Note that there are many R and Python libraries for calibration; for example, `val.prob()` from R package **rms** [Harrell, Jr., 2021] and the **sklearn.calibration** module.

```
isocal <- function(prob, y) { # isotonic calibration function
  ord <- order(prob)
  prob <- prob[ord] # put probabilities in increasing order
  y <- y[ord]
  prob.cal <- isoreg(prob, y)$yf # fitted values
  data.frame("original" = prob, "calibrated" = prob.cal)
}
```

To start, let's fit a default RF to the original (i.e., unbalanced) learning sample. Note that I exclude the prob column when specifying the model formula.

```
library(ranger)
# Fit a probability forest (omitting the prob column)
set.seed(1446) # for reproducibility
(rfo1 <- ranger(y ~ . - prob, data = trn, probability = TRUE,
                verbose = FALSE))
```

```
#> Ranger result
#>
#>
#> Call:
#> ranger(y ~ . - prob, data = trn, probability = TRUE, verbose = FA...
#>
#> Type:                         Probability estimation
#> Number of trees:             500
#> Sample size:                 100000
#> Number of independent variables: 10
#> Mtry:                          3
#> Target node size:              10
#> Variable importance mode:    none
#> Splitrule:                   gini
#> OOB prediction error (Brier score): 0.0256
```

The OOB prediction error (in this case, the Brier score) is 0.026. The Brier score on the test data can also be computed, but since I have access to the true probabilities, I might as well compare them with the predictions too (for this, I'll compute the MSE between the predicted and true probabilities). In this case, we see that the Brier score on the test set is comparable to the OOB Brier score.

```
prob1 <- predict(rf01, data = tst)$predictions[, 2]
```

```
mean((prob1 - tst$y) ^ 2) # Brier score
```

```
#> [1] 0.0255
```

```
mean((prob1 - tst$prob) ^ 2) # MSE between predicted and true probs
```

```
#> [1] 0.00319
```

Looking at a single metric (or metrics) does not paint a full picture, so it can be helpful to look at specific visualizations, like calibration curves, to further assess the accuracy of the model's predicted probabilities (lift charts can also be useful). The leftmost plot in Figure 7.26 shows the actual vs. predicted probabilities for the test set, as well as the isotonic-based calibration curve from the above RF. In this case, the RF seems to be doing a reasonable job in terms of accuracy. The model seems well-calibrated for probabilities below 0.5, but seems to have a slight negative bias for probabilities above 0.5, which makes sense since most of the probability mass is concentrated near zero (as we might have expected given the true class frequencies).

To naively combat the perceived issue of unbalanced class labels, the learning sample is often artificially rebalanced (e.g., using down sampling) so that the class outcomes have roughly the same distribution. In general, THIS IS A BAD IDEA for probability models, and can lead to serious bias in the predicted probabilities—in fact, any algorithm that requires you to remove good data to optimize performance is suspect. Nonetheless, sometimes the data have been artificially rebalanced in a preprocessing step outside of our control, or maybe you decided to down sample the data to reduce computation time (in which case, you should try to preserve the original class frequencies, or at least store them for adjustments later). In any case, let's see what happens to our predictions when we down sample the majority class.

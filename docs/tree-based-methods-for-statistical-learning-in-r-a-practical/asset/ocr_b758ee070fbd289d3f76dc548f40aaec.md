Nice, an overall accuracy of 81%—similar to the best accuracy reported in Frey and Slate [1991]. But don't be fooled, the data have been artificially balanced:

```
table(lr$lettr)
#>
#> A B C D E F G H I J K L M
#> 789 766 736 805 768 775 773 734 755 747 739 761 792
#> N O P Q R S T U V W X Y Z
#> 783 753 803 783 758 748 796 813 764 752 787 786 734
```

As noted in Matloff [2017, Sec. 5.8], this is unrealistic since some letters tend to appear much more frequently than others in English text. For example, assuming balanced classes, `rpart()` uses a prior probability for the letter “A” of $\pi_A = 1/26 \approx 0.0384$, when in fact $\pi_A$ is closer to 0.0855.

A proper analysis should take these frequencies into account, which is easy enough to do with classification trees. Fortunately, the correct letter frequencies are conveniently available in the **regtools** package [Matloff, 2019]. Below, I’ll refit the model including the updated (and more realistic) class priors. I’ll then sample the test data so that the resulting class frequencies more accurately reflect the true prior probabilities of each letter:

```
data(ltrfreqs, package = "regtools")
```

```
# Compute correct class priors
priors <- ltrfreqs$percent
priors <- priors / sum(priors) # class priors should sum to 1
names(priors) <- ltrfreqs$ltr
priors <- priors[order(ltrfreqs$ltr)]
```

```
# Refit tree using correct priors
set.seed(1718) # for reproducibility
lr.cart.priors <- rpart(lettr ~ ., data = lr.trn, cp = 0,
parms = list(prior = priors))
lr.cart.priors <- prune_se(lr.cart.priors, se = 1)
```

```
# Sample test set to reflect correct class frequencies
ltrfreqs2 <- ltrfreqs
names(ltrfreqs2) <- c("lettr", "prior")
ltrfreqs2$prior <- ltrfreqs2$prior / sum(ltrfreqs2$prior)
temp <- merge(lr.tst, ltrfreqs2) # merge the two data sets
set.seed(1107) # for reproducibility
lr.tst2 <- temp[sample(nrow(temp), replace = TRUE,
prob = temp$prior), ]
```

Finally, let’s compare the two CART fits on the modified test set that reflects the more correct class frequencies:

w Based on the English letter frequencies reported at http://practicalcryptography.com.
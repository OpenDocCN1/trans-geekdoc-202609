each feature. For categorical variables, $P(E|H)$ is estimated using the feature values frequencies.

# 2.4.1 Activity Recognition with Naive Bayes

```
naive_bayes.R
```

It's time to implement Naive Bayes. To keep it simple, we will first go through a by step example using a single feature. Then, we will implement a function to train a Naive Bayes classifier for the class of multiple features.

Let us assume we have already split the data into train and test sets. The complete code is in the script naive_bayes.R. We will only use the feature RESULTANT which corresponds to the acceleration magnitude of the three axes of the accelerometer sensor. The following code snippet prints the first rows of the train set. The RESULTANT feature is in column 39 and the class is the last column (40).

```
head(trainset,c(39:40]))
#> RESULTANT class
#> 1004 11.14 Walking
#> 623 1.24 Upstairs
#> 2693 9.90 Standing
#> 934 10.44 Upstairs
#> 4496 10.43 Walking
#> 2948 15.28 Jogging
```

First, we compute the prior probabilities for each class in the train set and store them in the variable priors. This corresponds to the $P(C_k)$ part in equation (2.13).

```
# Compute prior probabilities.
priors <- table(trainset$class) / nrow(trainset)

n# Print the table of priors.
```

> **NOTE:** The first discriminant function always does the best job at separating the classes, followed by the second, third, etc.

![](img/a22105d68c35e8d5bd3c7bafb4644881_129_0.png)

LDA has taken a three-dimensional dataset and combined the information in those three variables into two new variables that maximize the separation between the classes. That’s pretty cool, but if instead of just three predictor variables we had 1000 (as in the example I used earlier), LDA would still condense all this information into only two variables! That’s super cool!

LDA performs well if the data within each class are normally distributed across all the predictor variables, and that each class has similar covariances. Covariance simply means how much one variable increases/decreases when another variable increases/decreases. So LDA assumes that for each class in the dataset, the predictor variables covary with each other the same amount.

This often isn’t the case and classes have different covariances. In this situation, QDA tends to perform better than LDA as it doesn’t make this assumption (though it still assumes the data are normally distributed). Instead of learning straight lines that separate the classes, QDA learns curved lines. It is also well suited, therefore, to situations in which classes are best separated by a non-linear decision boundary. This is illustrated in figure 5.7.

In the example on the left of figure 5.7, the two classes are normally distributed across both variables, and have equal covariances. We can see the covariances are equal because, for both classes, as variable 1 increases, variable 2 decreases by the same amount. In this situation, LDA and QDA will find similar discriminant functions, although LDA is slightly less prone to overfitting than QDA as it is less flexible.

In the example on the right of figure 5.7, the two classes are normally distributed, but their covariances are different. In this situation QDA will find a curved discriminant function that, when the data are projected onto it, will tend to do a better job of separating the classes than a linear discriminant function.

![](img/a22105d68c35e8d5bd3c7bafb4644881_130_0.png)

So whichever method you’ve chosen, the discriminant functions have been constructed and you’ve reduced your high-dimensional data into a small number of discriminants. How do LDA and QDA use this information to classify new observations? They use an extremely important statistical theorem called Bayes' rule.

Bayes' rule provides us with a way of answering the following question: given the values of the predictor variables for any case in our data, what is the probability of that case belonging to class k. This is written as p(k|x), where k represents membership of class k, and x represents the values of the predictor variables. We would read this as: "the probability of belonging to class k, given the data, x". This is given by Bayes' rule:

```
p(k|x) = p(x|k) × p(k) / p(x)
```

Don't be scared by this! There are only four terms in the equation and I'm going to walk you through them. You already know p(k|x) is the probability of a case belonging to class k given the data. This is called the posterior probability.

- *p(x|k)* is the same thing but flipped around: what is the probability of observing this data, given the case belongs to class k? Put another way: if this case was in class k, what is the likelihood of it having these values of the predictor variables? This is called the likelihood.
- *p(k)* is called the prior probability, and is simply the probability of any case belonging to class k. This is the proportion of all cases in the data that belong to class k. For example, if 30% of cases were in class k, *p(k)* would equal 0.3.

Finally, p(x) is the probability of observing a case with exactly these predictor values in the dataset. This is called the evidence. Estimating the evidence is often very difficult (because each case in the dataset may have a unique combination of predictor values), and it only serves to make all the posterior probabilities sum to one. Therefore, we can omit the evidence from the equation and say that:

**EQUATION 5.3**

```
p(k|x) ∝ p(x|k) × p(k)
```

where the symbol ∝ means the values either side of it are proportional to each other instead of equal to each other. In a more digestible way:

**EQUATION 5.4**

```
posterior ∝ likelihood × prior
```

The prior probability for a case (p(k)) is easy to work out: it’s simply the proportion of cases in the dataset that belong to class k. But how do we calculate the likelihood (p(x|k))? The likelihood is calculated by projecting the data onto their discriminant functions, and estimating their probability density. The probability density is simply the relative probability of observing a case with a particular combination of discriminant scores.

Discriminant analysis assumes that the data are normally distributed, so it estimates the probability density by fitting a normal distribution to each class, across each discriminant function. The center of each normal distribution is the class centroid, and its standard deviation is one unit on the discriminant axis. This is illustrated in figure 5.8 for a single discriminant function, and for two (the same happens in more than two dimensions but is difficult to visualize!). You can see that cases near the class centroid along the discriminant axes have high probability density for that class, and cases far away have a lower probability density.

One discriminant function

Two discriminant functions

![](img/a22105d68c35e8d5bd3c7bafb4644881_132_0.png)

Figure 5.8 Probability density of each class is assumed to be normally distributed, where the center of each distribution is the centroid of the class. This is shown for one discriminant function (for classes k and j) and for two.

Once the probability density for a case, for a given class, is estimated, it can be passed into the equation:

```
posterior = likelihood × prior
```

The posterior probability is estimated for each class, and the class that has the highest probability is what the case is classified as.

> The reason the prior probability (proportion of cases in that class) is important is that if the classes are severely imbalanced, despite a case being far from the centroid of a class, it could be more likely to belong to that class simply because there are so many more cases in it.

Bayes' rule is very important in statistics and machine learning. Don’t worry though if you don’t quite understand it yet, that’s by design. I want to introduce you to it gently now, and we’ll cover it in more depth in Chapter 6.

## 5.2 Building our first linear and quadratic discriminant models

So now we know how discriminant analysis works, we’re going to build our first LDA model. If you haven’t already, load the mlr and tidyverse packages.

```r
library(mlr)
library(tidyverse)
```

```r
names(wineTib) <- c("Class", "Alco", "Malic", "Ash", "Alk", "Mag", "Phe", "Flav", "Non_flav", "Proan", "Col", "Hue", "OD", "Prol")
wineTib$Class <- as.factor(wineTib$Class)
wineTib
```

A tibble: 178 × 14

| Class | Alco | Malic | Ash | Alk | Mag | Phe | Flav | Non_flav | Proan | Col | Hue | OD | Prol |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 14.2 | 1.71 | 2.43 | 15.6 | 127 | 2.8 | 3.06 | 0.28 | 2.29 | 5.64 | 1.04 | 3.92 | 1065 |
| 1 | 13.2 | 1.78 | 2.14 | 11.2 | 100 | 2.65 | 2.76 | 0.26 | 1.28 | 4.38 | 1.05 | 3.4 | 1050 |
| 1 | 13.2 | 2.36 | 2.67 | 18.6 | 101 | 2.8 | 3.24 | 0.3 | 2.81 | 5.68 | 1.03 | 3.17 | 1185 |
| 1 | 14.4 | 1.95 | 2.5 | 16.8 | 113 | 3.85 | 3.49 | 0.24 | 2.18 | 7.8 | 0.86 | 3.45 | 1480 |
| 1 | 13.2 | 2.59 | 2.87 | 21 | 118 | 2.8 | 2.69 | 0.39 | 1.82 | 4.32 | 1.04 | 2.93 | 735 |
| 1 | 14.2 | 1.76 | 2.45 | 15.2 | 112 | 3.27 | 3.39 | 0.34 | 1.97 | 6.75 | 1.05 | 2.85 | 1450 |
| 1 | 14.4 | 1.87 | 2.45 | 14.6 | 96 | 2.5 | 2.52 | 0.3 | 1.98 | 5.25 | 1.02 | 3.58 | 1290 |
| 1 | 14.1 | 2.15 | 2.61 | 17.6 | 121 | 2.6 | 2.51 | 0.31 | 1.25 | 5.05 | 1.06 | 3.58 | 1295 |
| 1 | 14.8 | 1.64 | 2.17 | 14 | 97 | 2.8 | 2.98 | 0.29 | 1.98 | 5.2 | 1.08 | 2.85 | 1045 |
| 1 | 13.9 | 1.35 | 2.27 | 16 | 98 | 2.98 | 3.15 | 0.22 | 1.85 | 7.22 | 1.01 | 3.55 | 1045 |

That’s much better. We can see that we have 13 continuous measurements made on 178 bottles of wine, where each measurement is the amount of a different compound/element in the wine. We also have a single categorical variable, Class, which tells us which vineyard the bottle comes from.

> Lots of people consider it good form to keep variable names lowercase. I don’t mind so much so long as my style is consistent. Therefore, notice that I changed the name of the grouping variable class to Class!

Let’s plot the data to get an idea of how the compounds vary between the vineyards. As for the Titanic dataset in Chapter 4, we’re going to gather the data into an untidy format so we can facet by each of the variables.

```r
wineUntidy <- gather(wineTib, "Variable", "Value", -Class)
ggplot(wineUntidy, aes(Class, Value)) +
  facet_wrap(~ Variable, scales = "free_y") +
  geom_boxplot() +
  theme_bw()
```

The resulting plot from code listing 5.3 is shown in figure 5.9.

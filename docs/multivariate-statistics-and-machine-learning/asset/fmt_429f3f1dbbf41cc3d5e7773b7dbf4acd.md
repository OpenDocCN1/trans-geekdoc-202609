
```
> iris[iris$Species!=“setosa”,] ->iris
```

By dropping `setosa`, we will have removed 50 cases from the data set, so that the new data set should contain 100 cases. We can confirm this by requesting the dimension (`dim()`) of the new data:

```
> n <- dim(iris)[1]
> n
[1] 100
```

We assigned the dimension (`dim`) of the data because we are going to use `n` in what follows. We will sample 60 observations (i.e., `.6*n`; [Culp et al., 2016](#ref.xhtml#re_CIT000073), p. 5):390

```
> trind <- sample(1:n, floor(.6*n), FALSE)
> trind
```

| \[1\] || 9 || 57 || 50 || 12 || 47 || 3 || 49 || 66 || 48 || 77 || 19 || 40 || 98 || 35 || 44 || 87 |

| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

| \[17\] || 43 || 28 || 7 || 55 || 32 || 76 || 84 || 75 || 83 || 46 || 36 || 21 || 72 || 74 || 20 || 5 |

| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

| \[33\] || 60 || 78 || 4 || 53 || 85 || 61 || 79 || 64 || 38 || 33 || 31 || 17 || 97 || 45 || 86 || 93 |

| \[49\] || 68 || 42 || 81 || 100 || 59 || 99 || 71 || 96 || 89 || 73 || 88 || 15 ||  ||  ||  ||  |

We now obtain the balance of what was not selected by `trind`, where the function `setdiff` stands for *set difference of subsets*:

```
> teind <- setdiff(1:n, trind)
> teind
```

| \[1\] || 1 || 2 || 6 || 8 || 10 || 11 || 13 || 14 || 16 || 18 || 22 || 23 || 24 || 25 || 26 || 27 || 29 || 30 || 34 || 37 || 39 |

| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

| \[22\] || 41 || 51 || 52 || 54 || 56 || 58 || 62 || 63 || 65 || 67 || 69 || 70 || 80 || 82 || 90 || 91 || 92 || 94 || 95 ||  ||  |

| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

We now create the associated factor levels as well as numeric variables:

```
> iris[,5]<- as.factor((levels(iris[,5])[2:3])[as.numeric(iris[,5])-1])
```

We are now ready to fit the trees. The following will fit eight-split trees (Culp et al., [2016](#ref.xhtml#re_CIT000073), p. 5). We specify the number of iterations to equal 20 (`iter=20`) and set the shrinkage parameter (`nu`) equal to 1:

```
> gdis <- ada(Species~., data=iris[trind,], iter=20, nu=1, type=“discrete”)
> gdis
Call:
ada(Species ~ ., data = iris[trind, ], iter = 20, nu = 1, type = “discrete”)
Loss: exponential Method: discrete  Iteration: 20
Final Confusion Matrix for Data:
```

|  || Final Prediction |

| --- | --- |

| True value || versicolor || virginica |

| --- | --- | --- |

| Versicolor || 33 || 0 |

| Virginica || 0 || 27 |

```
Train Error: 0
Out-Of-Bag Error: 0.017 iteration= 6
```

| train.err1 || train.kap1  |

| --- | --- |

| 9 || 9 |

| --- | --- |

We note the confusion matrix results in perfect classification. We can also see from the above output that the out-of-bag error is equal to 0.017 for iteration = 6. As iterations increase, overfitting becomes a concern. These results can be visualized to observe fluctuations on the training error across iterations ([Figure 10.8](#c10.xhtml#f10.8)). Note that by iteration 9, the training error has bottomed to 0, which agrees with the output above. We note as well that `kappa` ([Figure 10.8](#c10.xhtml#f10.8)), which measures the agreement between observed and predicted classification, is also maximized by iteration 9 (these figures are reported in the above output, `train.err1` = 9, `train.kap1` = 9), where `TRUE`, `TRUE` controls the reporting of training and kappa curves:

![Figure 10.8 Training error (left) and training kappa (right) as a function of iteration. As the number of iterations increases, training error decreases, while kappa increases.Return to text.⏎](images/fig10.8.jpg)

*Figure 10.8* Training error (left) and training kappa (right) as a function of iteration. As the number of iterations increases, training error decreases, while kappa increases.[Return to text.⏎](#c10.xhtml#re_f10.8)

```
> plot(gdis, TRUE, TRUE)
```

391

Now, we add the testing data and evaluate both training and testing error:

```
> gdis=addtest(gdis, iris[teind, -5], iris[teind, 5])
> plot(gdis, TRUE, TRUE)
```

We can see from the left plot in [Figure 10.9](#c10.xhtml#f10.9) that the training error decreases while the testing error remains relatively constant until it elevates toward the end of the iterations, likely due to overfitting. The `kappa accuracy` reflects the extent to which there is agreement between the observed classification and the predicted classification. We see from the plot that kappa increases on the train data as the number of iterations increases, which is what we would expect, as the higher the kappa score, the greater the degree of agreement. Kappa decreases, however, on the test data as we near the final iteration, which is likely again a sign of overfitting.

![Figure 10.9 Testing and training error as a function of iteration (left). Training and testing kappas as a function of iteration (right).Return to text.⏎](images/fig10.9.jpg)

*Figure 10.9* Testing and training error as a function of iteration (left). Training and testing kappas as a function of iteration (right).[Return to text.⏎](#c10.xhtml#re_f10.9)

Finally, we can obtain a variable importance plot as in [Figure 10.10](#c10.xhtml#f10.10).392

![Figure 10.10 Variable importance measures for different features on the iris data.Return to text.⏎](images/fig10.10.jpg)

*Figure 10.10* Variable importance measures for different features on the iris data.[Return to text.⏎](#c10.xhtml#re_f10.10)

```
> varplot(gdis)
```

We can see from [Figure 10.10](#c10.xhtml#f10.10) that in the boosted sample, `sepal length` is most important, followed by `sepal width`. See Hastie et al. ([2009](#ref.xhtml#re_CIT000145), [Chapter 10](#c10.xhtml#c10)) for the computation of variable importance in this context. Re-running the model at various iterations may be useful both to regulate overfitting and also to observe changes in variable importance.

Whereas bagging and boosting combines weak “base” learners to produce a stronger learner, so-called `stacked models` seek to combine weak to strong learners into an even stronger one via optimizing the weighting of each model, a so-called `super learner`. This is generally referred to as `stacking` or `stacked generalization` ([Hastie et al., 2009](#ref.xhtml#re_CIT000145)). Stacked learners will often outperform individual base learners. [Breiman (1996, p. 51)](#ref.xhtml#re_CIT000047) summarizes the benefits of stacking:

> The results show that stacking can produce predictors with substantially reduced prediction errors. Stacking never does worse than selecting the single best predictor. We note that the biggest gains came when dissimilar sets of predictors were stacked, i.e., subset selection and ridge regressions. The more similar the predictors, the less advantage there is in stacking.

In R, we can use the package `h2o` ([Fryda et al., 2023](#ref.xhtml#re_CIT000120)) for model stacking. For details on stacked generalization, see [Hastie et al. (2009)](#ref.xhtml#re_CIT000145).393

## 10.8 Chapter Review Exercises

1. 1\. Distinguish between a `weak` vs. `strong` learner. Which, in general, is preferable? How are several weak learners potentially advantageous over fewer strong learners?

2. 2\. Describe the nature of a `decision tree`, both for classification and regression.

3. 3\. What does it mean to “overfit” a tree? How does `pruning` a tree reduce the possibility of overfitting?

4. 4\. Discuss the influence of the number of terminal nodes as it pertains to cost complexity pruning. How does the tuning parameter serve to regularize error?

5. 5\. Compare and contrast the `classification error rate` to the `Gini index`. How are they similar? Different?

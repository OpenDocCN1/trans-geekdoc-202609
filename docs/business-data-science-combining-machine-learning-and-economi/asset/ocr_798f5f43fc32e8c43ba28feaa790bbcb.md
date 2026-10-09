Now every variable has a standard deviation of 1. We can then run both 1-NN and 5-NN algorithms where a random sample of test observations are left out for prediction.

```
```
> test <- sample(1:214,10)
> nearest1 <- knn(train=x[- test,], test=x[test,], cl=fgl$type[- test], k=1)
> nearest5 <- knn(train=x[-test,], test=x[test,], cl=fgl$type[-test], k=5)
> data.frame(fgl$type[test], nearest1,nearest5)
```
```

```
```
fgl.type.test. nearest1 nearest5
     1     WinF     WinF     WinF
     2     WinF     WinF     WinF
     3     Tabl     Tabl     Tabl
     4     Veh    WinNF    WinNF
     5     Con      Con     Head
     6    WinNF    WinF     WinF
     7     Head     Head     Head
     8     WinF     WinF     WinF
     9     WinF     WinF     WinF
     10    WinNF    WinNF    WinNF
```
```

In this case, 1-NN manages 80% accuracy, while 5-NN obtains 70%. However, if you rerun on random test sets, these numbers will move a lot.

There are a some major problems with practical application of KNN. First, we can deduce that K-NN predictions will be *unstable* as a function of K. For example, using the counts as probabilities, in Figure 4.1 we see the following:

```
```
$K = 1 \Rightarrow \hat{p}_f(white) = 0$, 
$K = 2 \Rightarrow \hat{p}_f(white) = 1/2$, 
$K = 3 \Rightarrow \hat{p}_f(white) = 2/3$, 
$K = 4 \Rightarrow \hat{p}_f(white) = 1/2$.
```

The predicted $\hat{y}_f$ also changes with each of these different K. As mentioned in Chapter 3, such instability of predictions makes it hard to choose the optimal K and hence cross validation doesn't work well for KNN. Moreover, since prediction for each new $x_f$ requires a computationally
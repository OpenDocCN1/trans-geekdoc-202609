For the semiconductor data, we can do OOS validation on both the*full* and *cut* regression models. To do this, we first need to define some functions to calculate deviance and *R*2.

```
> ## pred must be probabilities (0<pred<1) for binomial
> deviance <- function(y, pred, family=c("gaussian", "binomial")){
+         family <- match.arg(family)
+         if(family=="gaussian"){
+               return( sum( (y-pred) ^2 ))
+         }else{
+               if (is.factor(y)){ y <- as.numeric (y)>1
+               return( -2*sum( y*log(pred) + (1-y)*log(1-pred)) )
+         }
+ }
>
> ## get null deviance too, and return R2
> R2 <- function(y, pred, family=c("gaussian", "binomial")){
+         fam <- match.arg(family)
+         if (fam=="binomial"){
+               if (is.factor(y)){ y <- as.numeric(y)>1 }
+         }
+         dev <- deviance(y, pred, family=fam)
+         dev0 <- deviance(y, mean(y), family=fam)
+         return (1-dev/dev0)
+ }
```

These functions can be used for either linear or logistic regression. In later chapters you'll be using R package functions that have these deviance calculations as built-ins, but it is good to code them yourself once. Next, we split the data into folds.
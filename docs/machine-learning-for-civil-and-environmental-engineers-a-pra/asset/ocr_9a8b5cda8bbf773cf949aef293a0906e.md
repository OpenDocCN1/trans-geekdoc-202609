#Setting the parameters for the XG.boost Model using list() function

```
>params<-list(set.seed=1500, eval_metric="auc", objective="binary:logistic")
```

#Running XG.boost model using xgboost() function a simple and fast way of implementing Extreme Gradient Boosting algorithm.

```
>modelxg <-xgboost(data = as.matrix(xtrainxg), label = ytrainxg,
params = params, nrounds = 20,
verbose = 1)
```

#Checking the model accuracy using Confusion Matrix (Sensitivity, Specificity, and Accuracy). The confusionMatrix() function can show the result.

```
>trained<-model.matrix(trainxg$Output~.-1,data = trainxg) trainlable<-trainxg[,1]
trainlable<-as.numeric(trainlable)-1
tested<-model.matrix(testxg$Output~.-1,data = testxg) testlabel<-testxg[,1]
testlabel<-as.numeric(testlabel)-1
pred<-predict(modelxg,tested) head(pred)
pred<-as.integer(pred>0.5) confusionMatrix(table(pred, testxg$Output))
```

#Plotting correlation matrices using cor() function. These plots show the correlation between different variables in the dataset. The first method is spearman that evaluate the monotonic relationship, and the last one is Pearson which evaluates the linear relation between two different continues variables.
#first Method (Spearman)

```
>m=cor(data, method = "spearman") corrplot(m, type = "full",
method = "circle", tl.cex = 0.5, tl.col = 'black')
corrplot(m, type = "full",
method = "number", tl.cex = 0.55, tl.col = 'black')
corrplot(m, method ="color",type = "upper",order ="hclust",tl.cex = 0.5, tl.col =
"black",tl.srt = 45, diag
= FALSE)
```

#Second method (Pearson)

```
>n=cor(data, method ="pearson") corrplot(n, type = "full",
method = "circle", tl.cex = 0.5, tl.col = 'black')
corrplot(n, type = "full",
method = "number", tl.cex = 0.55, tl.col = 'black')
corrplot(n, method ="color",type = "upper",order ="hclust",tl.cex = 0.5, tl.col =
"black",tl.srt = 45, diag
= FALSE)
```

#This summary plot is considered one of the most important plots in SHAP. The plot axes are as follows: Vertical location shows what the feature is depicting. The color shows whether that feature was high or low for that row of the dataset. Horizontal location shows whether the effect of that value caused a higher or lower prediction. It can be implemented using xgb.plot.shap.summary() function.

```
>xgb.plot.shap(data = as.matrix(xtrainxg), model = modelxg,
top_n =5)
>>xgb.plot.shap.summary(data = as.matrix(xtrainxg), model = modelxg,
```
![](bbox=[0.0, 0.05, 1.0, 0.35])

NOTE The first discriminant function always does the best job at separating the classes, followed by the second, and third etc.

LDA has taken a three-dimensional dataset and combined the information in those three variables into two new variables that maximize the separation between the classes. That’s pretty cool, but if instead of just three predictor variables we had 1000 (as in the example I used earlier), LDA would still condense all this information into only two variables! That’s super cool!



LDA performs well if the data within each class are normally distributed across all the predictor variables, and that each class has similar covariances. Covariance simply means how much one variable increases/decreases when another variable increases/decreases. So LDA assumes that for each class in the dataset, the predictor variables covary with each other the same amount.

This often isn’t the case and classes have different covariances. In this situation, QDA tends to perform better than LDA as it doesn’t make this assumption (though it still assumes the data are normally distributed). Instead of learning straight lines that separate the classes, QDA learns curved lines. It is also well suited, therefore, to situations in which classes are best separated by a non-linear decision boundary. This is illustrated in figure 5.7.

In the example on the left of figure 5.7, the two classes are normally distributed across both variables, and have equal covariances. We can see the covariances are equal because, for both classes, as variable 1 increases, variable 2 decreases by the same amount. In this situation, LDA and QDA will find similar discriminant functions, although LDA is slightly less prone to overfitting than QDA as it is less flexible.
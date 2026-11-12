# ## 6.2.2.1 Procedure

The wrapper method is an iterative algorithm that works as follows:

+   1) Initialize an empty set of selected features.
+   2) Train a model with all the available features and evaluate its performance using a validation set.
+   3) Add a feature to the set for each one that is absent from the chosen set, then train the model using both the chosen features and the new feature. Use the validation set to evaluate the model's effectiveness.
+   4) Add the feature to the chosen set that results in the greatest performance increase.
+   5) Continue performing steps 3 and 4 until a stopping criterion is reached.

This process is illustrated in Figure 6.2.

As we can see, the wrapper approach chooses the feature that results in the greatest performance increase at each iteration. This is accomplished by contrasting the performance of the model with and without the additional feature. If performance increases, the feature is added to the predetermined set, and the procedure continues.

![](bbox=[0.12, 0.47, 0.94, 0.895])

Figure 6.2 Steps in wrapper method.
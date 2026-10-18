# 3

Classifying based on similar observations:  
the k-Nearest neighbors algorithm

***This chapter covers:***

+   - What the k-nearest neighbors algorithm is and how it works
+   - What the bias-variance trade is
+   - The difference between underfitting and overfitting
+   - How to use cross-validation to assess model performance
+   - Building a k-nearest neighbors classifier to classify potential diabetes patients
+   - What hyperparameters are and how to tune them

This is probably the most important chapter of the entire book. In it, I’m going to show you how the k-nearest neighbors (k-NN) algorithm works, and we’re going to use it to classify potential diabetes patients. But this chapter is much more important than that, as I’m going to use the k-NN algorithm to teach you some essential concepts in machine learning that we will rely on for the rest of the book. These concepts include:

+   - underfitting (making a model that is too simple to reflect trends in the data)
+   - overfitting (making a model that is too complex and fits the noise in the data)
+   - the bias-variance trade-off (the balance between underfitting and overfitting)
+   - cross-validation (the process by which we tell if we are overfitting or underfitting)
+   - hyperparameter tuning (the process by which we find the optimal options for an algorithm)

By the end of this chapter, not only will you understand and be able to use the k-NN algorithm to make classification models, you will be able to validate its performance and tune it to improve its performance as much as possible. Once the model is built, you’ll learn how to pass new, unseen data into it and get their predicted classes (the value of the categorical or grouping variable we
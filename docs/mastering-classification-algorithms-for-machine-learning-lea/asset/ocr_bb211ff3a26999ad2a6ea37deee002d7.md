# Boosting Algorithm 271

yTrainPred = model1.predict(X_train)
print("Training Accuracy:", accuracy_score(y_train, yTrainPred)

yTestPred = model1.predict(X_train)
print("Test Accuracy:", accuracy_score(y_test, yTestPred))
Training Accuracy: 0.9876288659793815
Test Accuracy: 0.49382716049382713

Notice with a basic Neural Network, we get a test accuracy of 49.38%.

# Conclusion

In this chapter, we discussed a very powerful and popular algorithm for solving classification problems: AdaBoost. The AdaBoost Model which works in a sequence of iterations. In each iteration, the algorithm identifies the classification errors made in the previous iteration and tries to reduce the number of errors. This process continues until the algorithm can either find that the current iteration does not make any error in classification, or the algorithm can no longer reduce the number of errors.

That is the end of this book. Refer to the annexures for details on related topics discussed in the chapters.

Happy learning!

# Points to remember

+   - In Boosting Models, we create a sequence of models. For developing each model, we use the entire dataset initially. Also, each model is developed using the same algorithm.
- In each iteration of the sequence, the Boosting models try to eliminate the errors in the prediction made made in the previous iteration.
- AdaBoost is a powerful Boosting algorithm. AdaBoost is the short form of Adaptive Boosting.
- In AdaBoost, generally, the algorithm used for training the individual models in the sequence is the Decision Tree Algorithm.
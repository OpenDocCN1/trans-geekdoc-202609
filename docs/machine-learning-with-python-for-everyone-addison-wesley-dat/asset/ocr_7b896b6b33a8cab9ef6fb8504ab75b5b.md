# 8.8.3 Exercises

Here are some questions to keep you up at night:

+   1. Under what scenarios would an identifying variable, such as a unique number for each day, be *useful* for learning a target value? How could we apply it when we need to predict truly never-seen data—beyond even a hold-out test set?
+   2. Play around with SVM boundaries and example points. Make a few positive and negative examples—you can color them red and blue if you like. Make some patterns with the examples. Now, graph and look at the resulting linear boundaries that get created when you train an SVM. How do the boundaries change as you go from well-separated classes to having outliers across the obvious separation?
+   3. Compare the runtimes of of *NuSVC* and *SVC* under different learning scenarios and parameters.
+   4. Compare the DA methods with 20 repeated train-test splits. Use the same TTSs for each method. Count up the winners. Try with a different dataset.
+   5. You now have a bigger toolbox. Try to find better predictive models of the student data from the end of Chapter 6.
+   6. Our examples of bias and variance with SVCs were a bit weak. If you want to see very clear examples of bias-variance—overfitting and underfitting—redo those examples with a *Gaussian kernel*. Don't know what that is? Stay tuned or turn to Chapter 13.
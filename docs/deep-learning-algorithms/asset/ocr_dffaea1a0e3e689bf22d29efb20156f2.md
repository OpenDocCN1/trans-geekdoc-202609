The model figure of SVM [43] [44] [45] is shown in Figure 5. SVM is essentially the classifier for two types. Solving multiple classification problems needs to make more appropriate classifier.

There are two main methods for SVM to structure the classifier for multiple classifications. One is the direct method, namely modify the objective function to use an optimization problem to solve the multiple classification parameters. This method is of high computational complexity. Another method is the indirect method. Combining multiple two-classifier constructs multiple classification classifiers.

![](bbox=[0.2, 0.305, 0.8, 0.655])

# Figure 5. Support Vector Machine (SVM).

The method has two ways:

+   - One-Against-One: Build a hyper-plane between any two classes, to the problem of k classes needing to build k×(k−1)/2 classification planes.
+   - One-Against-the-Rest: The classification plane is built between one category and other multiple categories, to the problem of k classes only needing to build k classification planes.

We will use two methods of “One-Against-One” and “One-Against-the-Rest” for the experiment and choose the method with better effect to construct the multiple classification classifiers of SVM.
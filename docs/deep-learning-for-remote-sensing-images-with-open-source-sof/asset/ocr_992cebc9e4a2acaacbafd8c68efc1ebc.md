(training data and validation data), the validation step of the **Tensorflow-ModelTrain** application consists of computing the following metrics:

+   - Confusion matrix
+   - Overall accuracy index
+   - Kappa index
+   - For each class:
+     - Precision
+     - Recall
+     - F-Score

Depending on the placeholder names of the sources used for training, and the names of the sources used for evaluation, the application to detect which source is used as input of the model, or as a baseline to compute evaluation metrics, is explained in figure 5.3.

![](bbox=[0.1, 0.52, 0.9, 0.7])

# FIGURE 5.3

Computation of classification metrics, performed separately on the training dataset and validation dataset.

The application parameters are the following:

+   - **training.source1** is the parameter group for the first source, i.e. image patches (for learning)
+     - **training.source1.il** is the input image filename
+     - **training.source1.patchsizex** is the patch width
+     - **training.source1.patchsizey** is the patch height
+     - **training.source1.placeholder** is the name of the placeholder for the image patches
+   - **training.source2** is the parameter group for the second source, i.e. label patches (for learning)
improved by color space conversion, contrast enhancement, denoising, and deblurring. The exact area of the skin disease is separated from the healthy skin by applying different techniques of segmentation which improves the recognition performance. The segmented skin disease areas are employed for extracting the hand-crafted features. These features are utilized by a machine learning-based classifier such as SVM, KNN, etc. to carry out the recognition and classification task. The CNN-based models have achieved better performance as they are trained using a larger dataset. CNN-based models can be treated either as the end-to-end classifiers or only as the feature extractors. Then performance of the system for segmentation and classification tasks can be evaluated by different metrics usually obtained from the entries of the confusion matrices.

To understand all the steps and concepts related to skin disease recognition at a more intimate level, we implemented them by hand using different libraries of OpenCV, Scikit-learn, Keras, and TensorFlow in Python.

# 5.9 EXERCISES

+   1. For the given R, G, B matrices of a 3 x 3 image in Figure 5.35, calculate the grayscale values of the corresponding elements based on the weighted method.

![](bbox=[0.285, 0.445, 0.715, 0.545])

Figure 5.35 R, G, and B matrices for a 3 x 3 image.

+   2. In Figure 5.36, X is the input image matrix and h is the kernel of a convolutional layer. (a) Compute the pixel value of the output image by convolving the input image with the kernel with a stride of 1 and 2. (b) Repeat the process with considering zero-padding.

![](bbox=[0.355, 0.705, 0.645, 0.8])

Figure 5.36 Input image of X to be convolved with the kernel of h.

+   3. For the confusion matrix of multi-class classification given in Figure 5.37, computes the average evaluation metrics of accuracy, sensitivity, specificity, precision, and F1-Score.
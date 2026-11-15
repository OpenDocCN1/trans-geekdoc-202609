Planes and Hyperplane: In one dimension, a hyperplane is called a point. In two dimensions, it is a line. In three dimensions, it is a plane and in more dimensions we call it a hyperplane.

![](bbox=[0.255, 0.175, 0.705, 0.435])

Kernel: A kernel is a method of placing a two dimensional plane into a higher dimensional space, so that it is curved in the higher dimensional space. (In simple terms, a kernel is a function from the low dimensional space into a higher dimensional space.)

# Kernel Trick

![](bbox=[0.12, 0.59, 0.88, 0.75])

After understanding the above it is now easier to relate and understand the Kernel Trick. We now know that SVM works better with two dimensional space which are linearly separable.

However, for a non-linear data SVM finds it difficult to classify the data. The easy solution here is to use the Kernel Trick. A Kernel Trick is a simple method where a Non Linear data is projected onto a higher dimension space so as to make it easier to classify the data where it
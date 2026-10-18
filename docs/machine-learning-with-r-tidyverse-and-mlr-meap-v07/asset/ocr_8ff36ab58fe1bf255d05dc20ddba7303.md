# Linear discriminant analysis vs. principal component analysis

If you’ve come across principal component analysis (PCA) before, you might be wondering how it differs to linear discriminant analysis (LDA). PCA is an unsupervised learning algorithm for dimension reduction, meaning that, unlike LDA, it doesn’t rely on labeled data.

If you’re unfamiliar with PCA, don’t worry! You’ll learn about it in depth in chapter 13.

If you want to reduce the dimensionality of data with labeled class membership, you should typically favor LDA over PCA. If you want to reduce the dimensionality of unlabeled data, you should favor PCA (or one of the many other dimension reduction algorithms we’ll discuss in part 4 of the book).



Discriminant analysis can handle classification problems with more than two classes. But how does it learn the best axis in this situation? Instead of trying to maximize the separation between class centroids, it maximizes the separation between each class centroid and the grand centroid of the data (the centroid of all the data, ignoring class membership). This is illustrated in figure 5.5. Where we have two continuous measurements made on cases from three classes. The class centroids are shown with triangles and the grand centroid is shown by a cross.

LDA first finds the axis that best separates the class centroids from the grand centroid that minimizes the variance of each class along it. Then, LDA constructs a second discriminant function which is orthogonal to the first. This simply means the second discriminant function must be perpendicular to the first (at a right angle in this 2D example).

The number of discriminant functions will be whichever is smaller: the number of classes - 1, or the number of predictor variables.
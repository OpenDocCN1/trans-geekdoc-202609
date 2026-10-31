The working of the K-NN algorithm is explained in the following steps:

+   - Choose the number K of the neighbors;
+   - Calculate the Euclidean distance between K of your closest neighbors;
+   - Based on the Euclidean distance, select the K closest neighbors;
+   - Count how many data points there are in each category among the k neighbors;
+   - Assign the newly acquired data points to the category with the most neighbors;
+   - Finally, our test machine learning model is getting ready.

The K-NN approach is simple to implement and robust to noisy training data. As a result, it may be more successful if the training data is large. However, the main downside of this method is that it requires continual determination of the value of K, which might be challenging at times. Furthermore, the calculation cost is high because it takes time to calculate the distance between data points for all training samples.

# 6.5.3 SVM ALGORITHM

The support vector machine (SVM) algorithm is another important and most frequently used algorithm in many recent machine-learning-based applications. It’s a supervised ML algorithm that can handle regression and classification tasks. However, it is mostly used to tackle classification problems. The value of each feature is the value of a specific coordinate in the SVM methodology, and each data item is represented as a point in n-dimensional space (Zhao et al., 2020), where n is the number of distinct features. Then we locate the hyper-plane that clearly separates the two classes to complete classification. Figure 6.9 shows the graphical representation of the SVM algorithm.

Both linearity and non-linearity input can be classified using the SVM method. It starts by mapping each data point through an n-dimensional attribute vector, with n denoting the total number of attributes. The hyperplane that divides these data components into two groups is then found, with the minimum separation for both categories maximized and classification errors reduced. The selection hyperplane’s length and the class’s neighboring occurrence define the least closeness for a grouped class. Each feature vector is first displayed as a point in an n-dimensional space, with each feature’s value corresponding to a specific coordinate. To finish the categorization, we must first find the hyperplane that divides the two categories by the greatest distance.
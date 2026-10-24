![](bbox=[0.32, 0.11, 0.69, 0.31])

# FIGURE 11.20 Learning a model for the normal class.

Support Vector Data Description (SVDD), it seeks to find a minimum hypersphere that contains all the normal tuples.

Example 11.23. Outlier detection using a one-class model. Consider the training set shown in Fig. 11.20, where white points are samples labeled as “normal” and black points are samples labeled as “outlier.” To build a model for outlier detection, we can learn the decision boundary of the normal class using classification methods such as SVM (Chapter 7), as illustrated. Given a new object, if the object is within the decision boundary of the normal class, it is treated as a normal case. If the object is outside the decision boundary, it is declared an outlier.

An advantage of using only the model of the normal class to detect outliers is that the model can detect new outliers that may not appear close to any outlier objects in the training set. This occurs as long as such new outliers fall outside the decision boundary of the normal class.

The idea of using the decision boundary of the normal class can be extended to handle situations where the normal objects may belong to multiple classes. For example, an electronics store accepts returned items. Customers can return items for a number of reasons (corresponding to class categories) such as “product design defects” and “product damaged during shipment.” Each such class is regarded as normal. To detect outlier cases, the store can learn a model for each normal class. To determine whether a case is an outlier, we can run each model on the case. If the case does not fit any of the models, then it is declared an outlier.

Classification-based methods and clustering-based methods can be further combined to detect outliers in a semisupervised learning way.

Example 11.24. Outlier detection by semisupervised learning. Consider Fig. 11.21, where objects are labeled as either “normal” or “outlier” or have no label at all. Using a clustering-based approach, we find a large cluster, C, and a small cluster, C1. Because some objects in C carry the label “normal,” we can treat all objects in this cluster (including those without labels) as normal objects. We use the one-class model of this cluster to identify normal objects in outlier detection. Similarly, because some objects in cluster C1 carry the label “outlier,” we declare all objects in C1 as outliers. Any object that does not fall into the model for C (e.g., a) is considered an outlier as well.
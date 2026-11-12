There are the following two types of variability and one type of similarity in the pattern class:

+   - Intra-class variability
+   - Inter-class variability

Machine learning algorithms have to deal with these variabilities and similarities.

# Intra-class variability

It refers to the deviations in the particular class score for a specific object which is not a part of the systematic difference. So, basically, it is within the class variability. It can be used to map different types of objects. If we talk about land covers, then bare soil, forests, and rocks can be mapped using intra-class variability. It is the variation that exists between all the samples of a particular class that are used to learn the machine.

Intra-class variability uses a tool named as **feature space** which predicts the patterns according to their features by using spectral signatures. So, according to the specific requirement, an appropriate feature space can be chosen.

# Inter-class variability

Inter-class variability means the variability among the different types of classes in a dataset. It can be used in cases where one needs to separate different classes that exist in the dataset. Also, the accuracy of the classification of objects depends upon inter-class variability. *Figure 1.2(a)* represents the patterns having low inter-class and high intra-class variability, whereas *Figure 1.2(b)* represents the patterns having low intra-class and high inter-class variability. For an ideal clustering algorithm, the intra-class variability should be minimum, whereas inter-class variability should be maximum. This is an important criterion for getting classes of different patterns. In classification, there exists a labeled dataset, so inter and intra-class variability does not exist in supervised learning. The inter-class and intra-class variability is dependent on a distance metric.

# Inter-class similarity

In inter-class similarity, the data is similar, almost nearest to each other and belongs to the same cluster. The outcomes are calculated as the ratio of the total summation distance to the summation of all the distances within one cluster of the dataset. Inter-class similarity can be seen in *figure 1.3*:
# # Similarity Learning

In this chapter, we will learn about similarity learning and learn various loss functions used in similarity learning. Similarity us useful when the dataset is small per class. We will understand different datasets available for face analysis and build a model for face recognition, landmark detection. We will cover the following topics in this chapter:

+   - Different algorithms for similarity learning
- Various loss functions used for similarity learning
- A variety of scenarios in which such models are used
- The complete process of face recognition

# # Algorithms for similarity learning

**Similarity learning** is the process of training a metric to compute the similarity between two entities. This could also be termed as metric learning, as the similarity is learned. A metric could be Euclidean or cosine or some other custom distance function. Entities could be any data such as an image, video, text or tables. To compute a metric, a vector representation of the image is required. This representation can be the features computed by a CNN as described in Chapter 3, Image Retrieval. The CNN that was learned for object classification could be used as the vector to compute the metric. The feature vector obtained for image classification would not be the best representation of the task at hand. In similarity learning, we find out CNNs that generate features trained for a similarity learning task. Some applications of similarity learning are given here:

+   - Face verification for biometrics to compare two faces
- Visual search of real-world objects to find similar products online
- Visual recommendation of products that are similar in some attributes
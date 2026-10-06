# CHAPTER 7. ENCODING BEHAVIORAL DATA

| Word | Count |
|---|---|n| body | 1 |
| colors | 0 |
| diagnosis | 2 |
| health | 1 |
| hospital | 1 |
| idea | 0 |
| music | 0 |
| painting | 1 |
| patient | 0 |
| style | 0 |
| treatment | 2 |

| Word | Count |
|---|---|n| body | 1 |
| colors | 2 |
| diagnosis | 0 |
| health | 0 |
| hospital | 1 |
| idea | 1 |
| music | 1 |
| painting | 2 |
| patient | 0 |
| style | 1 |
| treatment | 0 |

a) BoW of medical document   b) BoW of art document

Figure 7.14: Table of two documents as BoW.

(document) can be decomposed into smaller elements (words) by identifying objects like trees, chairs, cars, cashiers, etc. In this case, instead of we bags of objects but the idea is the same. The object identification part can be done in a supervised manner where there is a classifier that assigns labels to objects.

Using a supervised approach can work in simple cases but is not scalable for more complex ones. Why? Because the classifier would need to be trained for each type of object. Furthermore, those types of objects need to be manually defined beforehand. If we want to apply this method on schemes where most of elements do not have a corresponding label in the object classifier we will be missing a lot of information and end up with incomplete word count tables.

A possible solution is to use, use an unsupervised approach. The image scene can be divided into squared (but not necessarily) patches. Conceptually, each patch may match an independent object (a tree, a chair, etc.). Then, feature extraction can be performed on each patch so ultimately patches are encoded as feature vectors. Again, each feature represents an individual object inside the complex scene. At this point, those feature do not have a label so we can build the BoW (table counts) for the whole scene. Then, how are unlabeled feature vectors useful? We could use a pre-trained classifier to assign them labels —but we are relying into the supervised approach along with its aforementioned limitations. Instead, we can use an unsupervised approach for, example, K-means! which was presented in chapter 6.

We can cluster all the unlabeled feature vectors into k groups where k is the number of possible unique labels. After the clustering, we can compute the centroid of each group. To assign a label to an unlabeled feature vector, we can compute the closest centroid and use its
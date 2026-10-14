
This type of algorithm has numerous other applications. In medical image analysis, it is used to distinguish between areas of different tissues and to spot cancers and lesions. On video recordings, it is used to isolate an object or individual under surveillance. On e-commerce sites, it is used to make customer recommendations based on products “similar to” the ones you have already ordered.

## [LET’S DO SOME SORTING](#contents.xhtml#toc2_85)

Grouping and separating objects based on shared characteristics, whether animals, gene sequences, images, or books, is done using particular algorithms.

The general idea is to give the computer a large amount of data describing the objects’ characteristics and to ask it to classify it all like a big boy. This is referred to as “cluster analysis” or “clustering.” It consists of forming clusters of similar objects. Each cluster must contain objects similar to each other and different from objects of other clusters.

The result of this operation depends on several things, starting with the number of clusters you want to make. In the clustering example below, we’ve separated the animals into carnivores and herbivores:

![image](images/inline9_2.jpg)

However, if we have to make three clusters now, we probably need to think differently. For example, we could also group our animals by size:

![image](images/inline9_3.jpg)

As you can see, our clusters also depend on the characteristics of the objects. For animals, besides their food type or size, we could also consider the number of limbs, habitat, or, why not, how fast they can travel. Each characteristic could lead to a different cluster! Computer scientists call these characteristics “features,” and they develop clustering algorithms that consider all the features at the same time in order to build the best cluster possible. Naturally, this requires a lot of calculations. Each object’s features have to be compared to the features of all the other objects. This is precisely what computers are made for.

The algorithms that do this type of work are called `unsupervised cluster analysis algorithms`. As their name suggests, they cluster objects together based on their features, with no hint of the expected result.

## [IT’S ALL A MATTER OF DISTANCE](#contents.xhtml#toc2_86)

There are as many unsupervised cluster analysis algorithms as there are ways of clustering objects. For example, imagine you must divide Christmas presents among several children. You might want each child to open the same number of presents. In this case, your clustering algorithm must ensure that each cluster contains the exact same number of presents. On the other hand, if you want each child to receive presents of a similar value, regardless of how many, you’ll choose a different algorithm to ensure the presents are distributed fairly. Or, if you want each child to receive a big present, you’ll apply yet another clustering algorithm.

Each clustering algorithm does not sort the presents: they compare the data to cluster what they have in common. Each one has a different way of clustering a specific object’s data. These algorithms have strange names: `k-means`, `DBSCAN`, `expectation maximization`, `SLINK`, and others. Each one has its own way of forming clusters.

All these algorithms compare the objects’ features to form clusters of objects that are similar to each other but different from other clusters. Naturally, these characteristics (for example, the animal’s size, what it eats) are represented by numbers in the computer. These are the `features`.

To describe these features, we need a computer scientist whose role is to define, for each feature, how to represent them numerically. While it’s pretty easy to do this for size, choosing a number for features such as diet, habitat, or coat raises more questions. Indeed, the computer scientist must determine the distance among the different values to allow the algorithm to compare the objects. For example, is an animal with feathers “closer” to an animal with hair or an animal with scales?

Using a number to represent a measurement of distance between feature values is the basis for a great number of clustering algorithms.

![image](images/inline9_4.jpg)

In this kind of representation, each feature corresponds to a dimension in a multidimensional space, and the objects to be clustered constitute just as many points in this space. It’s as if you placed your animals in the space based on their features so you could measure the distance separating them. But you have to imagine that this space doesn’t just have two or three dimensions like the image above, but probably hundreds. There are as many dimensions as there are features to study!

This mathematical modeling is difficult to grasp. In any case, bear in mind that the points’ relative position in the space determines the distances between the objects to be clustered. This is what will guide the clustering algorithm and determine how it regroups them. By representing the clustering problem as a geometry one, computer scientists have been able to build the majority of today’s modern clustering algorithms.

## [STARTING OVER AGAIN AND AGAIN](#contents.xhtml#toc2_87)

The `k-means` algorithm, invented by Hugo Steinhaus in 1957, illustrates the use of this multidimensional space very well.

For it to work, you have to tell the machine how many clusters you want: this is the value `k`. The computer, then, chooses `k` objects from your list (it usually takes the first objects on the list, no questions asked). Then, it builds `k` clusters containing just one object each. This is just the beginning. We still have to cluster all the objects.

By using each object’s position in the space, corresponding to the different features, the algorithm calculates each object’s distance from the first `k` objects chosen. This algorithm then places each object in the cluster associated with the initial object that it is closest to. Ultimately, we get `k` clusters, each one of a different size. Each cluster contains the objects that were closest to one of the initially chosen objects.

This first attempt at clustering is most often of very bad quality. Imagine, for example, that we need to separate animals into two clusters and we unfortunately chose the cat and the lion first.

![image](images/inline9_5.jpg)

The cow, which is going to be in one of these two clusters, is farther from the cat and lion than the cat and lion are from each other!

For this reason, the `k-means` algorithm doesn’t stop here. By using the distance function, it calculates a “mean object” for each cluster, which is the mean of all the features of all the objects in the cluster. This object doesn’t actually exist (imagine the mean of a cow and a cat), but that doesn’t really matter: it’s simply a way of having a reference point in a multidimensional space to build a cluster. Thus, we have `k` “mean objects” for `k` clusters.

Now, we just have to start clustering all over again! The algorithm takes each object one by one, measures the distance between it and these “mean objects,” and then rebuilds the clusters by associating each object with the closest mean point. With our animals, the mean point of the cluster not containing the cow is going to “catch” the missing animal (cat or lion), while the cow will remain near its mean point. In this way, we get `k` new clusters, which we can hope are a little better than the previous ones. For instance, the first `k` animals can now belong to the same cluster, which was impossible in the first round of the algorithm (remember the cat and the lion.)

However, this isn’t the end of the road for our algorithm. It calculates the mean of each cluster again and hits the road again. This continues until the clusters can no longer be modified.

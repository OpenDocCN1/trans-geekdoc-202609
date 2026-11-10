
## K-Means Clustering Example

Can we have a look at the dataset? (see [Table 11.1](#c11.xhtml#t11.1))

[**Table 11.1**](#c11.xhtml#re_t11.1) Dataset Considered for Clustering

| Objects || `X` || `Y` || `Z` |
| --- | --- | --- | --- |
| `O1` || 1 || 4 || 1 |
| --- | --- | --- | --- |
| `O2` || 1 || 2 || 2 |
| `O3` || 1 || 4 || 2 |
| `O4` || 2 || 1 || 2 |
| `O5` || 1 || 1 || 1 |
| `O6` || 2 || 4 || 2 |
| `O7` || 1 || 1 || 2 |
| `O8` || 2 || 1 || 1 |

Initially, we must take any two centroids, `C1` and `C2`. Next question: why select just two centroids? Since the `K` value is 2, the number of centroids chosen is also 2. Once chosen, the data points get tagged to a particular cluster based on the distance. It is time to start with the computation:
* First centroid = object 2 (`O2`); this will be cluster 1 (`O2` = first centroid = 1, 2, 2)
* Second centroid = `O6`; this will be cluster 2 (`O6` = second centroid = 2, 4, 2)

Can we choose any object as the centroid? This is a very common question – any object can become a centroid.

How do we measure distance? There is a formula, which comes to our rescue here.
* `d=|x2–x1|+|y2–y1|+|z2–z1|`
People call `d` the Manhattan distance.
* `d` is the distance between two objects.
* Remember – any object has `X`, `Y` and `Z` coordinates according to the dataset! So, the task is simple.

It is time to reconstruct the table and one must use the distance between each object and the centroids chosen (see [Table 11.2](#c11.xhtml#t11.2)).

[**Table 11.2**](#c11.xhtml#re_t11.2) Distance from `C1` and `C2`

| Objects || `X` || `Y` || `Z` || Distance from `C1` (1,2,2) || Distance from `C2` (2,4,2) |
| --- | --- | --- | --- | --- | --- |
| `O1` || 1 || 4 || 1 || `D= |1−1|+|4−2|+|2−1|= 3` || `D= |1−1|+|4−2|+|2−1|=2` |
| --- | --- | --- | --- | --- | --- |
| `O2` || 1 || 2 || 2 || `D= |1−1|+|2−2|+|2−2|=0` || `D= |2−1|+|4−2|+|2−2|= 3` |
| `O3` || 1 || 4 || 2 || `D= |1−1|+|4−2|+|2−2|=2` || `D= |2−1|+|4−4|+|2−2|=1` |
| `O4` || 2 || 1 || 2 || 2 || 3 |
| `O5` || 1 || 1 || 1 || 2 || 5 |
| `O6` || 2 || 4 || 2 || 3 || 0 |
| `O7` || 1 || 1 || 2 || 1 || 4 |
| `O8` || 2 || 1 || 1 || 3 || 4 |

Like `O1`, `O2` and `O3`, the rest of the calculations are carried out to compute the distance from `C1` and `C2`. One can refer to [Table 11.2](#c11.xhtml#t11.2) to get a clearer understanding.

The next step is to go ahead with the clustering. How is it achieved? Simple! Based on the distance, one can go ahead with the clustering. Whichever is shorter – say `C1` is shorter than `C2` – for an object, the object falls to `C1`. Hence, the clustering shall look like:

For a clear understanding, the following color guidelines have been followed in [Table 11.3](#c11.xhtml#t11.3). Cluster 1 is represented in green and cluster 2 in red.

[**Table 11.3**](#c11.xhtml#re_t11.3) Clustering – the Next Level

| ![](images/Table11.3a.jpg)  |
| --- |
| ![](images/Table11.3b.jpg)  |
| ![](images/Table11.3c.jpg)  |

To clarify, one can refer to [Table 11.4](#c11.xhtml#t11.4) as presented below.

[**Table 11.4**](#c11.xhtml#re_t11.4) Clusters 1 and 2

| ![](images/Table11.4.jpg)  |
| --- |
![](images/inline11.12.jpg)

The next round (iteration) of clustering then has to be done (see [Table 11.5](#c11.xhtml#t11.5)).

[**Table 11.5**](#c11.xhtml#re_t11.5) Reiterated Results

| ![](images/Table11.5.jpg)  |
| --- |

Now, the new clusters will be:

![](images/inline11.10.jpg)

So, we can stop here. No updates in the centroids or changes in the cluster grouping have been observed. Hence, this is the correct clustering.

This is how K-means clustering works.

One can listen to the lecture on K-Means clustering by the authors at the video link at https://youtu.be/Fuq9Dw43co0

## 11.3 Implementation of K-Means Clustering

K-means clustering has been carried out on the mall dataset, where we have variables on the customers such as age, gender, annual income and spending ability. Based on these entries, our model will be classifying the customers. For the reader to understand what the dataset looks like, a sample screenshot of the dataset is presented in [Figure 11.2](#c11.xhtml#f11.2).

![Figure 11.2 Mall dataset – a quick reference.](images/fig11.2.jpg)

[**Figure 11.2**](#c11.xhtml#re_f11.2) Mall dataset – a quick reference.

With the Intel oneAPI and the optimized associated libraries, it becomes easy for software developers to build solutions. One can read through the code below code, step by step, to understand how the implementation has been done effortlessly. The code is also made available in the GitHub with the dataset at: https://github.com/shriramkv/MachineLearningwithoneAPI.

![](images/inline11.1.jpg)![](images/inline11.2.jpg)![](images/inline11.3.jpg)

One can visualize the clusters from the results obtained below (see [Figure 11.3](#c11.xhtml#f11.3)).

![Figure 11.3 The clusters.](images/fig11.3.jpg)

[**Figure 11.3**](#c11.xhtml#re_f11.3) The clusters.

## 11.4 Principal Component Analysis (PCA)

Now that we know the complete working of the K-means clustering algorithm, let’s move on to understanding one of the most important concepts in machine learning, principal component analysis (PCA).

Have you heard about the Curse of Dimensionality? Yes, I am talking about a curse ![](images/inline11.11.jpg). Let’s try to understand, with an example, what this is and how is it relevant to the topic that we are talking about!

Consider you are a zoophile, a lover of animals. Say that you are so fond of animals that you live in a forest area (in a treehouse) so that you can enjoy the animals in their natural habitat, rather than caging them.

One day, while enjoying nature and trekking over a mountain, you find a beautiful snail moving over a tree trunk. You get yourself lost in enjoying the snail moving in one direction (one-dimensional movement) (see [Figure 11.4](#c11.xhtml#f11.4)).

![Figure 11.4 One-dimensional movement.](images/fig11.4.jpg)

[**Figure 11.4**](#c11.xhtml#re_f11.4) One-dimensional movement.

Next, you are distracted by a pack of pups, running around in a distant field plane (two-dimensional movement). Even though you are happy to enjoy the sight, fear strikes as you realize that they are not puppies but fox cubs ![](images/inline11.11.jpg)and you resume trekking (see [Figure 11.5](#c11.xhtml#f11.5)).

![Figure 11.5 Two-dimensional movement.](images/fig11.5.jpg)

[**Figure 11.5**](#c11.xhtml#re_f11.5) Two-dimensional movement.

Finally, you reach the top of the mountain, and lay down looking at the blue sky, enjoying the birds fly (three-dimensional movement) (see [Figure 11.6](#c11.xhtml#f11.6)).

![Figure 11.6 Three-dimensional movement.](images/fig11.6.jpg)

[**Figure 11.6**](#c11.xhtml#re_f11.6) Three-dimensional movement.

So, you enjoy the sunset and start back to your treehouse! Say, on your way back, you encounter some energy beings (aka ghosts ![](images/inline4.1.jpg)), then of course you have even encountered a higher-dimensional being ([Figure 11.7](#c11.xhtml#f11.7)).

![Figure 11.7 Higher-dimensional movement.](images/fig11.7.jpg)

[**Figure 11.7**](#c11.xhtml#re_f11.7) Higher-dimensional movement.

However, to cut a long story short, you scare the ghost and it disappears. Hurray! You reach your treehouse safe and sound ![](images/inline4.1.jpg).

Now, let’s connect this small story to our concept of the “Curse of Dimensionality.” It’s very simple. Just imagine, if you are trying to catch a snail which moves in one dimension, of course this would have been the easiest task. However, if you are trying to catch the pups running in two dimensions, yes, you could have done that, of course but it is not such an easy task as catching the snail. Then, just imagine, you are a hunter trying to catch the birds flying in three dimensions; oh my God, only that hunter knows the pain. Finally, if you are trying to catch the ghost, our higher-dimensional being, of course, that would be the toughest job of all.

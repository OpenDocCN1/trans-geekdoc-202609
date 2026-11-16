
Despite the ability of grouping similar data into the clusters, the algorithm is not capable to add levels to the group. This unsupervised learning algorithm knows only about data instances that are similar. However, this class of algorithm cannot identify the meaning of the group.

The applications of unsupervised machine learning are given below:

- Banking Sector: In this scenario, the unsupervised machine learning is used to segment customers using behavioral characteristics to develop multiple segments through clustering.

- Healthcare Sector: In the healthcare sector, unsupervised machine learning can be used to categorize MRI data using either normal or abnormal images. The system uses unsupervised learning techniques to build a model that learns from different features of images to recognize a pattern.

- Retail Sector: The unsupervised machine learning approach can be used in the retail sector to help customers to find the right products based on customers' past purchasing history. The system does this by building a collaborative filtering model based on the history of past purchasing.

There are various unsupervised learning algorithms are reported in the literature. We briefly discuss some of the most popular algorithms next.

### K-Means Algorithm

K-means performs the division of objects into clusters that are similar between them and are dissimilar to the objects belonging to another cluster. If we have some unlabeled data, we can cluster it with this algorithm. The term K is a number, therefore, we need to tell the system how many clusters are needed to perform.

To get an insight into this algorithm, let us consider an example of a cricket match. The batsman ran more but get less wickets. In contrast, the bowlers run less but get the wicket most. In Figure 7.11(a), we plot runs against wickets. Figure 7.11(b) shows the clustering model of Figure 7.11(a).

![](img/617e854c2620a5a4bed0116cef33155a_206_0.png)

Figure 7.11 Runs vs. wickets

![](img/617e854c2620a5a4bed0116cef33155a_207_0.png)

Figure 7.12 Relocation of the centroids

In the first step, we need to select the number of clusters that we want to identify in the dataset. This is the “K” in K-means clustering. For this case, let us consider, K = 2, and take two random points on the graph (Figure 7.12(a)). We then determine the distance of each of the data points from each of the randomly assigned points. The points with less distance are assigned for the one type of data that is represented in Figure 7.12(b).

The next step is to determine the actual center point of the actual center points of these two clusters. This process is continued until the relocation of the centroid is getting fixed as shown in Figure 7.12(c), and the final cluster is shown in Figure 7.12(d). It is found that the algorithm is converged.

Assuming we have inputs (x1, x2, x3,...) and we are splitting it into k clusters. The relocation process of centroid can be divided into four steps which are described below:

- Step 1: The first step is to pick k random points as cluster centers that called centroids. Let’s assume these are c1, c2, c3,...ck and we can say that

C = c1, c2, c3, ..., ck (7.3)

Where, C is the set of all centroids.

- Step 2: In this step, we assign each data point to closest center, this is done by calculating Euclidean distance

arg min_{c_i \in C} dist (c_i, x)^2 (7.4)

- Step 3: In this step, we find the new centroid by taking the average of all the points assigned to that cluster.

c_i = \frac{1}{|S_i|} \sum_{x_i \in S_i} x_i (7.5)

where, S_i is the set of all points assigned to the i th cluster.

- Step 4: In this step, we repeat step 2 and step 3 until none of the cluster assignments change that means until our clusters stable, we repeat the algorithm.

The practical applications of the K-Means algorithms include

- Grouping students based on their grades/scores
- The search result is grouped to form clusters
- Wireless sensor networks where the clustering algorithms play a big role in finding a cluster head that collects all the data of the respective cluster.

### Hierarchical Clustering Algorithm

The method of dividing the objects into clusters that are similar between them and are dissimilar to the objects belonging to another cluster. Hierarchical clustering is separating data into different groups based on some measure of similarity. There are two types of Hierarchical clustering: one is “Agglomerative” which brings things together and the other one is “Divisive” which divides things apart. The Agglomerative clustering follows a bottom-up approach whereas Divisive clustering is a top-down approach (Figure 7.13).

Suppose we have few points on a plane as shown in Figure 7.14(a) and we try to find the least distance between two data points to form a cluster. After finding the least distance between two points we need to form clusters of multiple points. This is represented in a tree-like structure called Dendrogram. For three sets of clusters shown in Figure 7.14(a), the corresponding Dendrogram figure is shown in Figure 7.14(b). Then for two nearest points, again we make one dendrogram. The process ends when we make one cluster.

Some applications of Hierarchical clustering are given below:

- Widely uses in customer segmentation in super shops.
- It also uses social network analysis to sort what are the items like or dislike the customers more.
- For city planning, this algorithm plays a vital role to separate different zone with one another such as industrial, commercial, residential.

![](img/617e854c2620a5a4bed0116cef33155a_209_0.png)
![](img/617e854c2620a5a4bed0116cef33155a_209_1.png)

Figure 7.13 Agglomerative and divisive algorithms

Figure 7.14 Hierarchical clustering algorithm

### 7.2.2.3 Semi-Supervised Learning Models

The semi-supervised learning model is a combination of supervised and unsupervised learning models. However, in semi-supervised learning models, datasets are divided into two parts: a labeled part and an unlabeled part. This technique is often used when labeling data or collecting tagged data is very difficult or expensive. The portion of tagged data may also be of low quality [25]. For example, if we do medical imaging for cancer, keeping doctors tagged in the datasets is very expensive to work on and also these doctors need to do more urgent work. The doctor has tagged one part of the dataset and left the other untagged. Finally, this machine learning technique has been shown to work well with good precision, even if the dataset is partially labeled. Additionally, unlabeled data is easily accessible and also available in large quantities.

![](img/617e854c2620a5a4bed0116cef33155a_210_0.png)
![](img/617e854c2620a5a4bed0116cef33155a_210_1.png)
![](img/617e854c2620a5a4bed0116cef33155a_210_2.png)
![](img/617e854c2620a5a4bed0116cef33155a_210_3.png)

Figure 7.15 Learning data set of semi-supervised models

Figure 7.15(a) shows some labeled data and supervised learning involves finding a boundary between different types of labeled data (Figure 7.15(b)). On the contrary, for the case of semi-supervised learning, there are both labeled and unlabeled data (Figure 7.15(c)). But the amount of unlabeled data is quite high than the labeled data. Training is performed in such a way that the model could divide them into similar parts (Figure 7.15(d)). In this case, the division is done taking the consideration of labeled data with the availability of unlabeled data.

A popular semi-supervised learning algorithm is described below:

Generative Adversarial Networks: A common training method used in medical software diagnostic with a very small set of labeled data is Generative Adversarial Networks (GAN) which is a type of semi-supervised learning method. From Figure 7.16, it is seen that real samples contain real images that are mixed with some latent space which generates noise. This data is fed into the Generator that generates some fake samples with fake images. Both the real sample and the output of the generator are mixed and compared in Discriminator. The Discriminator passes all the images and fine-tunes and

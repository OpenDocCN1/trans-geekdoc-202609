
random\_state=42: Sets a random seed for reproducibility.

kmeans.fit(X): Fits the KMeans model to the data X, where X is the dataset to be clustered.

wcss.append(kmeans.inertia\_): Appends the WCSS value of the fitted model to the wcss list.

kmeans.inertia\_: Retrieves the WCSS value of the fitted KMeans model.

plt.plot(range(1, 11), wcss): Plots the number of clusters (x-axis) against the corresponding WCSS values (y-axis).

plt.title('The Elbow method'): Sets the title of the plot.

plt.xlabel('Number of Clusters'): Sets the label for the x-axis.

plt.ylabel('WCSS'): Sets the label for the y-axis.

plt.show(): Displays the plot.

The purpose of the "elbow" point in the plot is to indicate the optimal number of clusters, where adding more clusters does not significantly reduce WCSS as seen in Figure 4-6 . Note: The elbow point is often chosen as the point of inflection, where the rate of decrease in WCSS begins to decrease more slowly. It is where the curve starts to bend less abruptly which is number 6 in this context based on the data.

![](OEBPS/image_rsrc573.jpg)

Figure 4-6.

# Training the model

To train the k-means clustering model, we utilize the entire dataset and specify the number of clusters obtained from Figure 4-6 . Figure 4-7 illustrates the process of training the model in this manner.

![](OEBPS/image_rsrc574.jpg)

Figure 4-7.

# Code Explanation

The code snippet initializes and trains a k-means clustering model with 6 clusters using the specified dataset X. It assigns each data point to its corresponding cluster and stores the cluster labels in the variable y_kmeans.

kmeans = KMeans(n_clusters=6, init='k-means++', random_state=42): Initializes a k-means clustering model.

n_clusters=6: Specifies the number of clusters to be created. In this case, the model will attempt to identify 6 clusters in the data.

init='k-means++': Specifies the initialization method for selecting initial cluster centroids. 'k-means++' is a smart initialization technique that helps speed up convergence.

random_state=42: Sets a random seed for reproducibility. It ensures that the initialization of centroids is consistent across runs.

# Predicting with the test data

Figure 4-8 below illustrates how we made predictions using the trained model (kmeans) and the test data (X).

![](OEBPS/image_rsrc575.jpg)

Figure 4-8.

# Code Explanation

y_kmeans = kmeans.fit_predict(X): Fits the k-means model to the data X and assigns each data point to its corresponding cluster.

kmeans.fit(X): Fits the k-means model to the data X, where X is the dataset to be clustered.

kmeans.predict(X): Predicts the cluster labels for each data point in X and assigned to y_kmeans.

# View the predicted outcome in y_kmeans

Figure 4-9 shows what is inside the variable y_kmeans.

![](OEBPS/image_rsrc576.jpg)

Figure 4-9.

Keep in mind that the predicted output indicates clusters numbered from 0 to 5 (which totals 6 when counted from 0 to 5). This means that:

Cluster 1 corresponds to index position 0,

Cluster 2 corresponds to index position 1,

Cluster 3 corresponds to index position 2,

Cluster 4 corresponds to index position 3,

Cluster 5 corresponds to index position 4,

Cluster 6 corresponds to index position 5.

To find the true cluster position, simply add 1 to the index positions.

# Visualize the predicted outcome

Figure 4-10 shows how to go about the implementation.

![](OEBPS/image_rsrc577.jpg)

Figure 4-10.

# Code Explanation

The code snippet in Figure 4-10 creates a scatter plot to visualize the clusters of bank customers based on their annual income and spending score. Each cluster is represented by a different color, and centroids are marked in yellow. This visualization provides insights into customer segmentation and can guide marketing strategies.

Scatter Plots:

plt.scatter(x, y, s, c, label): This function is used to create scatter plots.

x: The x-coordinates of the data points.

y: The y-coordinates of the data points.

s: The size of the markers (optional).

c: The color of the markers (optional).

label: The label for the scatter plot (optional).

Data Plotting:

X[y_kmeans == 0, 0]: Selects the x-coordinates of data points belonging to cluster 1.

X[y_kmeans == 0, 1]: Selects the y-coordinates of data points belonging to cluster 1.

Similarly, X[y_kmeans == 1, 0] and X[y_kmeans == 1, 1] select coordinates for cluster 2, and so on.

Centroid Plotting:

plt.scatter(kmeans.cluster_centers_[:, 0], kmeans.cluster_centers_[:, 1], s=300, c='yellow', label='Centroids'): Plots the centroids of the clusters.

kmeans.cluster_centers_[:, 0]: Retrieves the x-coordinates of the cluster centroids.

kmeans.cluster_centers_[:, 1]: Retrieves the y-coordinates of the cluster centroids.

Plot Customization:

plt.title("Clusters of Bank Customers"): Sets the title of the plot.

plt.xlabel("Annual Income of Bank Customers"): Sets the label for the x-axis.

plt.ylabel("Spending Score (1-100)"): Sets the label for the y-axis.

plt.legend(): Displays the legend with labels for different clusters.

plt.show(): Displays the plot.

Purpose:

The code snippet visualizes the clusters formed by the k-means clustering algorithm along with their centroids.

It helps in understanding the distribution of data points and the separation of clusters based on their features.

The execution of the code in Figure 4-10 will give the output as seen in Figure 4-11 below.

![](OEBPS/image_rsrc578.jpg)

Figure 4-11.

# Interpreting the visualization

Cluster 1: Customers in this cluster earn low annual income but have a high spending score, indicating that they carry out more transactions despite their lower income level.

Cluster 2: Customers in this cluster earn high annual income but engage in fewer transactions at the bank.

Cluster 3: This cluster comprises customers with low annual income who also perform few transactions at the bank.

Cluster 4: Customers in this cluster have high annual income and spend a significant amount.

Cluster 5: These customers have a high average annual income and engage in moderate transactions.

Cluster 6: Customers in this cluster are high earners annually but engage in few transactions at the bank.

From the graph, Kelly's target customers, based on spending behavior and income levels, are likely to be found in Clusters 1, 4, and 5. These clusters represent customers who exhibit favorable spending behavior despite variations in their annual income. Cluster 1 comprises customers with low annual income but high spending scores, Cluster 4 includes high-income customers who spend significantly, and Cluster 5 consists of customers with a high average annual income engaging in moderate transactions. These clusters present opportunities for targeted marketing efforts to maximize engagement and transactions.

# Exporting Data to CSV File.

To export the identified target customers into a CSV file, we first need to adjust the cluster column by adding 1 to show the exact cluster for ease of extraction, as demonstrated in Figure 4-12 .

![](OEBPS/image_rsrc579.jpg)

Figure 4-12.

# Grouping the clusters

After executing the code depicted in Figure 4-12 , the next step involves grouping the clusters. This grouping ensures that all customers belonging to a specific cluster are organized together, facilitating the process of exporting the data. To achieve this, we need to follow the code in Figure 4-13 .

![](OEBPS/image_rsrc57A.jpg)

Figure 4-13.

# Code Explanation

This code snippet groups the data by clusters, assigning each cluster's data to a separate variable. The groupby function organizes the data based on the 'cluster' column. Subsequently, data for each cluster is retrieved using the get_group method and stored in individual variables, such as cluster_1_data, cluster_2_data, and so on.

# Exporting cluster to CSV

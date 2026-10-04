
140 T. P. Fowdur, L. Babooram, M. N-U-Ibn Nazir Rosun and M. Indoondom

To perform Hierarchical clustering in MATLAB, the **linkage** and **cluster** functions are used. The **linkage** function from MATLAB's Statistics and Machine Learning Toolbox is used to generate the hierarchical cluster tree. The syntax of the function is as follows:

```
**Z = linkage(X,method)**
```

The inputs to the function are described below:

- **X:** Data elements.
- **method:** Linkage method ('single', 'complete',...).
The function returns the hierarchical cluster tree in array **Z**.

The **cluster** function from MATLAB's Statistics and Machine Learning Toolbox uses the hierarchical cluster tree obtained from the **linkage** function to cluster the data elements. The syntax of the function is as follows:

```
**c = cluster(Z,'Maxclust',N)**
```

The inputs to the function are described below:

- **Z:** Hierarchical tree.
- **N:** Number of clusters.

The function returns array **c** which contains the cluster assignment for each input data element. The short-hand example may be implemented in MATLAB as follows: First, the weights and mileages of the cars are defined in a matrix using the codes given in Listing 3.4.

# Listing 3.4. Hierarchical clustering- Define input data

| Description |
| :--- |
| Weight = [1835 3600 2372 3086 3504 1970]; % Array with car weights |
| Mileage = [26 15 24 14 18 31]; % Array with car mileages |
| X=[Weight, Mileage]; % Matrix with car information |

The hierarchical cluster tree is then created using the codes in Listing 3.5. The linkage method is set as single linkage.

# Listing 3.5. Hierarchical clustering- Cluster data

```
Z = linkage(X,'single'); % Create Hierarchical cluster tree with using single linkage methodnc = cluster(Z,'Maxclust',2); % The data is clustered in a maximum of 2 groups
```

## Machine Learning Algorithms

The clustered elements are plotted on a 2-D line plot and each element is labelled to identify the cars from the plot using the codes in Listing 3.6. Cars from the same cluster are displayed by data points of the same colour.

# Listing 3.6. Hierarchical clustering- Plot clustering results

```
for a = 1:length(X)
if c(a)==1
    line(X(a),X(2),'marker','color','red') % Plot points in first cluster in red
else c(a)==2
    line(X(a),X(2),'marker','color','blue') % Plot points in second cluster in blue
end
text(Weight, Mileage,{Car A','Car B','Car C','Car D','Car E','Car F});
```

The above code generates the plot given in Figure 3.5. It can be seen that cars A, C and F are grouped in the first cluster and cars B, D and E are grouped in the second cluster. The simulation results are therefore similar to the one obtained by the short-hand calculations.

![](img/2b52fde0e707e8c2f05a10309c3f8982_152_0.png)

Figure 3.5. Hierarchical Clustering- Scatter plot of clustered dataset.

Hierarchical clustering can also be demonstrated in the MATLAB example in Listing 3.7 in which a set of randomly generated 10000 samples are grouped into three clusters using the complete linkage method [17].

142 T. P. Fowder, L. Babooram, M. N-D-Ibn Nazir Rosun and M. Indoonon

# Listing 3.7. Hierarchical clustering- Clustering 10000 samples

```
rng('default'); % For reproducibility
X = rand(10000,3); % Generate dataset to be clustered
Z = linkage(X,'complete'); % The Hierarchical cluster tree is created using the complete
linkage method
c = cluster(X,'Maxclust',3); % The data is clustered in a maximum of 3 groups
scatter3(X(:,1),X(:,2),X(:,3),10,c) % Create scatter plot of the clustered data
```

The scatter plot produced by the codes in Listing 3.7, given in Figure 3.6, shows that the generated data has been clustered into 3 separate clusters (shown in different colours) and that the data in each cluster are closely grouped.

![](img/2b52fde0e707e8c2f05a10309c3f8982_153_0.png)

Figure 3.6. Hierarchical Clustering- Scatter plot of clustered dataset.

### 3.3.1.3. Gaussian Mixture Models

Gaussian mixture models (GMMs) determine clusters such that each cluster is considered to follow a Gaussian distribution. These models use a soft clustering methodology to assign data elements to the clusters. GMMs utilize the Expectation-Maximization technique to determine values for missing variables (mean, covariance and weight) based on the available dataset and then finds the right model parameters [18].

A GMM consisting of M Gaussian distributions can be represented using equation (3.5) [18].

$p(x|\theta) = \sum_{k=1}^{M} w_k p(x|\theta_k) \quad (3.5)$

## Machine Learning Algorithms

Where,

- $w_k$ - Weight of the $k^{th}$ Gaussian distribution.
- $\theta_k$ - Mean ($\mu_k$) and covariance ($\Sigma_k$) of the $k^{th}$ Gaussian distribution: $\theta_k = (\mu_k,\Sigma_k)$
- $p(x|\theta_k)$ - Gaussian density of the $k^{th}$ Gaussian distribution.

The cluster function available from MATLAB's Statistics and Machine Learning Toolbox uses Gaussian mixture distributions to cluster data [19]. The syntax of the function is as follows:

```
idx = cluster(gm,X)
```

The inputs to the function are described below:

- **gm**: Gaussian mixture distribution.
- **X**: Dataset to be clustered.

The function returns array **idx** which contains the cluster assignment for each input data.
Gaussian Mixture Clustering is demonstrated in the below example where a GMM is fitted to a set of randomly generated data so that the latter can be clustered [19].
Two sets of variates that follow a mixture of two bivariate Gaussian distributions are first generated using defined means and co-variances. The two sets of variates are combined to form dataset X and a scatter plot of the latter is generated using the codes in Listing 3.8.

# Listing 3.8. Gaussian Mixture Model- Define variants

```
mu1 = [2 3]; % Mean of the 1st component
sigma1 = [2 0 0 1]; % Covariance of the 1st component
mu2 = [-2 -1]; % Mean of the 2nd component
sigma2 = [1 0 0 1]; % Covariance of the 2nd component
rng('default') % For reproducibility
r1 = mvnrnd(mu1,sigma1,2000); % Generate first set of variates
r2 = mvnrnd(mu2,sigma2,2000); % Generate second set of variates
X = [r1; r2]; % Merge variates to form dataset
figure
scatter(X(:,1),X(:,2),15,'*') % Scatter plot with points of size 15
```

The generated scatter plot is given in Figure 3.7.

144 T. P. Fowdur, L. Babooram, M. N-U-D-Ibn Nazir Rosun and M. Indoonondon

![](img/2b52fde0e707e8c2f05a10309c3f8982_155_0.png)

Figure 3.7. Gaussian Mixture Model-Scatter plot of dataset.

A two-component GMM is fitted to the dataset and is used to cluster the data using the **cluster** function. The clustered dataset is then displayed in a scatter plot, given in Figure 3.8, using the codes given in Listing 3.9.

![](img/2b52fde0e707e8c2f05a10309c3f8982_155_1.png)

Figure 3.8. Gaussian Mixture Model- Scatter plot of clustered dataset.

# Listing 3.9. Gaussian Mixture Model- Cluster data

```
gm = fitgmd(X,2); % Fit 2-components GMM to dataset
idx = cluster(gm,X); % Cluster data
figure;
scatter(X(:,1),X(:,2),idx); % Plot clustered data
legend('Cluster 1', 'Cluster 2', 'Location', 'best');
```

## 3.3.2. Unsupervised Deep Learning Models

### 3.3.2.1. Restricted Boltzmann Machine (RBM)

Restricted Boltzmann Machines (RBMs) are neural network models which can learn key characteristics of the probability distribution of datasets. RBMs consist of visible neurons and hidden neurons, each belonging to a layer. The visible neurons are located in the first layer and correspond to elements of observation whereas the hidden neurons are located in the second layer and correspond to dependencies between these elements of observation [20]. All connections between neurons in RBMs are inter-layer. In other words, no two neurons from the same layer are connected and every neuron in one layer is connected to every neuron in the other layer as illustrated in Figure 3.9.

![](img/2b52fde0e707e8c2f05a10309c3f8982_156_0.png)

Figure 3.9. Restricted Boltzmann Machines architecture.

The energy of a joint configuration of the visible and hidden units (v,h) is given by equation(3.6) [21]:

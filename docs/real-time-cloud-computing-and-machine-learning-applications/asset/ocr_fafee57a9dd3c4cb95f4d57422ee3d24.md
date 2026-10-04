140 T. P. Fowdur, L. Babooram, M. N-U D-Ibn Nazir Rosun and M. Indoondom

To perform Hierarchical clustering in MATLAB, the **linkage** and **cluster** functions are used.The **linkage** function from MATLAB's Statistics and Machine Learning Toolbox is used to generate the hierarchical cluster tree. The syntax of the function is as follows:

```
**Z = linkage(X,method)**
```

The inputs to the function are described below:

+   **X:** Data elements.
**method:** Linkage method ('single', 'complete',...).
The function returns the hierarchical cluster tree in array **Z**.

The **cluster** function from MATLAB's Statistics and Machine Learning Toolbox uses the hierarchical cluster tree obtained from the **linkage** function to cluster the data elements. The syntax of the function is follows:

```
**c = cluster(Z,'Maxclust',N)**
```

The inputs to the function are described below:

+   **Z:** Hierarchical tree.
**N:** Number of clusters.

The function returns array **c** which contains the cluster assignment for each input data element. The short-hand example may be implemented in MATLAB as follows: First, the weights and mileages of the cars are defined in a matrix using the codes given in Listing 3.4.

# Listing 3.4. Hierarchical clustering- Define input data

| Weight = [1835 3600 2372 3086 3504 1970]; % Array with car weights |
| Mileage = [26 15 24 14 18 31]; % Array with car mileages |
| X=[WeightMileage]; % Matrix with car information |

The hierarchical cluster tree is then created using the codes in Listing 3.5. The linkage method is set as single linkage.

# Listing 3.5. Hierarchical clustering- Cluster data

```
Z = linkage(X,'single'); % Create Hierarchical cluster tree with using single linkage methodnc = cluster(Z,'Maxclust',2); % The data is clustered in a maximum of 2 groups
```

NOTE: Screenplots are so named because they resemble a scree slope, the collection of rocks and rubble that accumulates at the foot of a cliff due to weathering and erosion.

## Listing 13.5 Plotting the PCA results

```
install.packages("factoextra")

library(factoextra)

pcaDat <- get_pca(pca)

fviz_pca_biplot(pca, label = "var")

fviz_pca_var(pca)

fviz_screeplot(pca, addlabels = TRUE, choice = "eigenvalue")

fviz_screeplot(pca, addlabels = TRUE, choice = "variance")
```

I’ve condensed the four plots from code listing 13.5 into a single figure (figure 13.8) to save space. When deciding how many principal components to retain, there are a few rules of thumb. One rule of thumb is to keep the principal components that cumulatively explain at least 80% of the variance. Another is to retain all principal components with eigenvalues at least one; the mean of all the eigenvalues is always one, so this results in retaining principal components which contain more information than the average. A third rule of thumb is to look for an "elbow" in the scree plot, and exclude principal components beyond the elbow (although there is no obvious elbow in our example). Instead of relying too much on these rules of thumb, I look at my data projected onto the principal components, and consider how much information I can tolerate losing for my application. If I’m applying PCA to my data before applying a machine learning algorithm to it, I prefer to use automated feature selection methods, like we did in previous chapters, to select the combination of principal components that result in the best performance.

![](img/a22105d68c35e8d5bd3c7bafb4644881_338_0.png)

Figure 13.8 Typical exploratory plots for PCA analysis as supplied by the factoextra package. The top-left plot shows a biplot, combining each case’s component scores with arrows to show the variable loadings. The top-right plot shows the variable loading plot with a correlation circle (the boundary within which the variable loadings must lie). The bottom plots are scree plots showing the eigenvalue (left side) and percentage explained variance (right side).

Finally, let’s plot our first two principal components against each other, and see how well they’re able to separate the genuine and counterfeit bank notes. I first mutate the original dataset to include a column of component scores for PC1 and PC2 (extracted from our pca object using `$x`). I then plot the principal components against each other, and add a color aesthetic for the Status variable.

```r
swissPca <- swissTib %>%
  mutate(PCA1 = pca$x[, 1], PCA2 = pca$x[, 2])

ggplot(swissPca, aes(PCA1, PCA2, col = Status)) +
  geom_point() +
  theme_bw()
```

The resulting plot from code listing 13.6 is shown in figure 13.9. So we started with 6 continuous variables, and condensed most of that information into just two principal components that contain enough information to separate the two clusters of banknotes! If we didn’t have labels, having identified different clusters of data, we would now try to understand what those two clusters were, and perhaps come up with a way of discriminating genuine banknotes from counterfeits.

![](img/a22105d68c35e8d5bd3c7bafb4644881_339_0.png)

Figure 13.9 The PCA component scores are plotted for each case, shaded by whether they were genuine or counterfeit.

## EXERCISE 13.1

Add a `stat_ellipse()` layer to the plot we created in figure 13.9 to add 95% confidence ellipses to each class of banknote.

## The weaknesses of PCA are:

- Mapping from high dimensions to low dimensions cannot be non-linear
- It cannot handle categorical variables natively
- The final number of principal components to retain must be decided by us for the application at hand

## Additional exercise 13.2

Re-run the PCA on our Swiss banknote dataset, but this time set the scale argument to FALSE. Compare the:

- eigenvalues
- eigenvectors
- biplot
- variable loading plot
- screeplot of the PCA we trained on scaled data

## Additional exercise 13.3

Do the same as in 2. again, but this time set the arguments center = FALSE and scale = TRUE

- Dimension reduction is a class of unsupervised learning that learns a low-dimensional representation of a high-dimensional dataset, while retaining as much information as possible
- PCA is a linear dimension reduction technique that finds new axes that maximize the variance in the data. The first of these principal axes maximizes the variance, followed by the second, and the third, and so on, which are all orthogonal to the previously computed axes
- When data are projected onto these principal axes, the new variables are called principal components
- In PCA, eigenvalues represent the variance along a principal component, and the eigenvectors represent the direction of the principal axis through the original feature space

## 13.6 Solutions to exercises

+   1. Add 95% confidence ellipses to the plot of PCA1 vs PCA2

```
ggplot(swissPca, aes(PCA1, PCA2, col = Status)) +
  geom_point() +
  stat_ellipse() +
  theme_bw()
```

+   2. Compare the PCA results when `scale = FALSE`

```
pcaUnscaled <- select(swissTib, -Status) %>%
  prcomp(center = TRUE, scale = FALSE)

pcaUnscaled

fviz_pca_biplot(pcaUnscaled, label = "var")

fviz_pca_var(pcaUnscaled)

fviz_screeplot(pcaUnscaled, addlabels = TRUE, choice = "variance")
```

+   3. Compare the PCA results when `center = FALSE` and `scale = TRUE`

```
pcaUncentered <- select(swissTib, -Status) %>%
  prcomp(center = FALSE, scale = TRUE)

pcaUncentered

fviz_pca_biplot(pcaUncentered, label = "var")

fviz_pca_var(pcaUncentered)

fviz_screeplot(pcaUncentered, addlabels = TRUE, choice = "variance")
```

## Maximizing similarity: t-SNE and UMAP

+   **This chapter covers:**
+   - What is non-linear dimension reduction and why is it important?
+   - What is t-SNE?
+   - What is UMAP?

## 14.1 What is t-SNE?

In the last chapter, I introduced you to PCA as our first dimension reduction technique. While PCA is a linear dimension reduction algorithm (it finds new axes that are linear combinations of the original variables), sometimes the information in a set of variables cannot be extracted as a linear combination of these variables. In such situations, there are a number of non-linear dimension reduction algorithms we can turn to, such as *t-distributed stochastic neighbor embedding* (t-SNE), and *uniform manifold approximation and projection* (UMAP).

The t-SNE is one of the most popular non-linear dimension reduction algorithms. t-SNE measures the distance between each case and every other case in the dataset. By default this distance is Euclidean distance, which is the straight line distance between any two points in the feature space (but we can use other measures of distance instead). These distances are then converted into probabilities. This is illustrated in figure 14.1.

For a particular case in the dataset, the distance between this case and all other cases is measured. Then, a normal distribution is centered on this case, and the distances are converted into probabilities by mapping them onto the probability density of the normal distribution. The standard deviation of this normal distribution is inversely related to the density of cases around the case in question. Put another way, if there are lots of cases nearby (more dense), then the standard deviation of the normal distribution is smaller, but if there are few cases nearby (less dense), then the standard deviation is larger.

After converting the distances to probabilities, the probabilities for each case are scaled by dividing them by their sum. This makes the probabilities sum to one for every case in the dataset. Using different standard deviations for different densities, and then normalizing the probabilities to one for every case, means if there are dense clusters and sparse clusters of cases in the dataset, t-SNE will expand the dense clusters and compress the sparse ones so they can be visualized more easily together. The exact relationship between data density and the standard deviation of the normal distribution depends on a hyperparameter called *perplexity*, which we’ll discuss shortly.

In this section, I’ll show you what t-distributed stochastic neighbor embedding is, how it works, and why it’s useful. t-distributed stochastic neighbor embedding is such a mouthful. I’m so glad people shorten this to "t-SNE" (usually pronounced "tee-snee", occasionally pronounced "tiz-nee"), not least because when you hear someone say it, you can say "bless you", and everyone laughs (at least the first few times).

While PCA is a linear dimension reduction algorithm (because it finds new axes that are logical combinations of the original variables), t-SNE is a non-linear dimension reduction algorithm. It is non-linear, because instead of finding new axes that are logical combinations of the original variables, it focuses on the similarities between nearby cases in a dataset, and tries to reproduce these similarities in a lower-dimensional space. The main benefit of this approach is that t-SNE will almost always do a better job of highlighting patterns in the data, such as clusters, than PCA will. One of the downsides of this approach is that the axes are no longer interpretable, as they don’t represent logical combinations of the original variables.

The first step in the t-SNE algorithm is to compute the distance between each case, and every other case in the dataset. By default this distance is Euclidean distance, which is the straight line distance between any two points in the feature space (but we can use other measures of distance instead). These distances are then converted into probabilities. This is illustrated in figure 14.1.


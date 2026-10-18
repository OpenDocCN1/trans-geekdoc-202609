# 13.6 Solutions to exercises

+   1. Add 95% confidence ellipses to the plot of PCA1 vs PCA2

```
```r
ggplot(swissPca, aes(PCA1, PCA2, col = Status)) +
  geom_point() +
  stat_ellipse() +
  theme_bw()
```
```

+   2. Compare the PCA results when `scale = FALSE`

```
```r
pcaUnscaled <- select(swissTib, -Status) %>%
  prcomp(center = TRUE, scale = FALSE)

pcaUnscaled

fviz_pca_biplot(pcaUnscaled, label = "var")

fviz_pca_var(pcaUnscaled)

fviz_screeplot(pcaUnscaled, addlabels = TRUE, choice = "variance")
```
```

+   3. Compare the PCA results when `center = FALSE` and `scale = TRUE`

```
```r
pcaUncentered <- select(swissTib, -Status) %>%
  prcomp(center = FALSE, scale = TRUE)

pcaUncentered

fviz_pca_biplot(pcaUncentered, label = "var")

fviz_pca_var(pcaUncentered)

fviz_screeplot(pcaUncentered, addlabels = TRUE, choice = "variance")
```
```
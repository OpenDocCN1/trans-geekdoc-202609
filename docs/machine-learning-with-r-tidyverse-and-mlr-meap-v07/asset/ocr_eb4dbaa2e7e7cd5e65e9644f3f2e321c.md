clusters, I suppress the drawing of what would be a very large legend, by adding the line
theme(legend.position = "none").

> **TIP** The `theme()` function allows you to control the appearance of your plots (such as changing background colors, gridlines, font sizes and so on). To find out more, call `?theme`.

# Listing 18.9 Plotting the cluster memberships of each permutation

```
ggplot(swissClustersGathered, aes(Right, Diagonal,
                                  col = as.factor(Cluster))) +
  facet_wrap(~ Permutation) +
  geom_point() +
  theme_bw() +
  theme(legend.position = "none")
```

The resulting plot from code listing 18.9 is shown in figure 18.10. We can see that different combinations of epsilon and minPts have resulted in substantially different clustering models. Many of these models capture the two obvious clusters in the dataset, but most do not.
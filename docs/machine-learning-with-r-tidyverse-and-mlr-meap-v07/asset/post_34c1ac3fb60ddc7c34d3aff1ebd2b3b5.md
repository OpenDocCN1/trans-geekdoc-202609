
![](img/a22105d68c35e8d5bd3c7bafb4644881_351_0.png)

Figure 14.6 The effect of changing max_iter (row facets) and eta (column facets) using the default values of theta and perplexity, on the final t-SNE embedding of the swissTib dataset.

So now that we’re a little more clued up about how t-SNE’s hyperparameters affect its performance, let’s run t-SNE on our Swiss banknote dataset. Just like for PCA, I first select all the columns except the categorical variable (t-SNE also cannot handle categorical variables), and pipe this data into the `Rtsne()` function. I manually set the values of the perplexity, theta, and max_iter hyperparameters (honestly, I rarely alter eta), and set the argument `verbose = TRUE` so the algorithm prints a running commentary on what the Kullback–Leibler divergence is at each iteration.

### Listing 14.1 Running t-SNE

```r
swissTsne <- select(swissTib, -Status) %>%
  Rtsne(perplexity = 30, theta = 0, max_iter = 5000, verbose = TRUE)
```

> **TIP**  By default, the `Rtsne()` function reduces the dataset down to two dimensions. If you want to return another number, you can set this using the `dims` argument.

That didn’t take too long did it? For a small dataset like this, t-SNE takes only a few seconds. But it gets slow quickly (see what I did there?) as the dataset increases in size.

Next, let's plot the two t-SNE dimensions against each other to see how well they separated the genuine and counterfeit banknotes.

As we can't interpret the axes in terms of how much each variable correlates with them, it's common for people to color their t-SNE plots by the values of each of their original variables, to help identify which clusters have higher and lower values. To do this, I first use the mutate_if() function to center the numeric variables in our original dataset (by setting .funs = scale, and .predicate = is.numeric). I include scale = FALSE to only center the variables, not divide by their standard deviations. The reason I center the variables is that I'm going to shade by their value on the plots, and I don't want variables with larger values dominating the color scales (omit this line and see the difference in the final plot for yourself).

Next, I mutate two new columns that contain the t-SNE axes values for each case. Finally, I gather the data so that I can facet by each of the original variables. I plot this data, mapping the value of each original variable to the color aesthetic, the status of each banknote (genuine vs counterfeit) to the shape aesthetic, and facet by the original variables. I add a custom color scale gradient to make the color scale more readable in print.

```r
swissTibTsne <- swissTib %>%
mutate_if(.funs = scale, .predicate = is.numeric, scale = FALSE) %>%
mutate(tSNE1 = swissTsne$Y[, 1], tSNE2 = swissTsne$Y[, 2]) %>%
gather(key = "Variable", value = "Value", c(-tSNE1, -tSNE2, -Status))
ggplot(swissTibTsne, aes(tSNE1, tSNE2, col = Value, shape = Status)) +
facet_wrap(~ Variable) +
geom_point(size = 3) +
scale_color_gradient(low = "dark blue", high = "cyan") +
theme_bw()
```

The resulting plot from code listing 14.2 is shown in figure 14.7. Wow! Notice how much better a job t-SNE does of representing the differences between the two clusters in a two-dimensional space than PCA? The clusters are well resolved, although if you look closely you can see a couple of cases that seem to be in the wrong cluster. Shading the points by the value of each variable also helps us identify that counterfeit notes tend to have lower values of the Diagonal variable, and higher values of the Bottom and Top variables. It also seems like there might be a small, second cluster of counterfeit notes. This could be a set of notes made by a different counterfeiter, or it could be an artefact of an imperfect combination of hyperparameters. More investigation would be needed to tell if these are actually a distinct cluster or not.

### IMPORTANT

Do your plots look a little different to mine? Of course they do! Remember that the initial embedding is random (stochastic), so each time you run t-SNE on the same data and with the same hyperparameters, you’ll get a slightly different embedding.

![](img/a22105d68c35e8d5bd3c7bafb4644881_353_0.png)

Figure 14.7 tSNE1 and tSNE2 axes plotted against each other, faceted and shaded by the original variables, and shaped by whether each case was a genuine or counterfeit banknote.

Recreate the plot in figure 14.7, but this time don’t center the variables before running t-SNE on them (just remove the mutate_if() layer. Can you see why scaling was necessary?)

In this section, I’ll show you what UMAP is, how it works, and why it’s useful. Uniform manifold approximation and projection, thankfully shortened to UMAP, is a non-linear dimension reduction algorithm like t-SNE. UMAP is state of the art, having only been published in 2018, and has a few benefits over the t-SNE algorithm.

Firstly, it’s considerably faster than t-SNE, where the length of time it takes to run increases less than the square of the number of cases in the dataset. To put this in perspective, a dataset that might take t-SNE hours to compress, will take UMAP minutes.

The second benefit (and the main benefit in my eyes) is that UMAP is a deterministic algorithm. In other words, given the same input, it will always give the same output. This means that, unlike t-SNE, we can project new data onto the lower-dimensional representation, allowing us to incorporate UMAP into our machine learning pipelines.

The third benefit is that UMAP preserves both local *and* global structure. Practically, this means that not only can we interpret two cases close to each other in lower dimensions as being similar to each other in high dimensions, we can also interpret two *clusters* of cases close to each other as being more similar to each other in high dimensions.

So how does UMAP work? Well, UMAP assumes the data is distributed along a *manifold*. A manifold is an n-dimensional smooth geometric shape where, for every point on this manifold, there exists a small neighborhood around that point that looks like a flat, two-dimensional plane. If that doesn’t make sense to you, consider that the world is a three-dimensional manifold, any part of which can be mapped into a flat representation, literally called a map. So UMAP searches for a surface, or a higher-dimensional space that the data are distributed along. The distances between cases *along the manifold* can then be calculated, and a lower-dimensional representation of the data can be optimized iteratively to reproduce these distances.

Prefer a visual representation? Me too. Have a look at figure 14.8. I’ve drawn a question mark as a manifold, and randomly seeded 15 cases around the manifold across two variables. UMAP’s job is to learn the question mark manifold, so that it can measure the distances between cases along the manifold, instead of ordinary Euclidean distance, like t-SNE does. It achieves this by searching a region around each case, for another case. Where these regions encapsulate another case, the cases get connected by an edge. This is what I’ve done in the top row of figure 14.8, but can you see that the manifold is incomplete? There are gaps in my question mark. This is because the regions we searched around each case had the same radius, and the data wasn’t uniformly distributed along the manifold. If the cases were spaced out along the question mark at regular intervals, then this approach would have worked provided I selected an appropriate radius for the search regions.

Real-world data are rarely evenly distributed, and so UMAP solves this problem in two ways. Firstly, it expands out each search region for each case until it meets its nearest neighbor. This ensures that there are no orphan cases: while there can be multiple, disconnected manifolds in a dataset, every case must connect to at least one other case. Secondly, UMAP creates an additional search region which has a larger radius in low-density areas, and a smaller radius in high-density regions. These search regions are described as "fuzzy", in that the further from the center another case finds itself, the lower the probability that an edge exists between those cases.

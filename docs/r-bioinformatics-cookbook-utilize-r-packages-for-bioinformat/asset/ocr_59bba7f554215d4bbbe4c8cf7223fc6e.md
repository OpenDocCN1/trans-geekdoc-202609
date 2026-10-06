# Zooming and making callouts from selected plot sections with facetzoom

```
geom point() +
facet_zoom(x = island == "Dream", zoom.data = island = 
"Dream")
```

And is how we select a region of plot to highlight in a callout.

# How it works..

As usual, the recipe starts by loading the libraries and the data; then we use the allele_freqs data to create a scatter plot of allele frequency across genome position, having filtered data so that we are working only on chromosome 1 data. Once the plot is created and colored, we apply a facet_zoom() layer from ggforce and we use the xlim parameter so that the new zoomed facet shows the x axis between those points (Figure 3.16):

![](bbox=[0.135, 0.337, 0.813, 0.626])

Step 2 looks at pulling out a facet based on categorical data and not just a numeric axis range; in the early part, we build a ggplot on the penguins data, coloring a scatter plot by the island variable. This time, the facet_zoom() function is given a logical expression (island == "Dream") to retain data satisfying the expression in the zoom; zoom.data shows only data passing its logical condition in the zoom and not in other other panels.
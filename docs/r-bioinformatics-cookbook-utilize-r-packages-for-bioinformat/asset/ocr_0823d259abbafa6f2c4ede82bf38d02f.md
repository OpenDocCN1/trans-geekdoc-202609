```
angle = 15
force = 10,
xlim = c(NA, NA)
) +
geom_point(aes(x = log2FoldChange, y = scaled_p, colour = signif)) + 
theme_minimal()
```

This is all we need to apply some tidying to our labels.

# # How it works...

After loading the libraries, this use ggrepel goes on a set to random; this helps with the reproducibility of the plots when using ggrepel as the layout has a random component that can make over plots thicker than it needs to be. The dataset has a column added and the p-value for the volcano plot we will make. The data passes to ggplot2, and geom_text_repel() is used—note that the aesthetic is declared in the geom with aes() rather than ours. We must set the label mapping to render the labels. The parameters for this geom are to allow maximum readability and space for the labels. The max.time parameter limits the algorithm runtime; setting point.padding removes the maximum distance the label can be from the point and allows the label to float far from the one it belongs to. The arrow function defines the properties of the line joining labels and points. The force parameter defines how labels overlap (defaulting to 1, this is strong). The final parameter, xlim, defines a boundary on labels on the x axis; setting values to NA means the labels can float outside of the plot area, which is useful as some very busy plots can still run out of room. A corresponding parameter exists for the y axis. The plot is produced as seen in Figure 3.15. A keen-eyed reader will notice that most points don't actually have a label. This is because the max.overlaps removes labels that overlap too many things; the default value that we have used is 10:

![](bbox=[0.139, 0.653, 0.81, 0.846])

As we can see, the plot we have created makes the best use of the space available for the number of labels we want to show.
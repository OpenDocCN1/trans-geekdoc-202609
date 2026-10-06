62 ggplot2 and Extensions for Publication Quality Plots

3. Create a gradient plot:

```
ggplot(penguins) +
  aes(x = fli_length_mm, y = island) +
  stat_gradientinterval(aes(colour=island, fill=island)) +
  theme_minimal ()
```

And that is all we need to make plots with representations of variability.

# How it works...

Step 1 shows how to create a raincloud plot, as seen in Figure 3.11. We set up the data and aesthetic layer in ggplot as usual, adding the geom_dots () function from ggdist, which will add a layer of dots representing each data point to the plot. We use the side parameter to put the dots underneath the line "bottomleft". The density plot and the range markers in black are added with a stat layer, not a geom layer, and range and point markers in black need to be calculated from the data before plotting—stat_slabinterval () does this for us. Note that 'slabs' is ggdist's naming convention for distribution glyphs:

![](bbox=[0.141, 0.458, 0.858, 0.676])

Figure 3.11 – Raincloud plots

Step 2 creates the plot shown in Figure 3.12; again, we use a stat_halfe stat to compute the distributions, passing it a logical predicate to divide the areas of the plot up. We also use the geom_vlineline () function to add a dashed line to further demarcate the regions across the y axis. The last part of this step adds a custom palette:
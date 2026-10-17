![](bbox=[0.24, 0.12, 0.73, 0.48])

# Figure 8.2: RColorBrewer Palettes.

Here is one more example of how you can use the scale functions; take a look at the next plot example. We used two geom_histogram() calls; layers, to plot a histogram of pain at baseline and at follow-up. This allows us to visualize that pain at follow-up tends to be lower than at baseline.

We also specify the fill to be by “Baseline” and “Follow-up” within the aesthetic, even though this isn’t a column in the data: this is a sort of manual way to color the bars. We use the scale_fill_manual() function to then specify the colors we want to use for these two categories using the values argument. We received three warnings when creating this plot! This is because we have many NA values for follow-up and because we did not specify the bin size for either histogram. C’est la vie.

```
ggplot(pain_df)+
geom_histogram(aes(x = PAIN_INTENSITY_AVERAGE, fill = "Baseline")) +
geom_histogram(aes(x = PAIN_INTENSITY_AVERAGE.FOLLOW_UP,
fill = "Follow-Up")) +
```
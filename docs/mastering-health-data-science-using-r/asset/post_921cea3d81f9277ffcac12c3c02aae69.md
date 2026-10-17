
![](img/58a554e865d49ca347d9a3f76f8f0812_139_0.png)

### 8.1.1 Practice Question

Recreate Figure 8.1.

```r
# Insert your solution here:
```

## 8.2 Adjusting the Axes and Aesthetics

We can further control how each aesthetic element is displayed using scale functions. For example, suppose that I want to update the previous plot. In particular, I first want to update the x-axis to display all of the values 0 to 10 instead of 0, 2.5, 5, etc. To update the x-axis, I need to find the corresponding scale function for x with continuous values. This function is `scale_x_continuous()`, which allows me to specify limits (`limits`), breaks (`breaks`), and labels (`labels`). The scale functions can be found on the second sheet of the cheat sheet. In this case, I just want to update the breaks to be all integer values from 0 to 10.

```r
ggplot(pain_df)+
geom_histogram(aes(x = PAIN_INTENSITY_AVERAGE), color = "violetred",
fill = "lightblue", alpha = 0.5, bins = 11) +
labs(x = "Patient Reported Pain Intensity", y = "Count")+
scale_x_continuous(breaks = 0:10)+
theme_minimal()
```

![](img/58a554e865d49ca347d9a3f76f8f0812_140_0.png)

Figure 8.1: Line Plot.

![](img/58a554e865d49ca347d9a3f76f8f0812_140_1.png)

Now, let's take a more complex example. The following plot shows each patient's reported sleep disturbance vs. physical function and colors each point by their reported pain intensity. Since some points might overlap in values, we added `position = "jitter"` to the `geom_point()` function to jitter the points, which corresponds to adding some random noise to each point’s position. As presented, this plot is difficult to interpret. For example, the color of pain intensity makes it hard to see how pain changes, and the legend title needs to be simpler.

```r
ggplot(pain_df)+
geom_point(aes(x = PROMIS_PHYSICAL_FUNCTION,
 y = PROMIS_SLEEP_DISTURB_V1_0,
 color = PAIN_INTENSITY_AVERAGE), position="jitter")
```

![](img/58a554e865d49ca347d9a3f76f8f0812_141_0.png)

Suppose that we wanted to visualize the pain intensity and sleep disturbance for patients with below-average physical function. Note that both sleep disturbance and physical function are reported as T-Scores, meaning that the raw scores have been converted to a standardized score with mean 50 and standard deviation 10 within the population. We can use the scale functions to update our axes and labels to reflect this information. As before, we need to use the `scale_x_continuous()` function to update the x-axis for a continuous variable. In this case, we update the limits (to restrict to below-average physical function), breaks, and labels. We similarly update the y-axis.

Lastly, suppose we want to update the color aesthetic. As before, this aesthetic corresponds to a continuous variable. The cheat sheet provides several possible scale functions depending on how we want to specify the color gradient. We choose the `scale_color_gradient()` function, since this allows us to specify the low and high end colors. We can also specify the breaks for the legend values similar to how we specified the breaks for the x- and y-axes. The `name` argument also allows us to rename this legend. The palette then converts this to a continuous color gradient. Note that in contrast to the `scale_color_gradient()` function that we chose to use for this example, the functions `scale_color_gradient2()` and `scale_color_gradientn()` allow you to specify more color points in the gradient rather than just the two extreme colors.

We can observe that decreased physical function is associated with higher sleep disturbance, and that those with worse physical function and worse sleep disturbance tend to have higher reported pain. Note that this time we receive a warning message, which is because our axis limits have cut off some points. To avoid this message, we could use the function `coord_cartesian()` to specify our limits which clips the values rather than removing points outside the limits.

```r
ggplot(pain_df)+
  geom_point(aes(x = PROMIS_PHYSICAL_FUNCTION,
                 y = PROMIS_SLEEP_DISTURB_V1_0,
                 color = PAIN_INTENSITY_AVERAGE),
             position = "jitter", alpha = 0.5) +
  scale_x_continuous(limits = c(15,50), breaks = c(20, 30, 40, 50),
                     labels = c("-3 SD", "-2 SD", "-1 SD",
                                "Pop Mean")) +
  scale_y_continuous(breaks = c(40, 50, 60, 70, 80),
                     labels = c("-1 SD", "Pop Mean", "+1 SD", "+2 SD",
                                "+3 SD")) +
  scale_color_gradient(breaks = seq(0,10,2), low = "green",
                       high = "red", "Reported Pain") +
  labs(x = "PROMIS Physical Function T-Score",
       y = "PROMIS Sleep Disturbance T-Score") +
  theme_minimal()
#> Warning: Removed 121 rows containing missing values or values outside the scale range
#> ('geom_point()').
```

![](img/58a554e865d49ca347d9a3f76f8f0812_143_0.png)

We now demonstrate these scale functions for discrete variables. In the subsequent example, we first create a new race variable that has only three categories since other groups have limited observations. We then create a boxplot for pain intensity by race. There are two discrete aesthetics here: color and the y-axis. This plot shows a higher median pain for black patients compared to other races.

```r
pain_df$PAT_RACE_CAT <- ifelse(pain_df$PAT_RACE %in% c("BLACK",
                                        "WHITE"),
                               pain_df$PAT_RACE, "OTHER")
pain_df$PAT_RACE_CAT <- as.factor(pain_df$PAT_RACE_CAT)
```

```r
ggplot(pain_df)+
  geom_boxplot(aes(y = PAT_RACE_CAT, x = PAIN_INTENSITY_AVERAGE,
                   fill = PAT_RACE_CAT), alpha = 0.5) +
  theme_minimal()
```

![](img/58a554e865d49ca347d9a3f76f8f0812_145_0.png)

The **RColorBrewer** package (Neuwirth 2022) contains several default palettes to choose from, shown in the following output. You can also create your own palette using the `brewer.pal()` function from this package. To visualize a palette, you can use the available online tool².

```r
library(RColorBrewer)
display.brewer.all()
```

![](img/58a554e865d49ca347d9a3f76f8f0812_146_0.png)

Figure 8.2: RColorBrewer Palettes.

Here is one more example of how you can use the scale functions; take a look at the next plot example. We used two `geom_histogram()` calls (layers) to plot a histogram of pain at baseline and at follow-up. This allows us to visualize that pain at follow-up tends to be lower than at baseline.

We also specify the fill to be by “Baseline” and “Follow-up” within the aesthetic, even though this isn’t a column in the data: this is a sort of manual way to color the bars. We use the `scale_fill_manual()` function to then specify the colors we want to use for these two categories using the values argument. We received three warnings when creating this plot! This is because we have many NA values for follow-up and because we did not specify the bin size for either histogram. C’est la vie.

```r
ggplot(pain_df)+
geom_histogram(aes(x = PAIN_INTENSITY_AVERAGE, fill = "Baseline")) +
geom_histogram(aes(x = PAIN_INTENSITY_AVERAGE.FOLLOW_UP,
fill = "Follow-Up")) +
scale_x_continuous(breaks = c(0:10)) +
scale_fill_manual(values = c("violetred", "pink"),
name = "Measurement") +
labs(x = "Reported Pain Intensity", y = "Count") +
theme_minimal()
#> Warning: Removed 3604 rows containing non-finite values outside the scale range
#> ('stat_bin()').
```

![](img/58a554e865d49ca347d9a3f76f8f0812_147_0.png)

## 8.3 Adding Groups

In the previous example, we created two histograms using two calls to the `geom_histogram()` function. However, there is another way to create multiple layers like this when you want to separate the geom layer based on a variable. For example, suppose we want to visualize the distribution of physical function by whether someone has follow-up information. In the following code, we create the variable HAS_FOLLOW_UP before using it in our aesthetic for `geom_density()` as both the color and group. In fact, we do not have to add the group argument because as soon as we specify to `ggplot` that we want to color the density plots by this variable, it creates the grouping. Finally, we update the legend for this grouping using the `scale_color_discrete()` function, as the discrete variable HAS_FOLLOW_UP determines the color.

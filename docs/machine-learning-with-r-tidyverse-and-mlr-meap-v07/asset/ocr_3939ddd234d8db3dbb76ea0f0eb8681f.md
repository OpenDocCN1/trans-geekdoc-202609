![](bbox=[0.1, 0.1, 0.9, 0.4])

Can you see how the faceting has worked? Rows in the data with different values of Variable are plotted on different subplots! This is why we needed to gather the data into an untidy format: so we could supply a single variable for ggplot2 to facet by.

> EXERCISE 4.1 Re-draw the plot in figure 4.10, but add a geom_point() layer, setting the alpha argument to 0.05, and the size argument to 3. Does this make the violin plot make more sense?

Now let’s do the same for the factors in our dataset by filtering the data for rows that contain only the Pclass and Sex variables. This time, we want to see what proportion of passengers in each level of the factors, survived. So we plot the factor levels on the x axis by supplying Value as the x aesthetic mapping, and we want to use different colors to denote survival vs. non-survival, so we supply Survived as the fill aesthetic. We facet by Variable as before and add a bar geometric object with the argument position = "fill", which stacks the data for the survivors and non-survivors such that they sum to one, to show us the proportion of each. The resulting plot is shown in figure 4.11.



```
titanicUntidy %>% 
  filter(Variable == "Pclass" | Variable == "Sex") %>% 
  ggplot(aes(Value, fill = Survived)) + 
  facet_wrap(~ Variable, scales = "free_x") + 
  geom_bar(position = "fill") + 
  theme_bw()
```
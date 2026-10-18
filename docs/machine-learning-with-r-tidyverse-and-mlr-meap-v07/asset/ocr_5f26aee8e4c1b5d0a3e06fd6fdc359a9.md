# IMPORTANT

At the end of the tuning process, did you get the warning: did not converge in 100 iterations? This is how to tell whether you've set the iter.max argument too low in your learner definition. Your choices are either: choose to accept the result as is, which may or may not be a near-optimal solution, or if you have the computational budget, increase iter.max.

# EXERCISE 16.1

Change our kmeans definition (we created it in code listing 16.8) such that the value of iter.max is 200. Re-run the tuning procedure in code listing 16.12. Does the error about not converging disappear?

# NOTE

Notice that we have a metric we didn't ask for: exec.time, which records how long it took to train a model with each combination of hyperparameters, in seconds.

To get a better understanding of how our three internal metrics vary with both cluster number and algorithm choice, let’s plot the tuning process. Recall that to do this, we first need to extract the tuning data from our tuning result, using the generateHyperParsEffectData() function. Call the $data component from the kMeansTuningData object so you can see how it’s structured (I won’t print it here for the sake of space).

Let’s plot this data such that we have a different facet per performance metric, and a different line per algorithm. To do this we first need to gather the data such that the name of each performance metric is in one column, and the value of the metric is in another column. I do this using the gather() function, naming the key column "Metric" and the value column "Value". As we only want these columns gathered, I supply a vector of columns I don’t want to gather. Print the new, gathered dataset to make sure you understand what we did. Having the data in this format allows us to facet by algorithm, and plot separate lines for each metric.

To plot the data, I use the ggplot() function, mapping centers (the number of clusters) and Value to the x and y aesthetics, respectively. By mapping algorithm to the col aesthetic, separate geom_line() and geom_point() layers will be drawn for each algorithm (with different colors). I use the facet_wrap() function to draw a separate subplot for each performance metric, setting the scales = "free_y" argument to allow different y axes for each facet (as they have different scales). Lastly, I add the geom_line() and geom_point() layers, and a theme.

```
kMeansTuningData <- generateHyperParsEffectData(tunedK)
kMeansTuningData$data
```
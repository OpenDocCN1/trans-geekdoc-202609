# CHAPTER 4. EXPLORING AND VISUALIZING BEHAVIORAL DATA

library(qtlcharts) # Library for interactive plots.

```
# Load home activities dataset.
dataset <- read.csv(file.path(datasets_path,
    "home_tasks",
    "sound_acc.csv")
```

```
oplCorr(dataset[-1]
```

![](bbox=[0.157, 0.351, 0.823, 0.638])

> Please note that at the time this book was written, printed paper does not support interactive plots. Please, see the online version instead to see the actual result or run the code on a computer.

# 4.7 Timeseries

Behavior is something that usually depends on time. Thus, being able to visualize time series data becomes essential. To illustrate how timeseries data can be plotted, I will use the ggplot package and the HAND GESTURES dataset. Recall that the data was collected
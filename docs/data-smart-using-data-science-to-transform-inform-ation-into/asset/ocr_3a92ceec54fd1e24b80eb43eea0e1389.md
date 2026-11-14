various cutoff values and uses them to assemble a curve of your choosing (in this case a ROC curve).

```
perf.lm <- performance(pred.lm, "tpr", "fpr")
perf.rf <- performance(pred.rf, "tpr", "fpr")
```

> NOTE
> 
> If you're curious, `performance()` provides other options besides the `tpr` and `fpr` values, such as `prec` for precision and `rec` for recall. Read the ROCR package documentation for more detail.

You can then plot these curves using R's `plot()` function. First, the linear model curve (the `xlim` and `ylim` flags are used to set the upper and lower bounds on the x- and y-axes in the graph):

```
> plot(perf.lm, xlim = c(0,1), ylim = c(0,1))
```

You can add the random forest curve in using the `add = TRUE` flag to overlay it and using the `lty = 2` flag (`lty` stands for “line type”:) to make this line dashed.

```
> plot(perf.rf, xlim = c(0,1), ylim = c(0,1), lty = 2, add = TRUE)
```

This overlays the two curves with the random forest performance as a dashed line, as shown in Figure 11.10. For the most part, the logistic regression is superior with the random forest pulling ahead briefly on the far right of the graph.

![](bbox=[0.19, 0.596, 0.742, 0.856])

# Figure 11.10: Recall and precision graphed in R
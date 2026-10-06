# CHAPTER 6. DISCOVERING BEHAVIORS WITH UNSUPERVISED LEARNING 191

# Item frequencies

![](bbox=[0.125, 0.143, 0.814, 0.396])

Figure 6.12: Frequencies of the top 15 items.

```
itemFrequencyPlot(transactions,
  type = "relative",
  topN = 15,
  main = 'Item frequencies')
```

The type argument specifies that we want to plot the relative frequencies. Use **absolute** instead to plot the total counts. **topN** is used to select how many items are plotted. Figure 6.12 shows the output.

Now it is time to find some interesting rules! This can be done with apriori() function as follows:

```
# Run apriori algorithm
resrules <- apriori(transactions,
  parameter = list(support = 0.001,
  confidence = 0.5,
  # Find rules with at least 2 items.
  minlen = 2,
  target = 'rules')
```
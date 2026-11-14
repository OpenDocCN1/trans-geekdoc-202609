![](bbox=[0.136, 0.105, 0.847, 0.303])

# Figure 5.27: Counting edge stubs on the r-neighborhood graph

As for the expected edge calculation that you need to tack on as a penalty, you can calculate it the same way as described previously:

# stubs customer A * # stubs customer B / Total stubs

By bringing these points and penalties together in cell B2, you end up with this formula:

```
='WineNetwork-radj'!B2 - (
('WineNetwork-radj'!$CX2*'WineNetwork-radj'!B$102) /
'WineNetwork-radj'!$CX$102
)
```

You have the 0/1 adjacency score minus the expected count.

Note that the formula uses absolute cell references on the stub values so that when you drag the formula, everything changes appropriately. Thus, dragging the formula across and down the Scores tab, you end up with the values shown in Figure 5.28.

![](bbox=[0.136, 0.64, 0.847, 0.808])

# Figure 5.28: The Scores tab

To drive this score home, check out cell K2. This is the score for a Brown/Adams clustering. It's 0.755.
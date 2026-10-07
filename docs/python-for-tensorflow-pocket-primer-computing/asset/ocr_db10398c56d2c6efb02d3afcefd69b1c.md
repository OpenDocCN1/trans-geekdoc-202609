```
plt.hist([grey_height,
labs_height],stacked=True,color=['r ', 'b'])
plt.show()
```

Listing 4.10 is straightforward: the NumPy variables grey_height and labs_height contain a random set of values whose upper bound is greyhounds and labradors, respectively. The Pyplot API hist() uses the points grey_height and labs_height in order to display a histogram.

**Figure 4.10** displays a histogram whose shape is based on the code in Listing 4.10.

![](bbox=[0.19, 0.365, 0.866, 0.754])

**FIGURE 4.10** A Histogram Based on Random Values.

# A SIMPLE LINE IN MATPLOTLIB
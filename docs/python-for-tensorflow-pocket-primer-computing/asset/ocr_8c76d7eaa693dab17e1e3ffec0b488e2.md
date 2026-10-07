```
#create figure and scatter plot of the random
points
plt.figure()
plt.scatter(trX,trY)
```

```
# Draw one line with the line function
plt.plot(trX, .2 + 2 * trx)
plt.show()
```

Listing 4.9 defines the NumPy variable trx that contains 101 equally spaced numbers that are between -1 and 1 (inclusive). The variable trY is defined in two parts: the first part is 2*trx and the second part is a random value that is partially based on the length of the one-dimensional array trx. The variable trY is the sum of these two “parts,” which creates a “fuzzy” line segment. The next portion of Listing 4.9 creates a scatterplot based on the values in trx and trY, followed by the Pyplot API plot() that renders a line segment.

Figure 4.9 displays a random set of points based on the code in Listing 4.9.
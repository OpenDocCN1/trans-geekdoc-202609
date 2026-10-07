```
x2 = np.linspace(-5, 5, num=200)
y2 = -x2

plt.axis([-5, 5, -5, 5])
plt.plot(x1,y1)
plt.plot(x2,y2)
plt.show()
```

Listing 4.2 defines two lines using the technique that you saw in Listing 4.1, except that these two lines define y1 = x1 and y2 = -x2, which produces slanted lines instead of horizontal lines.

Figure 4.2 displays two slanted line segments whose equations are defined in Listing 4.2.

![](bbox=[0.223, 0.406, 0.868, 0.793])

FIGURE 4.2 A Graph of Two Slanted Line Segments.

# PARALLEL SLANTED LINES IN MATPLOTLIB
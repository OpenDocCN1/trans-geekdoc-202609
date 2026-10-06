# SUPPORT VECTOR MACHINES

So we have plotted two lines that has separated the data into two classes. As we already know, the SVM algorithms finds the maximum marginal hyperplane around them of some width like we can do so for the two lines by drawing margins around them of some width like:

```
In [16]: xfit = numpy.linspace(-5,5)
plt.scatter(X1,X2,c=y)
for m, b, d in [[0.375,0.5,3],(-0.5,2,6)]:
 yfit = m * xfit + b
 plt.plot(xfit, yfit, '-k')
 plt.fill_between(xfit, yfit - d, yfit + d,
edgecolor='none',color='#AAAAAA', alpha=0.4)
plt.xlim(-5,5)
```

Out[16]: (-5.0, 5.0)

![](bbox=[0.297, 0.439, 0.843, 0.668])

As you can see we have drawn marigns around the lines to find the nearest support vector. The margins are very wide because the data clusters are are a bit far

We did so as same as before, plotting our graph with data clusters, separator lines and then we used the fill_between() functions to create those margins. We passed the value of one X and 2 Y axes to fill between them to represent our margin. We didn’t need edgecolor, and the fill color as black and the alpha as 0.4 i.e. transparency
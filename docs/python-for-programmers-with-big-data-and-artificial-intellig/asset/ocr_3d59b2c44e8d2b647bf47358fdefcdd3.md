the x-axis.

When you run this code, you’ll see in the full color output that using separate colors for each Iris species shows how the species relate to one another on a feature-by-feature basis. Interestingly, all the scatter plots clearly separate the Iris setosa blue dots from the other species’ orange and green dots, indicating that Iris setosa is indeed in a “class by itself.” We also can see that the other two species can sometimes be confused with one another, as indicated by the overlapping orange and green dots. For example, if you look at the scatter plot for sepal width vs. sepal length, you’ll see the Iris versicolor and Iris virginica dots are intermixed. This indicates that it would be difficult to distinguish between these two species if we had only the sepal measurements available to us.

# Displaying the pairplot in One Color

If you remove the hue keyword argument, pairplot function uses only one color to plot all the data because it does not know how to distinguish the species:

lick here to view code image

```
In [21]: grid = sns.pairplot(data=iris_df, vars=iris_df.columns[0:4])
```

As you can see in the resulting pair plot on the next page, in this case, the graphs along the diagonal are histograms showing the distributions of all the values for that feature, regardless of the species. As you study each scatter plot, it appears that there may be only two distinct clusters, even though for this dataset we know there are three species. If you do not know the number of clusters in advance, you might ask a domain expert who is thoroughly familiar with the data. Such a person might know that there are three species in the dataset, which would be valuable information as we try to perform machine learning on the data.

The pairplot diagrams work well for a small number of features or a subset of features so that you have a small number of rows and columns, and for a relatively small number of samples so you can see the data points. As the number of features and samples increases, each scatter plot quickly becomes too small to read. For larger datasets, you may choose to plot a subset of the features and potentially a randomly selected subset of the samples to get a feel for your data.
lick here to view code image

```
In [16]: iris_df['species'].describe()
Out[16]:
count    150
unique     3
top     setosa
freq      50
Name: species, dtype: object
```

# 14.7.3 Visualizing the Dataset with a Seaborn pairplot

Let's visualize the features in this dataset. One way to learn more about your data is to see how the features relate to one another. The dataset has four features. We cannot graph one against the other three in a single graph. However, we can plot pairs of features against one another. Snippet [20] uses Seaborn function pairplot to create a grid of graphs plotting each feature against itself and the other specified features:

lick here to view code image

```
In [17]: import seaborn as sns
In [18]: sns.set(font_scale=1.1)
In [19]: sns.set_style('whitegrid')
In [20]: grid = sns.pairplot(data=iris_df,   vars=iris_df.columns[0:4],
        ...:                 hue='species')
        ...:
```

The keyword arguments are:

+   - data—The DataFrame ³ containing the data to plot.

³This also may be a two-dimensional array or list.

+   - vars—A sequence containing the names of the variables to plot. For a DataFrame, these are the names of the columns to plot. Here, we use the first four DataFrame columns, representing the sepal length, sepal width, petal length and petal width, respectively.

+   - hue—The DataFrame column that's used to determine colors of the plotted data. In this case, we'll color the data by Iris species.
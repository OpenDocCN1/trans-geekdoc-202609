
import`matplotlib.pyplot` as `plt` import`seaborn` as `sns` `titanic` = `sns`.load_dataset("titanic") # Returns a scalar # `titanic`.ix[4, 'age'] print("age:",`titanic`.at[4, 'age']) # Returns a Series of name 'age', and the age values associated # to the index labels 4 and 5 # `titanic`.ix[[4, 5], 'age'] print("series:",`titanic`.loc[[4, 5], 'age']) # Returns a Series of name '4', and the age and fare values # associated to that row. # `titanic`.ix[4, ['age', 'fare']] print("series:",`titanic`.loc[4, ['age', 'fare']]) # Returns a DataFrame with rows 4 and 5, and columns 'age' and 'fare' # `titanic`.ix[[4, 5], ['age', 'fare']] print("dataframe:",`titanic`.loc[[4, 5], ['age', 'fare']]) 

query = `titanic`[(`titanic`.sex == 'female') & (`titanic`['class'].isin(['First', 'Third'])) & (`titanic`.age > 30) & (`titanic`.survived == 0)] print("query:",query) 

[Listing F.27](#appF.xhtml#listF.27) contains the same import statements as [Listing F.26](#appF.xhtml#listF.26), and then initializes the variable `titanic` with the contents of the built-in Titanic dataset. The next code snippet displays the age of the passenger with index 4 in the dataset (which equals 35).

The following code snippet displays the ages of passengers with index values 4 and 5 in the dataset:

print("series:",`titanic`.loc[[4, 5], 'age']) 

The next snippet displays the age and fare of the passenger with index 4 in the dataset, followed by another code snippet displays the age and fare of the passengers with index 4 and index 5 in the dataset.

The final portion of [Listing F.27](#appF.xhtml#listF.27) is the most interesting part: it defines a variable `query` as shown here:

query = `titanic`[(`titanic`.sex == 'female') & (`titanic`['class'].isin(['First', 'Third'])) & (`titanic`.age > 30) & (`titanic`.survived == 0)] 

The preceding code block will retrieve the female passengers who are in either first class or third class, and who are also over 30, and they did not survive the accident. The entire output from [Listing F.27](#appF.xhtml#listF.27) is here:

age: 35.0 series: 4    35.0 5     NaN Name: age, dtype: float64 series: age       35 fare    8.05 Name: 4, dtype: object dataframe:     age    fare 4  35.0  8.0500 5   NaN  8.4583 query:   survived  pclass     sex   age  sibsp  parch     fare embarked  class  \\ 18          0       3  female  31.0      1      0  18.0000        S  Third 40          0       3  female  40.0      1      0   9.4750        S  Third 132         0       3  female  40.0      1      0   14.5000        S  Third 167         0       3  female  47.0      1      0  27.9000        S  Third 177         0       3  female  50.0      0      0  28.7125        C  First 254         0       3  female  41.0      0      2  20.2125        S  Third 276         0       3  female  45.0      0      0   7.7500        S  Third 362         0       3  female  45.0      0      1  14.4542        C  Third 396         0       3  female  31.0      0      0   7.8542        S  Third 503         0       3  female  37.0      0      0   9.5875        S  Third 610         0       3  female  39.0      1      5  31.2750        S  Third 638         0       3  female  41.0      0      5  39.6875        S  Third 657         0       3  female  32.0      1      1  15.5000        Q  Third 678         0       3  female  43.0      1      6  46.9000        S  Third 736         0       3  female  48.0      1      3  34.3750        S  Third 767         0       3  female  30.5      0      0   7.7500        Q  Third 885         0       3  female  39.0      0      5  29.1250        Q  Third 

## **Visualizing a Pandas Dataset in Seaborn**

[Listing F.28](#appF.xhtml#listF.28) displays the contents of `pandas_seaborn.py` that illustrates how to display a Pandas dataset in Seaborn.

***LISTING F.28: pandas_seaborn.py***

```python
import`pandas` as `pd` import`random` import`matplotlib.pyplot` as `plt` import`seaborn` as `sns` df = `pd`.DataFrame() df['x'] = `random`.sample(range(1, 100), 25) df['y'] = `random`.sample(range(1, 100), 25) print("top five elements:") print(df.head()) # display a density plot #`sns`.kdeplot(df.y) # display a density plot #`sns`.kdeplot(df.y, df.x) #`sns`.distplot(df.x) # display a histogram #`plt`.hist(df.x, alpha=.3) #`sns`.rugplot(df.x) # display a boxplot #`sns`.boxplot([df.y, df.x]) # display a violin plot #`sns`.violinplot([df.y, df.x]) # display a heatmap #`sns`.heatmap([df.y, df.x], annot=True, fmt="d") # display a cluster map #`sns`.clustermap(df) # display a scatterplot of the data points `sns`.lmplot('x', 'y', data=df, fit_reg=False) plt.show()
```

[Listing F.28](#appF.xhtml#listF.28) contains several familiar import statements, followed by the initialization of the Pandas variable `df` as a Pandas data frame. The next two code snippets initialize the columns and rows of the data frame and the print() statement display the first five rows.

For your convenience, [Listing F.28](#appF.xhtml#listF.28) contains an assortment of “commented out” code snippets that use Seaborn in order to render a density plot, a histogram, a boxplot, a violin plot, a heatmap, and a cluster. Uncomment the portions that interest you in order to see the associated plot. The output from [Listing F.29](#appF.xhtml#listF.29) is here:

top five elements:

    `x`   `y` 0  52  34 1  31  47 2  23  18 3  34  70 4  71   1 

[Figure F.22](#appF.xhtml#figF.22) displays a plot of the data in the Titanic dataset based on the code in [Listing F.28](#appF.xhtml#listF.28).

![Figure F.22. ¶ A Pandas Data Frame Displayed via Seaborn.](images/figF.22.jpg)

Figure F.22. ¶ A Pandas Data Frame Displayed via Seaborn.

## **Data Visualization in Pandas**

Although Matplotlib and Seaborn are often the “go to” Python libraries for data visualization, you can also use Pandas for such tasks.

[Listing F.29](#appF.xhtml#listF.29) displays the contents `pandas_viz1.py` that illustrates how to render various types of charts and graphs using Pandas and Matplotlib.

***LISTING F.29: pandas_viz1.py***

```python
import`pandas` as `pd` import`numpy` as `np` import`matplotlib.pyplot` as `plt` df = `pd`.DataFrame(`np`.random.rand(16,3), columns=['X1','X2','X3']) print("First 5 rows:") print(df.head()) print() print("Diff of first 5 rows:") print(df.diff().head()) print() # bar chart: #ax = df.plot.bar() # horizontal stacked bar chart: #ax = df.plot.barh(stacked=True) # vertical stacked bar chart: ax = df.plot.bar(stacked=True) # stacked area graph: #ax = df.plot.area() # non-stacked area graph: #ax = df.plot.area(stacked=False) #plt.show(ax)
```

[Listing F.29](#appF.xhtml#listF.29) initializes the data frame `df` with a 16×3 matrix of random numbers, followed by the contents of `df`. The bulk of [Listing F.29](#appF.xhtml#listF.29) contains code snippets for generating a bar chart, a horizontal stacked bar chart, a vertical stacked bar chart, a stacked area graph, and a nonstacked area graph. You can uncomment the individual code snippet that displays the graph of your choice with the contents of `df`. Launch the code in [Listing F.29](#appF.xhtml#listF.29) and you will see the following output:

First 5 rows:          `X1`        `X2`        `X3` 0  0.051089  0.357183  0.344414 1  0.800890  0.468372  0.800668 2  0.492981  0.505133  0.228399 3  0.461996  0.977895  0.471315 4  0.033209  0.411852  0.347165   Diff of first 5 rows:          `X1`        `X2`        `X3` 0       NaN       NaN       NaN 1  0.749801  0.111189  0.456255 2 -0.307909  0.036760 -0.572269 3 -0.030984  0.472762  0.242916 4 -0.428787 -0.566043 -0.124150 

[Listing F.29](#appF.xhtml#listF.29) initializes the data frame `df` with a 16×3 matrix of random numbers, followed by the contents of `df`. The bulk of [Listing F.29](#appF.xhtml#listF.29) contains code snippets for generating a bar chart, a horizontal stacked bar chart, a vertical stacked bar chart, a stacked area graph, and a nonstacked area graph. You can uncomment the individual code snippet that displays the graph of your choice with the contents of `df`. Launch the code in [Listing F.29](#appF.xhtml#listF.29) and you will see the following output:

First 5 rows:          `X1`        `X2`        `X3` 0  0.051089  0.357183  0.344414 1  0.800890  0.468372  0.800668 2  0.492981  0.505133  0.228399 3  0.461996  0.977895  0.471315 4  0.033209  0.411852  0.347165   Diff of first 5 rows:          `X1`        `X2`        `X3` 0       NaN       NaN       NaN 1  0.749801  0.111189  0.456255 2 -0.307909  0.036760 -0.572269 3 -0.030984  0.472762  0.242916 4 -0.428787 -0.566043 -0.124150 

## **Summary**

This appendix started with some basic features of Matplotlib, along with examples of plotting lines, histograms, and simple trigonometric functions.

You also learned about Sklearn, including examples of working with the Digits and Iris datasets, and also how to process images. In addition, you saw how to perform linear regression with Sklearn.

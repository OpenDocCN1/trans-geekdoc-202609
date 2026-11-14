| country | description | designation | points | price | province | region_1 | region_2 | taster_name | taster_twitter_handle | title | variety | winery |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Italy | Aromas include tropical fruit, broom, brimstone... | Vulka Blanco | 87 | NaN | Sicily & Sardinia | Etna | NaN | Kerin O'Keefe | @kerinokeefe | Nicosia 2013 Vulka Blanco (Etna) | White Blend | Nicosia |
| Portugal | This is ripe and fruity, a wine that is smooth... | Avidagos | 87 | 15.0 | Douro | NaN | NaN | Roger Voss | @vossroger | Quinta dos Avidagos 2011 Avidagos Red (Douro) | Portuguese Red | Quinta dos Avidagos |
| US | Tart and snappy, the flavors of lime flesh and... | NaN | 87 | 14.0 | Oregon | Willamette Valley | Willamette Valley | Paul Gregutt | @paulgwine | Rainstorm 2013 Pinot Gris (Willamette Valley) | Pinot Gris | Rainstorm |
| US | Pineapple rind, lemon pith and orange blossom ... | Reserve Late Harvest | 87 | 13.0 | Michigan | Lake Michigan Shore | NaN | Alexander Peartree | NaN | St. Julian 2013 Reserve Late Harvest Riesling ... | Riesling | St. Julian |
| US | Much like the regular bottling from 2012, this... | Vinther's Reserve Wild Child Block | 87 | 65.0 | Oregon | Willamette Valley | Willamette Valley | Paul Gregutt | @paulgwine | Sweet Cheeks 2012 Vinther's Reserve Wild Child... | Pinot Noir | Sweet Cheeks |

# # Linear Graph

The “plot” method can be used to generate a linear chart in matplotlib. You will able to plot a number of columns in a single graph by looping through those desired columns and plotting them all on the same axis. Below is the sample code for the “iris” data set available on GitHub and the resulting graph for your reference.

```
```python
"# getting columns to plot
columns = iris.columns.drop (['class'])
# creation of x data
x_data = range(0, iris.shape [0])
# creation of figure and axis
fig, ax = plt.subplots ()
# plotting each column
for column in columns:
     ax.plot (x_data, iris[column], label=column)
# setting title and legend
ax.set_title ('Iris Dataset')
```
```
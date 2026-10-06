34 Machine Learning for Biomedical Applications

| df | gender | height | df2 | distance | height |
|---|---|---|---|---||}{
| 0 | M | 183 | 0 | 80 | 183 |
| 1 | F | 163 | 1 | 3 | 163 |
| 2 | F | 152 | 2 | 90 | 152 |
| 3 | F | 157 | 3 | 272 | 157 |
| 4 | F | 157 | 4 | 80 | 157 |

**Figure 1.9** Examples of dataframe objects. Left: the dataframe df composed of numerical values. Right: the dataframe df2 composed of mixture of numerical and text values.

simply typing its name, or if it has too many rows, we can display only the first five rows by

```
df.head()
```

as shown in Fig. 1.9. The last five rows are displayed by df.tail().

# Convert dataframe to numpy array

If the dataframe object contains numerical values, we can convert it to a numpy array using

```
np_array=df.to_numpy()
```

We will of course lose all the names of columns and rows by applying this conversion.

# 11.1.2 Reading and writing files

Pandas offers interfaces to read and write tabular data with various formats. We can read a CSV file using

```
df=pd.read_csv('distance_height.csv')
```

and the Python specific data format **pickle** can be read by

```
df2=pd.read_pickle('gender_height.pkl')
```

Similarly, we can save dataframe objects to the disk using these formats:

```
df.to_csv('distance_height2.csv')
df2.to_pickle('gender_height2.pkl')
```

# 11.1.3 Selecting and filtering the data

We can select a column by

```
df['height']
```
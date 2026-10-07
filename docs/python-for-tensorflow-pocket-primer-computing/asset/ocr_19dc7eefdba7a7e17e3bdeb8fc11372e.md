```
df = pd.DataFrame({ 'City name': names,'sizes':
sizes })
```

```
print('df:',',df)
```

Listing 3.25 is straightforward: the first portion initializes the Pandas Series names and sizes with cities, and zip codes, respectively. The next portion of Listing 3.25 creates the Pandas DataFrame df with the contents of the series names and sizes. The output from Listing 3.25 is here:

```
('df:',
City name Sizes
0 SF 852469
1 San Jose 1015785
2 Sacramento 485199)
```

# USEFUL ONE-LINE COMMANDS IN PANDAS

This section contains an eclectic mix of one-line commands in Pandas (some of which you have already seen in this chapter) that are useful to know:
 a data frame to a CSV file (comma separated and without indices):

```
df.to_csv("data.csv", sep=",", index=False)
```

List the column names of a DataFrame:

```
df.columns
```

Drop missing data from a DataFrame:

```
df.dropna(axis=0, how='any')
```

Replace missing data in a DataFrame:
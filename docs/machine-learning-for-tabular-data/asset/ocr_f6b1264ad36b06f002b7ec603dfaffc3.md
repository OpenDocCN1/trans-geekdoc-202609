# Exploratory data analysis

The returned results

```
Index(['seville', 'sij', 'skyhawk', 'skylark', 'special', 'spirit', 'sport',
'sportabout', 'squire', 'gst', 'st.', 'stanza', 'starfire', 'starlet',
'strada', 'subari', 'suburb', 'submird', 'super', 'supreme', 'sx', 'tc',
tc3', 'tercel', 'thunderbird', 'torino', 'town', 'toyota', 'toyota',
'tr7', 'triumph', 'turbo', 'type', 'v6', 'v8', 'valiant', 'vega',
ventura', 'vista', 'volkswagen', 'volare', 'volvo', 'vw',
wagon', 'woody', 'xl.9', 'xeer', 'zephyr'], dtype=object)
```

In this data size the words containing the categorical feature, we notice
how brands are misspelled (e.g., Toyota and Toyota, Volkswagen and Volkswagen
but also VW as a shortening). Misspell will split the examples related to a true category
(Volkswagen and Toyota in this case) into multiple categories, putting your model at
risk of picking noisy evidence or discarding weaker signals. The same happens with
other categorical and ordinal features that present erroneous additional categories:

```
data.origin\    .value_counts()
```

The returned results for data origin

+   1. 253
2. 79
3. 73
4. 1
Name: origin, dtype: int64

Let's operate the model for model_year, ordering the results based on the year:

```
data.model_year
    .value_counts()
    .reset_index().rename(columns={'index': 'model_year',
    'model_year': 'counts'})
    .sort_values(by="model_year")
```

2.7 shows how the ordered results for model_year will appear.
Not all these problems with data taken significantly affect the results. However,
the combined presence may affect your model performances in an evident way when
your dataset is composed of tens and features with many problems. Remediation
is simple: just remove the cases with the erroneous labels unless you can
sonably correct them or treat them as missing cases and then impute them. Since they
require inspection and reasoning on every feature, such actions may take considerable
time and effort. Still, you are doing EDA precisely for this purpose, and later, a model
that is more confident and performing in predictions will repay your efforts in full. Tabular data has stronger requirements for the cleanness of data, especially when applying
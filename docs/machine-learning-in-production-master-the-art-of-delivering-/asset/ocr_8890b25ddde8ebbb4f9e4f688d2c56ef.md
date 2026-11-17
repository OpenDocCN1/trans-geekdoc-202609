```
7. 25% 4.750000
8. 50% 5.500000
9. 75% 6.500000
10. max 8.000000
```

```
1. df['fruit']
2. 0 apple
3. 1 banana
4. 2 orange
5. 3 mango
6. Name: fruit, dtype: object
```

# loc - selection by label

A loc gets rows (and/or columns) with specific labels. To get all the rows in which fruit size is medium, loc is written as follows:

# Example: 1.21 Get the data by location

```
1. df.loc[df['size'] == 'medium']
2. fruit size quantity
3. 1 banana medium 4
4. 3 mango medium 6
```

# iloc - selection by position

iloc gets rows (and/or columns) at the index's locations. To get the row at index 2, iloc is written as follows:

# Example: 1.22 Get the data by position

```
1. df.iloc[2]
2. fruit orange
3. size small
4. quantity 8
5. Name: 2, dtype: object
```

To retrieve the rows from index 2 to 3 and columns 0 to 1, iloc is written as follows:

```
1. df.iloc[2:4, 0:2]
2. fruit size
3. 2 orange small
4. 3 mango medium
```
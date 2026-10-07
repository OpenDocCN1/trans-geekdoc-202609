The following code snippet displays the ages of passengers with index values 4 and 5 in the dataset:

```
print("series:", titanic.loc[[4, 5], 'age'])
```

The next snippet displays the age and fare of the passenger index 4 in the dataset, followed by another code snippet displays the age and fare of the passengers with index 4 and index 5 in the dataset.

The final portion of Listing 4.32 is the most interesting part; it defines a variable query as shown here:

```
query = titanic[
    (titanic.sex == 'female')
    & (titanic['class'].isin(['First', 'Third']))
    & (titanic.age > 30)
    & (titanic.survived == 0)
]
```

The preceding code block will retrieve the female passengers who are in either first class or third class, and who are also over 30, and did not survive the accident. The entire output from Listing 4.32 is here:
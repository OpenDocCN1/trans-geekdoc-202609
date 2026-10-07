Listing 3.11 displays the contents of the CSV file people.csv and Listing 3.12 displays the contents of people-pandas.py that illustrates how to define a Pandas DataFrame that reads the CSV file and manipulates the data.

# LISTING 3.11: people.csv

```
fname, lnamename, age, gender, country
john, smith, 30,m, usa
jane, smith, 31, f, france
jack, jones, 32, f, france
dave, stone, 33, f, france
sara, stein, 34, f, france
eddy, bower, 35, f, france
```

# LISTING 3.12: people-pandas.py

```
import pandas as pd
def = pd.read_csv('people.csv')
df.info()
print('fname:')
print(df['fname'])
print('----------------------')
print('age over 33:')
print(df['age'] > 33)
print('----------------------')
print('age over 33:')
myfilter = df['age'] > 33
print(df[myfilter])
```

Listing 3.12 populate the Pandas dataframe df with the contents of the CSV file people.csv. The next portion of Listing 3.12 displays the structure of df, followed by the first names of all the people. The next portion of Listing 3.12 displays a tabular list of six
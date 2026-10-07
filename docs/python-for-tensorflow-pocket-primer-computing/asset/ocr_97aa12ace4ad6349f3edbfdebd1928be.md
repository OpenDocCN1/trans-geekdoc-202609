Listing 3.20 displays the contents of multiple-delims2b.py that reads the contents of multiple-delims2b.dat into a Pandas DataFrame.

# LISTING 3.20: multiple-delims2b.py

```
import pandas as pd

df = pd.read_csv('multiple-delims2b.dat',
                           names=['a', 'b', 'c', 'd'],
                           sep=',', engine='python')

print("dataframe")
print(df)
```

Listing 3.20 imports pandas and then initializes the variable with the contents of the text file multiple-delims2b.dat. That the output from launching the code in Listing 3.20 is here:

| | a | b | c | d |
|---|---|---|---|---|
| 0 | 1000 | Jane | Edwards | Sales |
| 1 | 2000 | Tom | Smith | Development |
| 2 | 3000 | Dave | Del Ray | Marketing |
| 3 | 4000 | Steven | Andrews | Marketing |

Once again, the "heavy lifting" is performed by the cryptic-looking command in the shell script multiple-delims2.sh, which is in Chapter 4 of the following book: Data Cleaning Pocket Primer (ISBN-13: 978-1683922179)

The preceding book contains a detailed explanation of the command that will enable you to understand the contents of multiple-delims2.sh, as well as chapters that discuss the grep and awk commands and numerous examples of how to use them for various data cleaning tasks.

# SELECT, ADD, AND DELETE COLUMNS IN DATAFRAMES
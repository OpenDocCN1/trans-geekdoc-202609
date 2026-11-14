Similar to “NumPy”, the columns of “DataFrame” are also homogeneous.
You can use dictionary like syntax or add the column name with
“DataFrame”, to view the data type of the column, as shown in the code
below:

```
"df['age'].dtype  # Dict Like Syntax
df.age.dtype  # DataFrame.ColumnName
df.name.dtype  # DataFrame.ColumnName"
```

You can use the code below to selectively view the record or rows available
within the “Pandas DataFrame,” by using the “head ( )” function for the
first five rows and “tail ( )” function for the last five rows. For instance, use
the code below to view the first 3 rows of the data:

```
"df.head(3)  # Display first 3 Rows"
```

# Pandas Series

It can be defined as a "one-dimensional labeled array capable of holding
data of any type (integer, string, float, python objects)." Simply put, it is
like a column in an excel spreadsheet. To generate a “Pandas Series” from
an array, a “NumPy” module must be imported and used with “array ()”
function, as shown in the code below:

```
"# import pandas as pd
import pandas as pd"
```

```
"# import numpy as np"
```
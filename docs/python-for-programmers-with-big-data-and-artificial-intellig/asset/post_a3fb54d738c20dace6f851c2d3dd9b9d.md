
## Caution: Missing Commas and Extra Commas in CSV Files

account, name, balance = record

Be careful when preparing and processing CSV files. For example, suppose your file is composed of records, each with *four* comma-separated `int` values, such as:

```
100, 85, 77, 9
```

If you accidentally omit one of these commas, as in:

```
100, 8577, 9
```

then the record has only *three* fields, one with the invalid value `8577`.

If you put two adjacent commas where only one is expected, as in:

```
100, 85, , 77, 9
```

then you have *five* fields rather than *four*, and one of the fields erroneously would be *empty*. Each of these comma-related errors could confuse programs trying to process the record.

### 9.12.2 Reading CSV Files into Pandas DataFrames

In the Intro to Data Science sections in the previous two chapters, we introduced many pandas fundamentals. Here, we demonstrate pandas’ ability to load files in CSV format, then perform some basic data-analysis tasks.

### Datasets

In the data-science case studies, we'll use various free and open datasets to demonstrate machine learning and natural language processing concepts. There’s an enormous variety of free datasets available online. The popular **Rdatasets repository** provides links to over 1100 free datasets in comma-separated values (CSV) format. These were originally provided with the R programming language for people learning about and developing statistical software, though they are not specific to R. They are now available on GitHub at:

https://vincentarelbundock.github.io/Rdatasets/datasets.html

This repository is so popular that there's a **pydataset module** specifically for accessing R datasets. For instructions on installing `pydataset` and accessing datasets with it, see:

https://github.com/iamaziz/PyDataset

Another large source of datasets is:

https://github.com/awesomedata/awesome-public-datasets

A commonly used machine-learning dataset for beginners is the **Titanic disaster dataset**, which lists all the passengers and whether they survived when the ship *Titanic* struck an iceberg and sank April 14–15, 1912. We'll use it here to show how to load a dataset, view some of its data and display some descriptive statistics. We'll dig deeper into a variety of popular datasets in the data-science chapters later in the book.

### Working with Locally Stored CSV Files

You can load a CSV dataset into a `DataFrame` with the pandas function `read_csv`. The following loads and displays the CSV file `accounts.csv` that you created earlier in this chapter:

click here to view code image

```
In [1]: import pandas as pd

In [2]: df = pd.read_csv('accounts.csv',
    ...:                     names=['account', 'name', 'balance'])
    ...:

In [3]: df
Out[3]:
   account   name  balance
0      100  Jones    24.98
1      200   Doe   345.67
2      300  White     0.00
3      400  Stone   -42.16
4      500  Rich   224.62
```

The `names` argument specifies the `DataFrame`'s column names. Without this argument, `read_csv` assumes that the CSV file's first row is a comma-delimited list of column names.

To save a DataFrame to a file using CSV format, call DataFrame method `to_csv`:

click here to view code image

```
In [4]: df.to_csv('accounts_from_dataframe.csv',  index=False)
```

The `index=False` keyword argument indicates that the row names (0–4 at the left of the DataFrame's output in snippet [3]) are not written to the file. The resulting file contains the column names as the first row:

| account,name,balance |
| --- |
| 100,Jones,24.98 |
| 200,Doe,345.67 |
| 300,White,0.0 |
| 400,Stone,-42.16 |
| 500,Rich,224.62 |

### 9.12.3 Reading the Titanic Disaster Dataset

The Titanic disaster dataset is one of the most popular machine-learning datasets. The dataset is available in many formats, including CSV.

### Loading the Titanic Dataset via a URL

If you have a URL representing a CSV dataset, you can load it into a DataFrame with `read_csv`. Let's load the Titanic Disaster dataset directly from GitHub:

click here to view code image

```
In [1]: import pandas as pd

In [2]: titanic = pd.read_csv('https://vincentarelbundock.github.io/' +
    ...:     'Rdatasets/csv/carData/TitanicSurvival.csv')
    ...:
```

### Viewing Some of the Rows in the Titanic Dataset

This dataset contains over 1300 rows, each representing one passenger. According to Wikipedia, there were approximately 1317 passengers and 815 of them died. ³ For large datasets, displaying the `DataFrame` shows only the first 30 rows, followed by “…” and the last 30 rows. To save space, let's view the first five and last five rows with `DataFrame` methods **head** and **tail**. Both methods return five rows by default, but you can specify the number of rows to display as an argument:

3 https://en.wikipedia.org/wiki/Passengers_of_the_RMS_Titanic.

click here to view code image

```
In [3]: pd.set_option('precision', 2) # format for floating-point values

In [4]: titanic.head()
Out[4]:
    Unnamed: 0 survived sex age passengerClass
Allen, Miss. Elisabeth Walton yes female 29.00 1s
Allison, Master. Hudson Trevor yes male 0.92 1s
Allison, Miss. Helen Loraine no female 2.00 1s
Allison, Mr. Hudson Joshua Crei no male 30.00 1s
Allison, Mrs. Hudson J C (Bessi no female 25.00 1s

In [5]: titanic.tail()
Out[5]:
    Unnamed: 0 survived sex age passengerClass
1304 Zabour, Miss. Hileni no female 14.50 3rd
1305 Zabour, Miss. Thamine no female NaN 3rd
1306 Zakarian, Mr. Mapriededer no male 26.50 3rd
1307 Zakarian, Mr. Orin no male 27.00 3rd
1308 Zimmerman, Mr. Leo no male 29.00 3rd
```

Note that pandas adjusts each column’s width, based on the widest value in the column or based on the column name, whichever is wider. Also, note the value in the age column of row 1305 is NaN (not a number), indicating a missing value in the dataset.

### Customizing the Column Names

The first column in this dataset has a strange name (‘Unnamed: 0’). We can clean that up by setting the column names. Let’s change ‘Unnamed: 0’ to ‘name’ and let’s shorten ‘passengerClass’ to ‘class’:

click here to view code image

```
In [6]: titanic.columns = ['name', 'survived', 'sex', 'age', 'class']

In [7]: titanic.head()
Out[7]:
```

| name | survived | sex | age | class |
| :--- | :--- | :--- | :--- | :--- |
| Allen, Miss. Elisabeth Walton | yes | female | 29.00 | 1st |
| Allison, Master. Hudson Trevor | yes | male | 0.92 | 1st |
| Allison, Miss. Helen Loraine | no | female | 2.00 | 1st |
| Allison, Mr. Hudson Joshua Crei | no | male | 30.00 | 1st |
| Allison, Mrs. Hudson J C (Bessi | no | female | 25.00 | 1st |

### 9.12.4 Simple Data Analysis with the Titanic Disaster Dataset

Now, you can use pandas to perform some simple analysis. For example, let’s look at some descriptive statistics. When you call `describe` on a DataFrame containing both numeric and non-numeric columns, `describe` calculates these statistics _only for the numeric columns_—in this case, just the `age` column:

```python
In [8]: titanic.describe()
Out[8]:
       age
count  1046.00
mean    29.88
std     14.41
min      0.17
25%     21.00
50%     28.00
75%     39.00
max     80.00
```

Note the discrepancy in the `count` (1046) vs. the dataset’s number of rows (1309—the last row’s index was 1308 when we called `tail`). Only 1046 (the `count` above) of the records contained an age value. The rest were _missing_ and marked as `NaN`, as in row 1305. When performing calculations, Pandas _ignores missing data_ (`NaN`) _by default_. For the 1046 people with valid ages, the average (`mean`) age was 29.88 years old. The youngest passenger (`min`) was just over two months old (0.17 * 12 is 2.04), and the oldest (`max`) was 80. The median age was 28 (indicated by the 50% quartile). The 25% quartile is the median age in the first half of the passengers (sorted by age), and the 75% quartile is the median of the second half of passengers.

Let’s say you want to determine some statistics about people who survived. We can compare the `survived` column to 'yes' to get a new Series containing `True`/`False` values, then use `describe` to summarize the results:

click here to view code image

```python
In [9]: (titanic.survived == 'yes').describe()
```

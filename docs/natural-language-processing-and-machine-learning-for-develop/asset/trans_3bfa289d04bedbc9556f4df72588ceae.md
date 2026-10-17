
shirts: `type` `ssize` `0` `shirt` `xxlarge` `1` `shirt` `xxlarge` `2` `shirt` `xlarge` `3` `shirt` `xlarge` `4` `shirt` `xlarge` `5` `shirt` `large` `6` `shirt` `medium` `7` `shirt` `small` `8` `shirt` `small` `9` `shirt` `xsmall` `10` `shirt` `xsmall` `11` `shirts starting with xl`: `type` `ssize` `2` `shirt` `xlarge` `3` `shirt` `xlarge` `4` `shirt` `xlarge` `5` `shirt` `large` `6` `shirt` `medium` `7` `shirt` `small` `8` `shirt` `small` `9` `shirt` `xsmall` `10` `shirt` `xsmall` `11` `shirt` `xsmall` `first three letters`: `type` `ssize` `sub1` `0` `shirt` `xxlarge` `xxl` `1` `shirt` `xxlarge` `xxl` `2` `shirt` `xlarge` `xla` `3` `shirt` `xlarge` `xla` `4` `shirt` `xlarge` `xla` `5` `shirt` `large` `lar` `6` `shirt` `medium` `med` `7` `shirt` `small` `sma` `8` `shirt` `small` `sma` `9` `shirt` `xsmall` `xsm` `10` `shirt` `xsmall` `xsm` `11` `shirt` `xsmall` `class_Section-header_1'>**Converting Strings to Dates in Pandas**<class_Section-header>

[Listing 2.12](#ch02.xhtml#list2.12) displays the contents of `string2date.py` that illustrates how to convert strings to date formats.

***LISTING 2.12: string2date.py***

```python
import pandas as pd
bdates1 = {'strdates': ['20210413','20210813','20211225'], 'people': ['Sally','Steve','Sarah']}
df1 = pd.DataFrame(bdates1, columns=['strdates','people'])
df1['dates'] = pd.to_datetime(df1['strdates'], format='%Y%m%d')
print("=> Contents of data frame df1:")
print(df1)
print()
print(df1.dtypes)
print()

bdates2 = {'strdates': ['13Apr2021','08Aug2021','25Dec2021'], 'people': ['Sally','Steve','Sarah']}
df2 = pd.DataFrame(bdates2, columns=['strdates','people'])
df2['dates'] = pd.to_datetime(df2['strdates'], format='%d%b%Y')
print("=> Contents of data frame df2:")
print(df2)
print()
print(df2.dtypes)
```

[Listing 2.12](#ch02.xhtml#list2.12) initializes the data frame `df1` with the contents of `bdates1`, and then converts the `strdates` column to dates using the `'%Y%m%d'` format. The next portion of [Listing 2.12](#ch02.xhtml#list2.12) initializes the data frame `df2` with the contents of `bdates2`, and then converts the `strdates` column to dates using the `'%d%b%Y'` format. Now launch the code in [Listing 2.12](#ch02.xhtml#list2.12) and you will see the following output:

```
=> Contents of data frame df1:
   strdates people       dates
0  20210413   Sally 2021-04-13
1  20210813  Steve 2021-08-13
2  20211225  Sarah 2021-12-25
strdates       object people        object
dates    datetime64[ns] dtype: object

=> Contents of data frame df2:
   strdates people       dates
0  13Apr2021   Sally 2021-04-13
1   08Aug2021  Steve 2021-08-08
2  25Dec2021  Sarah 2021-12-25
strdates       object people        object
dates    datetime64[ns] dtype: object
```

## **Merging and Splitting Columns in Pandas**

[Listing 2.13](#ch02.xhtml#list2.13) displays the contents of `employees.csv` and [Listing 2.14](#ch02.xhtml#list2.14) displays the contents of `emp_merge_split.py` that illustrates how to merge columns and split columns of a CSV file.

***LISTING 2.13: employees.csv***

```csv
name,year,month
Jane-Smith,2015,Aug
Dave-Smith,2020,Jan
Jane-Jones,2018,Dec
Jane-Stone,2017,Feb
Dave-Stone,2014,Apr
Mark-Aster,,Oct
Jane-Jones,NaN,Jun
```

***LISTING 2.14: emp_merge_split.py***

```python
import pandas as pd
emps = pd.read_csv("employees.csv")
print("emps:")
print(emps)
print()

emps['year'] = emps['year'].astype(str)
emps['month'] = emps['month'].astype(str)

# separate column for first name and for last name:
emps['fname'],emps['lname'] = emps['name'].str.split("-",1).str

# concatenate year and month with a "#" symbol:
emps['hdate1'] = emps['year'].astype(str)+"#"+emps['month'].astype(str)

# concatenate year and month with a "-" symbol:
emps['hdate2'] = emps[['year','month']].agg('-'.join, axis=1)

print(emps)
```

[Listing 2.14](#ch02.xhtml#list2.14) initializes the data frame `df` with the contents of the CSV file `employees.csv`, and then displays the contents of `df`. The next pair of code snippets invoke the `astype()` method to convert the contents of the `year` and `month` columns to strings.

The next code snippet in [Listing 2.14](#ch02.xhtml#list2.14) uses the `split()` method to split the `name` column into the columns `fname` and `lname` that contain the first name and last name, respectively, of each employee’s name:

`emps['fname'],emps['lname'] = emps['name'].str.split("-",1).str`

The next code snippet concatenates the contents of the `year` and `month` string with a “#” character to create a new column called `hdate1`, as shown here:

`emps['hdate1'] = emps['year'].astype(str)+"#"+emps['month'].astype(str)`

The final code snippet concatenates the contents of the `year` and `month` string with a “-” to create a new column called `hdate2`, as shown here:

`emps['hdate2'] = emps[['year','month']].agg('-'.join, axis=1)`

Now launch the code in [Listing 2.14](#ch02.xhtml#list2.14) and you will see the following output:

```
emps:
    name  year month  fname  lname    hdate1    hdate2
0  Jane-Smith  2015   Aug  Jane  Smith  2015#Aug  2015-Aug
1  Dave-Smith  2020   Jan  Dave  Smith  2020#Jan  2020-Jan
2[[content><class_Section-header_1>##' (inside) 

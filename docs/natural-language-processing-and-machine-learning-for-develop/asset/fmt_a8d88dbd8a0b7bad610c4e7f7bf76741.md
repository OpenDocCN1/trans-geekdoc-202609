
\=> contents of CSV file:         name    year month 0  Jane-Smith  2015.0   Aug 1  Jane-Smith  2015.0   Aug 2  Dave-Smith  2020.0   NaN 3  Dave-Stone     NaN   Apr 4  Jane-Jones  2018.0   Dec 5  Jane-Stone  2017.0   Feb 6  Jane-Stone  2017.0   Feb 7  Mark-Aster     NaN   Oct 8  Jane-Jones     NaN   Jun 

\=> Check for NANs:    name   year  month 0  False  False  False 1  False  False  False 2  False  False   True 3  False   True  False 4  False  False  False 5  False  False  False 6  False  False  False 7  False   True  False 8  False   True  False   \=> Drop missing data:         name    year month 0  Jane-Smith  2015.0   Aug 1  Jane-Smith  2015.0   Aug 4  Jane-Jones  2018.0   Dec 5  Jane-Stone  2017.0   Feb 6  Jane-Stone  2017.0   Feb   \=> Replace missing data:         name    year month 0  Jane-Smith  2015.0   Aug 1  Jane-Smith  2015.0   Aug 2  Dave-Smith  2020.0  7777 3  Dave-Stone  7777.0   Apr 4  Jane-Jones  2018.0   Dec 5  Jane-Stone  2017.0   Feb 6  Jane-Stone  2017.0   Feb 7  Mark-Aster  7777.0   Oct 8  Jane-Jones  7777.0   Jun 

## **Sorting Data Frames in Pandas**

[Listing 2.36](#ch02.xhtml#list2.36) displays the contents of sort_df.py that illustrates how to sort the rows in a Pandas data frame.

***LISTING 2.36: sort_df.py***

```python
import pandas as pd
df = pd.read_csv("duplicates.csv")
print("Contents of data frame:")
print(df)
print()
df.sort_values(by=['fname'], inplace=True)
print("Sorted (ascending) by first name:")
print(df)
print()
df.sort_values(by=['fname'], inplace=True, ascending=False)
print("Sorted (descending) by first name:")
print(df)
print()
df.sort_values(by=['fname','lname'], inplace=True)
print("Sorted (ascending) by first name and last name:")
print(df)
print()
```

[Listing 2.36](#ch02.xhtml#list2.36) initializes the data frame df with the contents of the CSV file duplicates.csv, and then displays the contents of df. The next portion of [Listing 2.36](#ch02.xhtml#list2.36) displays the rows in ascending order based on the first name, and the next code block displays the rows in descending order based on the first name.

The final code block in [Listing 2.36](#ch02.xhtml#list2.36) displays the rows in ascending order based on the first name as well as the last name. Launch the code in [Listing 2.36](#ch02.xhtml#list2.36) and you will see the following output:

Contents of data frame:   fname  lname   level    dept       state 0  Jane  Smith  Senior   Sales  California 1  Dave  Smith  Senior   Devel  California 2  Jane  Jones   Year1   Mrktg    Illinois 3  Jane  Jones   Year1   Mrktg    Illinois 4  Jane  Stone  Senior   Mrktg     Arizona 5  Dave  Stone   Year2   Devel     Arizona 6  Mark  Aster   Year3  BizDev     Florida 7  Jane  Jones   Year1   Mrktg    Illinois   Sorted (ascending) by first name:   fname  lname   level    dept       state 1  Dave  Smith  Senior   Devel  California 5  Dave  Stone   Year2   Devel     Arizona 0  Jane  Smith  Senior   Sales  California 2  Jane  Jones   Year1   Mrktg    Illinois 3  Jane  Jones   Year1   Mrktg    Illinois 4  Jane  Stone  Senior   Mrktg     Arizona 7  Jane  Jones   Year1   Mrktg    Illinois 6  Mark  Aster   Year3  BizDev     Florida   Sorted (descending) by first name:  fname  lname   level    dept       state 6  Mark  Aster   Year3  BizDev     Florida 0  Jane  Smith  Senior   Sales  California 2  Jane  Jones   Year1   Mrktg    Illinois 3  Jane  Jones   Year1   Mrktg    Illinois 4  Jane  Stone  Senior   Mrktg     Arizona 7  Jane  Jones   Year1   Mrktg    Illinois 1  Dave  Smith  Senior   Devel  California 5  Dave  Stone   Year2   Devel     Arizona   Sorted (ascending) by first name and last name:   fname  lname   level    dept       state 1  Dave  Smith  Senior   Devel  California 5  Dave  Stone   Year2   Devel     Arizona 2  Jane  Jones   Year1   Mrktg    Illinois 3  Jane  Jones   Year1   Mrktg    Illinois 7  Jane  Jones   Year1   Mrktg    Illinois 0  Jane  Smith  Senior   Sales  California 4  Jane  Stone  Senior   Mrktg     Arizona 6  Mark  Aster   Year3  BizDev     Florida 

## **Working with groupby() in Pandas**

[Listing 2.37](#ch02.xhtml#list2.37) displays the contents of groupby1.py that illustrates how to invoke the Pandas groupby() method in order to compute subtotals of feature values.

***LISTING 2.37: groupby1.py***

```python
import pandas as pd
# colors and weights of balls: data = { 'color':\['red','blue','blue','red','blue'\],         'weight':\[40,50,20,30,90\]} df1 = pd.DataFrame(data)
print("df1:")
print(df1)
print()
print(df1.groupby('color').mean())
print()
red_filter = df1['color']=='red'
print(df1[red_filter])
print()
blue_filter = df1['color']=='blue'
print(df1[blue_filter])
print()
red_avg = df1[red_filter]['weight'].mean()
blue_avg = df1[blue_filter]['weight'].mean()
print("red_avg,blue_avg:")
print(red_avg,blue_avg)
print()
df2 = pd.DataFrame({'color':\['blue','red'\],'weight':\[red_avg,blue_avg\]})
print("df2:")
print(df2)
print()
```

[Listing 2.37](#ch02.xhtml#list2.37) defines the variable data containing color and weight values, and then initializes the data frame df with the contents of the variable data. The next two code blocks define red_filter and blue_filter that match the rows whose colors are red and blue, respectively, and then prints the matching rows.

The next portion of [Listing 2.37](#ch02.xhtml#list2.37) defines the two filters red_avg and blue_avg that calculate the average weight of the red value and the blue values, respectively. The last code block in [Listing 2.37](#ch02.xhtml#list2.37) defines the data frame df2 with a color color and a weight column, where the latter contains the average weight of the red values and the blue values. Launch the code in [Listing 2.37](#ch02.xhtml#list2.37) and you will see the following output:

initial data frame: df1:  color  weight 0   red      40 1  blue      50 2  blue      20 3   red      30 4  blue      90            weight color           blue   53.333333 red    35.000000    color  weight 0  red      40 3   red      30    color  weight 1  blue      50 2  blue      20 4  blue      90   red_avg,blue_avg: 35.0 53.333333333333336   df2:  color     weight 0  blue  35.000000 1   red  53.333333 

## **Working with apply() and mapapply() in Pandas**

Earlier in this chapter you saw an example of the Pandas apply() method for modifying the categorical values of a feature in the CSV file shirts.csv. This section contains more examples of the apply() method.

[Listing 2.38](#ch02.xhtml#list2.38) displays the contents of apply1.py that illustrates how to invoke the Pandas apply() method in order to compute the cube of a column of numbers.

***LISTING 2.38: apply1.py***

```python
import pandas as pd
df = pd.DataFrame({'X1': \[1,2,3\], 'X2': \[10,20,30\]})
def cube(x):
    return x * x * x
df1 = df.apply(cube) # same result:
# df1 = df.apply(lambda x: x * x * x)
print("initial data frame:")
print(df)
print("cubed values:")
print(df1)
```

[Listing 2.38](#ch02.xhtml#list2.38) initializes the data frame df with columns X1 and X2, where the values for X2 are 10 times the corresponding values in X1. Next, the Python function cube() returns the cube of its argument. [Listing 2.38](#ch02.xhtml#list2.38) then defines the variable df1 by invoking the apply() function, which specifies the user-defined Python function cube(), and then prints the values of df as well as df1. Launch the code in [Listing 2.38](#ch02.xhtml#list2.38) and you will see the following output:

initial data frame:    X1  X2 0   1  10 1   2  20 2   3  30 cubed values:    X1     X2 0   1   1000 1   8   8000 2  27  27000 

Apply a function to a Data frame that multiplies all values in the “height” column of the data frame by 3:

df\["height"\].apply(lambda height: 3 \* height) 

OR:

def multiply(x):    return x \* 3 df\["height"\].apply(multiply) 

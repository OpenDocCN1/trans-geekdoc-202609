The example in Code Listing 57 is the same as Code Listing 56 but uses **fetchInto()** rather than **fetchRow()**. The output is shown in Output 31. The one notable difference in the output is that the last line seems to indicate that there is data in the row indexed by *rownum* 7. However the output is generated because the argument passed in line 26 of the code ($aRow) is already set to a value because of its use on line 24.

> This is an important difference between **fetchRow()** and **fetchInto()** that you must consider if you choose to use the **fetchInto()** method. Always clear the variable you pass as the first parameter to **fetchInto()** or you may end up with residual data.

```
1 Blake Schwendiman
2 Jeffrey Cox
3 Kate McNulty
4 Ryan Schwendiman
5 Scott Schwendiman
6 Taylor Schwendiman
7
8 By rownum:
9
10 Jeffrey Cox
11 Ryan Schwendiman
12 Taylor Schwendiman
13 Taylor Schwendiman
```

Output 31: Results of fetchInto example (Code Listing 57).

Returns null or DB_OK.

# DB_result::numCols

```
mixed numCols( void )
```

Use the **numCols()** method to return the number of columns in the result set. A usage example is given in Code Listing 58 on page 117.
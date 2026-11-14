The leftmost column is the key. A key column contains a unique identification for each record. Keys can be anything from a simple record number to a Social Security number, student ID, or SKU. As you'll see, VLOOKUP requires a table of this layout.

The breakdown of VLOOKUP looks like this:

```
VLOOKUP(what you're looking for, the entire table of where you're looking, the column (s) of interest, whether to perform an exact or approximate match)
```

Let's take a look at each of these:

+   - what you're looking for: This is your search term. In the case of VLOOKUP, it'll be the specific key you're looking for.
+   - The entire table of where you're looking: This is a reference to the entire table where you're looking, including the key column.
+   - the column(s) of interest: This is where you identify the columns you'd like to return.
+   - whether to perform an exact or approximate match: VLOOKUP allows you to either match the key exactly or approximately match it. In this book, we won't be dealing with approximate match. So, whenever you use VLOOKUP from examples in this book, make sure the last parameter is always a zero or a FALSE (which mean the same thing in Excel). This tells Excel we always want exact matching.

VLOOKUP works by matching the search term to the key along the table's left side. Once the match is found, the key effectively “unlocks” the record. You can tell VLOOKUP what to return from the record by specifying the desired return column numbers in the column of interest parameter.

Enough talk—let's see it in Excel. In the Concessions file, select the Calories Worksheet tab. Note there is already a table there named NutritionInfo. In Figure 1.16, I've implemented the following formula in cell B19:

```
=VLOOKUP("Hot Dog", NutritionInfo, 2, FALSE)
```

As you can see, Hot Dog is the unique key. Once the VLOOKUP finds the key in the table, it returns the value associated with the column number provided. In this case, the 2 passed into the third parameter of the formula indicates we want the information from the second column.
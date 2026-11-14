
This works out really well for the associated function, INDEX. INDEX takes in a row, column, or table of data, and lets you supply the coordinates of where you want to look. In that way, it functions like a reverse lookup. Let's take a look at INDEX:

```
=INDEX(table or column of interest, row of interest, column of interest)
```

- table or column of interest: This is a cell or table reference to a table or column.
- row of interest: If you supply a 4 here, the fourth record within the column or table is returned. In this case, we'll place the results of our MATCH function here since that returns the record location.
- column of interest: This is an optional parameter. In this case, we're using data of only one dimension (rows or columns), so we don't need this. However, if you would like to look up values across an entire table, this parameter is very useful.

Once we know where the record is located using MATCH, we can figure out the key to the associated person using INDEX. Let's see this in action in Excel.

Let's say we want to know which item has the most calories. In cells B22:24, I have broken down the steps to complete this formula (see Figure 1.18). In B22, we find the maximum calories from the NutritionInfo[Calories] column. In B23, we use MATCH to find where this value is located. Excel returns a 10. Finally, in B24, we use INDEX to look up the 10th record from NutritionInfo's Item column field. In B25, I've combined the formula into one.

```
=INDEX(NutritionInfo[Item], MATCH(MAX(B22), NutritionInfo[Calories], 0))
```

![](img/9c4b3d77873bec9e7da149a75c568d36_39_0.png)

Figure 1.18: INDEX/MATCH has been across helper cells B22:B24. It's also implemented as one formula in B25.

Combining lots of functions together is hard to read, so press Alt+Enter (Option+Return on a Mac) while in the formula bar to go to a new line. It will look like the following code. We'll be doing that for long formulas in this book.

```
=INDEX(
    NutritionInfo[Item],
    MATCH(MAX(B22),NutritionInfo[Calories],0)
)
```

## USE LET TO AVOID REPEATING MULTIPLE COLUMNS

Take a look at the INDEX/MATCH function we wrote:

```
=INDEX(NutritionInfo[Item], MATCH(MAX(NutritionInfo[Calories]),
    NutritionInfo[Calories], 0))
```

Notice that we have to repeat the column NutritionInfo[Calories] for this problem. It's not uncommon to have to repeat multiple references and functions in Excel, especially when working with complicated datasets.

If you have the most updated version of Excel 365, you can use the LET function to help you stay more organized. LET allows you to declare a variable that exists only within the formula. For instance, we could use this instead to make the formula more readable:

```
= LET(
    CaloriesColumn, NutritionInfo[Calories],
    INDEX(NutritionInfo[Item],
    MATCH(MAX(CaloriesColumn),CaloriesColumn, 0)
    )
)
```

Notice how we replace NutritionInfo[Calories] info with the CaloriesColumn variable. We'll be using LET quite a bit in this book.

## XLOOKUP

For many years, VLOOKUP and INDEX/MATCH were the mainstays of Excel developers. But as you can see, both have issues: with a VLOOKUP you need to know the column index of interest. And INDEX/MATCH just feels needlessly complicated. As a result, Microsoft released a new function that can do what VLOOKUP and INDEX/MATCH do but better.

You might be wondering why I'm even bringing up VLOOKUP and INDEX/MATCH if a better alternative is out there. The answer is that while XLOOKUP is considered generally available, not everyone has it yet. XLOOKUP is technically slower than INDEX/MATCH, so sometimes you might prefer the latter to save calculation time.

For those with XLOOKUP, this section is for you. For those who don't have it yet (you'll know you don't have it when it doesn't work), make sure you're using the latest version of Excel or Office 365.

XLOOKUP is effectively the best of both worlds. While there are many options in the XLOOKUP function, you really need to know only three things to get started: what you're looking for, the column of where you want to look, and the return column where the cell you return resides. Take a look at the representation in Figure 1.19.

![](img/9c4b3d77873bec9e7da149a75c568d36_41_0.png)

Figure 1.19: The elements required to implement an XLOOKUP

Let's implement XLOOKUP in Excel. Take a look at cell B28 in Figure 1.20. In this case, the goal is again to find the item with the most calories, this time using XLOOKUP. The following is the formula we use:

```
=XLOOKUP(MAX(NutritionInfo[Calories]), NutritionInfo[Calories],
NutritionInfo[Item])
```

Notice that XLOOKUP contains many of the same elements of the INDEX/MATCH solution— it's just more condensed.

Once you understand lookup formulas, you're ready to move on to PivotTables.

## PivotTables

What if you wanted to know the total counts of each item type you sold? Or you wanted to know revenue totals by item?

These questions are akin to “aggregate” or “group by” queries, which are a key element of descriptive analytics. The goal of descriptive analytics is to take large columns of data and push them through aggregator functions to get just a few descriptive numbers. PivotTables help us do this by grouping together different elements of a dataset and applying some type of aggregation function like SUM, MIN, COUNT, and others.

| Item | Calories | Formula |
| :--- | :--- | :--- |
| Beer | 200 | |
| Bottled Water | 0 | |
| Chocolate Bar | 255 | |
| Chocolate Dipped Cone | 300 | |
| Gummy Bears | 300 | |
| Hamburger | 320 | |
| Hot Dog | 265 | |
| Ice Cream Sandwich | 240 | |
| Licorice Rope | 280 | |
| Nachos | 560 | |
| Pizza | 480 | |
| Popcorn | 500 | |
| Popsicle | 150 | |
| Soda | 120 | |
| How many calories are in a Hot Dog? | | |
| VLOOKUP | 265 | =VLOOKUP("Hot Dog", NutritionInfo, 2,FALSE) |
| Which item has the most calories? | | |
| MAX | 560 | =MAX(NutritionInfo[Calories]) |
| MATCH | 10 | =MATCH(B22,NutritionInfo[Calories],0) |
| INDEX | Nachos | =INDEX(NutritionInfo[Item],B23) |
| INDEX/MATCH | Nachos | =INDEX(NutritionInfo[Item], MATCH(MAX(NutritionInfo[Calories]), NutritionInfo[Calories], 0)) |
| Which item has the most calories? | | |
| XLOOKUP | Nachos | =XLOOKUP(MAX(NutritionInfo[Calories]),NutritionInfo[Calories],NutritionInfo[Item]) |

**Figure 1.20:** XLOOKUP is implemented in cell B28. Notice the XLOOKUP formula uses many of the same cell references as INDEX/MATCH but gets to the answer in fewer steps.

To apply a PivotTable, go back to your Basketball Game Sales sheet and click into the Sales table. On the Insert tab, click PivotTable. Click OK to create a new sheet for the PivotTable.¹

In this new sheet, the PivotTable Builder will appear on the right side of the screen. The builder allows you to take the columns from the original selected data and use them as report filters, column and row labels for grouping, or values for aggregating.

Now, say you wanted to know total revenue by item. To get at that, you drag the Item title in the PivotTable Builder into the Rows section and the Price tile into the Values section. This means that you’ll be operating on revenue grouped by item name. This is shown in Figure 1.21.

¹ A PivotTable joke: A PivotTable walks into a bar. The bartender says, “should I start a new tab?”

![](img/9c4b3d77873bec9e7da149a75c568d36_43_0.png)

**Figure 1.21:** The PivotTable Builder and a count of sales by item

What if you wanted to break out these sums by category? Simply drag the Category tile into the Columns section of the builder. This gives the table shown in Figure 1.22. Note that the PivotTable in the figure automatically totals up rows and columns for you.

If you want to ever get rid of something from the table, just uncheck it or grab the tile from the section it's in and drag it out of the builder as if you were tossing it away. Go ahead and drop the Category tile. Feel free to swap in various row and column labels until you get the hang of what's going on. For instance, try to get a total calorie count sold by category using a PivotTable. When you're done with the PivotTable, change the worksheet tab name to “Pivot” to stay organized.

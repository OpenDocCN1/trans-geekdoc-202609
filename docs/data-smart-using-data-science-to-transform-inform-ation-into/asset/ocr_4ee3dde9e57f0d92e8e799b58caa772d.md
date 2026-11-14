To delete this column, simply right-click the column header of Column F and select Delete.

Excel tables are a wonderful tool in Excel, and as you can see, they fix many of the issues described at the start of this section. For the rest of this book, we'll work with a mix of cell references and the structured references of tables. We'll choose the one that makes the most sense given the situation. As we go through the book, you'll see how best to use each type.

> > **TIP**
> > I would love to further extol Excel tables, but unfortunately there’s a page limit from the publisher. If you’d like to master Excel tables, see these books:
> > * Excel Tables: A Complete Guide for Creating, Using and Automating Lists and Tables by Zack Barresse and Kevin Jones (Holy Macro Books, 2014).
> > * Excel 2019 Bible by Michael Alexander, Richard Kusleika, and John Walkenbach (Wiley, 2018)

# # Lookup Formulas

Lookup formulas are very important in data analysis. They allow us to find out information about one or more records as well as join information from different tables.

There are multiple lookup functions in Excel. However, the ones we’re most concerned with are `VLOOKUP`, `INDEX/MATCH`, and the venerable `XLOOKUP`. To understand each function, let’s understand why they exist and the workflows they are designed to solve.

# # VLOOKUP

Let's start with `VLOOKUP`. `VLOOKUP`s exist because of a specific data workflow. For instance, sometimes you will receive data that looks like in Figure 1.15.

| Key | Value1 | Value2 | Value3 |
|---|---|---|---|
| 4524 | ... | ... | ... |
| 2352 | ... | ... | ... |
| 1834 | ... | ... | ... |
| 3271 | ... | ... | ... |

**Figure 1.15:** A table layout where the unique identifier the “key” is the leftmost column
complete row of information first (all of Pete Smith's information) before storing another row of information. This again, maps to the operating system storing all the related information into the same general location of memory before it save the next row of information (possibly at a completely different location in memory).

**All this just leads us to remember to always list the first row, and then the column when saving or retrieving information in a two-dimensional array.**

```
$customer_record[0];
```

In chapter 1, we discovered that the statement above would print out the first name of the customer ('Pete'). However, if the array is two-dimensional, this statement will pull the complete first row, instead of the first record. To read a specific record, both the row and column must be specified.

```
$customer_record[1][0];
```

In this statement, the first subscript indicates the row (1), and the second subscript indicates the column (0). If the table shown previous is an array, this statement would print Sally.

What would $customer_record[2][4]; display GA

To dynamically create a two-dimensional array in PHP, we use almost the same statements that we used for a single dimension.

```
$customer_record[0][0] = "Pete";
$customer_record[0][1] = "Smith";
$customer_record[0][2] = "123 Main Street";
$customer_record[0][3] = "Atlanta";
$customer_record[0][4] = "GA";
$customer_record[0][5] = 30001;
$customer_record[1][0] = "Sally";
$customer_record[1][1] = "Parisi";
$customer_record[1][2] = "101 South Street";
$customer_record[1][3] = "Atlanta";
$customer_record[1][4] = "GA";
$customer_record[1][5] = 30001;
```

Let's look at what we see when we use the print_r method on the array we just
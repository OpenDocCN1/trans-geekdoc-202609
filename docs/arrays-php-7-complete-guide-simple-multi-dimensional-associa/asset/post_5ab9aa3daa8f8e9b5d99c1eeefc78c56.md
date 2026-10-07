
## Chapter 2 – Multi-dimensional Arrays

After completing this chapter, the student will be able to...

- Define and describe the advantages in using multi-dimensional arrays
- Compare a table with a multi-dimensional array
- Create a multi-dimensional PHP array
- Save values into a multi-dimensional PHP array
- Display values in a multi-dimensional array
- Add values from an html form into a multi-dimensional array
- Validate values before placing them into a multi-dimensional array
- Convert JSON data read from a text file into a PHP array
- Convert PHP arrays to JSON objects and save to a text file
- Save array information to a MySQL Database

The previous chapter showed how efficient arrays can be.
However, the question that was not answered

> “How do we handle data from multiple customers?”

A simple array holds information that is related a particular individual component, such as a customer. In order to hold all customers information in memory, we must think in more than one dimension. We need to have the ability to hold multiple components of customer information. We can think of a doctor’s office (before everything became computerized) keeping records of each patient in a file, with all the files for all patients stored within a file cabinet.

Multi-dimensional arrays work in a similar way. A customer’s information is stored in a ‘record’ (similar to the file in the doctor’s office). In our previous example, all of the information related to Fred Smith is kept together in a ‘record’. Multiple records (just like the file cabinet) are kept together in a ‘table’. The ‘table’ would contain all of the customer records.

Spreadsheets work in the same way.

# Figure 2-1 Customers Table

| "Pete" "Smith" | "123 Main Street" |
| :--- | :--- |
| "Atlanta" | "GA" 30001 |
| "Sally" "Parisi" | "101 South Street" |
| "Atlanta" | "GA" 30001 |
| "Jake" "Boukari" | "111 Peachtree Street" |
| "Atlanta" | "GA" 30011 |
| "Cap" "Hill" | "1112 Peachtree Road" |
| "Atlanta" | "GA" 30018 |

In 2-1, four customers exist within the table. In a spreadsheet or in a program, the information for each customer is contained in a *record* (also referred to as a row). Each row has the same type of information in each *column*. For example, the *first column* contains the first name of each of the customers.

This table contains six columns and four rows. However, remember that spreadsheets and programs begin the numbering of elements with zero, not one. The uppermost left element (which contains “Pete”) resides in row zero and column zero (0, 0). The lowermost right element (30018) resides in row three and column five (3, 5).

What resides in row 2 and column 2? “111 Peachtree Street"
Why do we say row x and column y, not column y and row x?

The answer lies in how the information is stored in memory. The operating system stores two dimensional arrays by row. The rows are kept intact because everything in a row is related (all of *Pete Smith’s* information). The row information is placed in memory locations that are contiguous to each other (next to each other). Other rows are not necessarily stored in memory next to previous rows. This allow the operating system to be efficient with memory storage.

When retrieving data from a *two-dimensional array*, we usually retrieve or look at a row of information at a time (such as all of *Pete Smith’s* information). In turn allows the operating system to go to one continuous area of memory to pull the information. When a column of information is needed, less efficiently occurs, because the operating system might need to go to several noncontiguous locations in memory to retrieve the information.

When we store information into a table, or array, we also (usually) store a complete row of information first (all of Pete Smith's information) before storing another row of information. This again, maps to the operating system storing all the related information into the same general location of memory before it save the next row of information (possibly at a completely different location in memory).

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

Let's look at what we see when we use the print_r method on the array we just created.

```php
print_r($customer_record);

Array (
[0] => Array ( [0] => Pete [1] => Smith [2] => 123 Main Street [3] => Atlanta [4] => GA [5] => 30001 )
[1] => Array ( [0] => Sally [1] => Parisi [2] => 101 South Street [3] => Atlanta [4] => GA [5] => 30001 )
```

Note: The print_r method will display the information about without the line breaks that have been added.

The outside array (Array ( ) controls the rows, which are actually their own arrays. In this example, there are two rows indicated by [0]=> and [1]=> on the lines by themselves. Inside of each row is an Array that controls the columns for row. The first Array contains information about Pete Smith. The second Array contains information about Sally Parisi. You should notice that these arrays are exactly the same format as the one dimensional array that we discussed in chapter 1. In PHP, two-dimensional arrays are actually individual one-dimensional arrays held together by an array that surrounds them.

We can create this two dimensional array without specifying the subscript numbers (as shown with one dimensional arrays)?

When using the dynamic approach of creating the positions when needed, we have to tell PHP when to start a new array or row (when to switch to which array contains the Pete information to the array that contains the Sally information). One way we can do this by using a counting variable.

Example 2-1 process_customer_twodim.php

```php
<?php
$I = -1;
$customer_record[+$I][][] = 'Pete';
$customer_record[$I][] = 'Smith';
$customer_record[$I][] = '123 Main Street';
$customer_record[$I][] = 'Atlanta';
$customer_record[$I][] = 'GA';
$customer_record[$I][] = 30001;
$customer_record[+$I][][] = 'Sally';
$customer_record[$I][] = 'Parisi';
$customer_record[$I][] = '101 South Street';
$customer_record[$I][] = 'Atlanta';
$customer_record[$I][] = 'GA';
$customer_record[$I][] = 30001;
print_r($customer_record);
?>
```

In Example 2-1, A counting variable $I is created with an initial value of -1. In the next statement, the variable is incremented before it is used (++$I). The value in the (0) is used to define the initial subscript for the array containing the information for Pete. The remaining values for Pete are placed into the related array using $I, which is still set to 0. When it is time to create the array holding the information for Sally, the counting variable is again incremented. This provides a subscript of 1 for each value placed in the Sally array. Notice that we did not need to provide a value for any of the positions with the Pete or Sally array.

However, this is not the most efficient way! This not good coding. Don't create your two-dimensional arrays using this example!

What would happen if we didn't place the counting variable or a number in the first subscript positions (such as $customer_record[$][] = 'Pete');

Each value for Sally would end up with its own array and only one subscript. Each of the two subscripts would increment each time. Download Example 2-1 and remove every place that $I occurs and run the program to see the mess it would eliminate the need for the counting variable if we define the complete array at one time.

```php
$customer_record = array (
array('Pete', 'Smith', '123 Main Street', 'Atlanta', 'GA', 30001),
array('Sally', 'Parisi', '101 South Street', 'Atlanta', 'GA', 30001)
);
```

This approach is a lot more efficient; taking a lot less lines of code to create. It

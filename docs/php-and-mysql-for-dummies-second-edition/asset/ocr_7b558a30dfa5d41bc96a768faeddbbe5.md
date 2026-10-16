![](bbox=[0.23, 0.13, 0.86, 0.51])

Figure 8-1:
The Web page resulting from pet Display.php.

The program in Listing 8-1 uses a while loop to get all the rows from the temporary location. In some cases, you might need to use a for loop. For instance, if you need to use a number in your loop, a for loop is more useful than a while loop.

To use a for loop, you need to know how many rows of data were selected. You can find out how many rows are in the temporary storage by using the PHP function mysql_num_rows as follows:

```
$nrows = mysql_num_rows($result);
```

The variable $nrows contains the number of rows in the temporary storage location. By using this number, you can build a for loop to get all the rows, as follows:

```
for ($i=0;$i<$nrows;$i++)
{
    $row = mysql_fetch_array($result)
    block of statements;
}
```

For instance, the program in Listing 8-1 displays the Pet items of the type horse. Suppose that you want to number each item. Listing 8-2 shows a program, petDescripFor.php, which displays a numbered list by using a for loop.
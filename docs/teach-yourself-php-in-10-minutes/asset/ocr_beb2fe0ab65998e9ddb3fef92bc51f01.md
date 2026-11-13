The complementary functions to `fgets` and `fread` to perform write operations on a file pointer are `fputs` and `fwrite`. These functions are actually identical to one another, with the newline character treated just like any other character as they are written to the file.

The following example opens a file and writes to it the current time:

```
$fp = fopen("time.txt", "w");
fwrite($fp, "Data written at ".date("H:i:s"));
fclose($fp);
```

Remember that the apache user needs to have write permissions on the directory in order to create a new file.

If you examine the new `time.txt` file, you will see that it does indeed contain the current time.

# Working with Data Files

One of the reasons you might need to access the filesystem from PHP is to load data from a structured file format into your script. One of the easiest file formats to use is comma-separated values (CSV).

Although it would appear to be fairly easy to read a line of the file at a time and call `explode` to break up the line where each comma appears, this would not work where data elements in the CSV file contain commas. If you export data from a spreadsheet, columns containing commas are usually enclosed in quotes, so you need quite a complex rule to manipulate the data successfully.

Fortunately, PHP includes the function `fgetcsv`. It works in a similar way to `fgets`, except that an array is returned, containing one element for each comma-separated value in the list. The size argument to `fgetcsv` is optional as of PHP 5.

Often the first line of a CSV file contains the column headings. If you know that this is the case, you should discard the file line before processing the data file. The following example reads a comma-separated data file and dumps each record to screen by using `print_r`:

```
$fp = fopen("data.csv", "r");
while ($record = fgetcsv($fp, 1000)) {
echo $chunk;
}
```

![](bbox=[0.11, 0.76, 0.17, 0.81])

> **Reading CSV Files** The `fgetcsv` function requires a line length argument, just like `fgets`. In the previous example, this has an arbitrary value of `1000`, but you should ensure that whatever value you use is larger than the longest line in your data file.
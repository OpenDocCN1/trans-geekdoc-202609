# Reading from a CSV File

Now let's read the CSV data from the file. The following snippet reads records from the file accounts.csv and displays the contents of each record, producing the same output we showed earlier:

lick here to view code image

```
In [3]: with open('accounts.csv', 'r', newline='') as accounts:
    ...:     print(f'{"Account":<10}{"Name":<10}{"Balance":>10}')
    ...:     reader = csv.reader(accounts)
    ...:     for record in reader:
    ...:         account, name, balance = record
    ...:         print(f'{account:<10}{name:<10}{balance:>10}')
    ...: 
Account   Name      Balance
100       Jones       24.98
200       Doe        345.67
300       White         0.0
400       Stone      -42.16
500       Rich       224.62
```

The csv module's reader function returns an object that reads CSV-format data from the specified file object. Just as you can iterate through a file object, you can iterate through the reader object one record of comma-delimited values at a time. The preceding for statement returns each record as a list of values, which we unpack into the variables account, name and balance, then display.

# Caution: Commas in CSV Data Fields

Be careful when working with strings containing embedded commas, such as the name 'Jones, Sue'. If you accidentally enter this as the two strings 'Jones' and 'Sue', then writerow would, of course, create a CSV record with four fields, not three. Programs that read CSV files typically expect every record to have the same number of fields; otherwise, problems occur. For example, consider the following two lists:

```
[100, 'Jones', 'Sue', 24.98]
[200, 'Doe' , 345.67]
```

The first list contains four values and the second contains only three. If these two records were written into the CSV file, then read into a program using the previous snippet, the following statement would fail when we attempt to unpack the four-field record into only three variables:
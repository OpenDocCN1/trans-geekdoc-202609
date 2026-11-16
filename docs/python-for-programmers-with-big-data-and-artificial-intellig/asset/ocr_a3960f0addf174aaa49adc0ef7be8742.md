can vary in size. For example, 7, 14, −117, 2074 and 27383 are all integers and are stored in the same number of “raw data” bytes internally (typically 4 or 8 bytes in today’s systems). However, when these integers are output as formatted text, they become different-sized fields. For example, 7 is one character, 14 is two characters and 27383 is five characters.

To make the preceding name change, we can:

+   - copy the records before 300 White 0.00 into a temporary file,
+   - write the updated and correctly formatted record for account 300 to this file,
+   - copy the records after 300 White 0.00 to the temporary file,
+   - delete the old file and
+   - rename the temporary file to use the original file’s name.

This can be cumbersome because it requires processing *every* record in the file, even if you need to update only one record. Updating a file as described above is more efficient when an application needs to update many records in one pass of the file. 3

3 n the chapter, Big Data: Hadoop, Spark, NoSQL and IoT, youll see that database systems solve this update in place problem efficiently.

# Updating accounts.txt

Let’s use a with statement to update the accounts.txt file to change account 300’s name from 'White' to 'Williams' as described above:

lick here to view code image

```
n [1]: accounts = open('accounts.txt', 'r')

In [2]: temp_file = open('temp_file.txt', 'w')

In [3]: with accounts,   temp_file:
    ....:     for record in accounts:
    ....:         account, name, balance = record.split()
    ....:         if account != '300':
    ....:             temp_file.write(record)
    ....:         else:
    ....:             new_record = ' '.join([account, 'Williams', balance]
    ....:             temp_file.write(new_record + '\n')
```
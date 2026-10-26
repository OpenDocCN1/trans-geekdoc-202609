# Code Listing 55: Using getListOf().

The example in Code Listing 55 illustrates the usage of getListOf(). As can be seen from the output in Output 29, not only are the types of lists database dependant, but the information available is strictly dependent on user access privileges. There are many more databases on the MySQL server used for this book, but only one is listed because it is the only one available to the specified user. Also, the user name used in the examples here does not have privileges to look into the MySQL user database to list the other users.

```
Tables:
1. Departments
2. Employees
3. Paychecks
4. UploadedFiles
5. seq_employees
6. seq_sequence_1
7. seq_sequence_2
8. sequence_1_seq
9. sequence_2_seq
Users:
Databases:
1. book_test
```

# Output 29: Output of the getListOf() example (Code Listing 55).

Returns a DB_result or DB_Error object.

# DB_common::getSequenceName

```
string getSequenceName( string $sqn )
```

This is a private method used by the sequence functions (see page 22). This method returns a fully-
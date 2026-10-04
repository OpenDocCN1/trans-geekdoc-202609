
# Table E-20 MYSQL FUNCTIONS (Continued)

| Function | Returns | Action |
|---|---|---|
| mysql_errno([int link_identifier]) | int | Returns the number of the error message from previous MySQL operation |
| mysql_affected_rows([int link_]) | int | Gets number of affected rows in previous MySQL operation |
| mysql_insert_id(int link_identifier]) | int | Gets the number generated from the previous INSERT operation, where there is an auto_increment column |
| mysql_result(int result, int row [, mixed field]) | int | Gets result data |
| mysql_rows(int result) | int | Gets number of rows in a result |
| mysql_num_fields(int result) | int | Gets number of fields in a result |
| mysql_fetch_row(int result) | array | Gets a row as an enumerated array |
| mysql_fetch_object(int result [, int result_type]) | object | Fetches a result row as an object |
| mysql_fetch_array(int result [, int result_type]) | array | Fetches a result row as an associative array, a numeric array, or both. |
| mysql_data_seek(int result, int row_number) | int | Moves internal pointer. Creates an error if given an invalid row |
| mysql_fetch_lengths(int result) | array | Gets size of each column in a result |
| mysql_fetch_field(int result [, int field_offset]) | object | Gets column information from a result and returns an object |
| mysql_field_seek(int result, int field_offset) | int | Sets result pointer to a specific field offset. The next call to mysql_fetch_field() will use this offset |
| mysql_field_name(int result, int field_index) | string | Gets the name of the specified field in a result |
| mysql_field_table(int result, int field_offset) | string | Gets name of the table the specified field is in

# Appendix E: PHP Function Reference

| Function | Returns | Action |
| --- | --- | --- |
| mysql_field_len(int result, int field_offset) | int | Returns the length of the specified field |
| mysql_field_type(int result, int field_offset) | string | Gets the type of the specified field in a result |
| mysql_field_flags(int result, int field_offset) | string | Gets the flags associated with the specified field in a result |
| mysql_free_result(int result) | int | Frees result memory |

# Table E–21 ASPELL FUNCTIONS

| Function | Returns | Action |
| --- | --- | --- |
| aspell_new(string master [, string personal]) | int | Loads a dictionary |
| aspell_suggest(aspell int, string word) | array | Returns array of suggestions |
| aspell_check(aspell int, string word) | bool | Returns TRUE if a word is valid, FALSE if it is not |
| aspell_check_raw(aspell int, string word) | int | Returns TRUE if word is valid |

> To use the aspell functions, you need the aspell library from http://metalab.unc.edu/kevina/aspell/. That PHP is configured with with-aspell

![](img/245156cc770929860a3ede93c01f9981_497_0.png)

# Part V: Appendixes

## TABLE E-22 BCMATH FUNCTIONS
| Function | Returns | Action |
| --- | --- | --- |
| bcsub(string left_operand, string right_operand [, int scale]) | string | Returns the difference between two arbitrary-precision numbers |
| bcmul(string left_operand, string right_operand [, int scale]) | string | Returns the multiplication of two arbitrary-precision numbers |
| bcdiv(string left_operand, string right_operand [, int scale]) | string | Returns the quotient of two arbitrary-precision numbers (division) |
| bcmod(string left_operand, string right_operand) | string | Returns the modulus of the two arbitrary-precision operands |
| bcpow(string x, string y [, int scale]) | string | Returns the value of an arbitrary-precision number raised to the power of another |
| bcqsrt(string operand [, int scale]) | string | Returns the square root of an arbitrary-precision number |
| bbcc(string left_operand, string right_operand [, int scale]) | string | Compares two arbitrary-precision numbers |
| bcscale(int scale) | string | Sets default scale parameter for all bc math functions |

> Note Use of the bcmath functions requires PHP to be complied with --enable-bc-math.

## TABLE E-23 CALENDAR FUNCTIONS
| Function | Returns | Action |
| --- | --- | --- |
| jdtounix(int jday) | int | Converts Julian Day to Unix timestamp |

# Appendix E: PHP Function Reference

| Function | Returns | Action |
| --- | --- | --- |
| jdtogregoriancount(int juliandaycount) | string | Converts a Julian Day count to a Gregorian calendar date |
| gregorianjd(int month, int day, int year) | int | Converts a Gregorian calendar date to Julian Day count |
| jdtojulian(int juliandaycount) | string | Converts a Julian Day count to a Julian calendar date |
| juliantojd(int day, int year) | int | Converts a Julian calendar date to jul day count |
| jdtojeweish(int juliandaycount) | string | Converts a Julian Day count to a French Republic calendar date |
| jwishtojd(int month, int day, int year) | int | Converts a Jewish calendar date to Julian Day count |
| jdtofrench(int juliandaycount) | string | Converts a Julian Day count to a French Republic calendar date |
| frenchtoj(int calendar, int day, int year) | int | date to Julian Day count |
| jddayofweek(int juliandaycount [. int mode]) | mixed | Returns name or number of day of week from Julian Day count |
| jdmonthname(int juliandaycount, int mode) | string | Returns name of month for Julian Day count |

Use of the calendar functions requires PHP to complied with --enable-calendar.

![](img/245156cc770929860a3ede93c01f9981_499_0.png)

# TABLE E-24 COM FUNCTIONS

| Function | Returns | Action |
| --- | --- | --- |
| com_load(int result) | int | Loads a object |
| com_invoke(int result, int result_type]) | object | Fetches a result row as an object |
| com_get(int result [, int result_type]) | array | Fetches a result row as an associative array, a numeric array, or both. |
| com_seek(int result, int row_number) | int | Moves internal pointer. Creates an error if given an invalid row |
| com_lengths(int result) | array | Gets size of each column in a result |
| com_field(int result [, int field_offset]) | object | Gets column information from a result and returns an object |
| com_field_seek(int result, int field_offset) | int | Sets result pointer to a specific field offset. The next call to mysql_fetch_field() will use this offset |
| com_free(int result) | int | Frees result memory |

# TABLE E-25 CYBER FUNCTIONS

| Function | Returns | Action |
| --- | --- | --- |
| com_field_len(int result, int field_offset) | int | Returns the length of the specified field |
| com_field_type(int result, int field_offset) | string | Gets the type of the specified field in a result |
| com_field_flags(int result, int field_offset) | string | Gets the flags associated with the specified field in a result |
| com_free_result(int result) | int | Frees result memory |

# TABLE E-26 DBASE FUNCTIONS

| Function | Returns | Action |
| --- | --- | --- |
| db_open(string filename, string mode) | int | Opens a database |
| db_close(int handle) | void | Closes database |
| db_exists(string key, int handle) | bool | Determines whether the specified key exists |
| db_fetch(string key, int handle) | string | Fetches the data associated with key |
| db_firstkey(int handle) | string | Resets the internal key pointer and returns the first key |
| db_nextkey(int handle) | string | Returns the next key |
| db_delete(string key, int handle) | bool | Deletes the entry associated with the key |
| db_insert(string key, string value, int handle) | bool | Inserts value as key, returns false if key already exists |
| db_replace(string key, string value, int handle) | bool | Inserts value as key, replaces key if key already exists |
| db_optimize(int handle) | bool | Optimizes (e.g. cleans up vacuums) database |
| db_sync(int handle) | bool | Synchronizes database |

# TABLE E-27 DBA FUNCTIONS

| Function | Returns | Action |
| --- | --- | --- |
| dba_popen(string path, string mode, string handlername [, string ...]) | int | Opens path using the specified handler persistently |
| dba_open(string path, string mode, string handlername [, string ...]) | int | Opens path using the specified handler in mode |
| dba_close(int handle) | void | Closes database |
| dba_exists(string key, int handle) | bool | Determines whether the specified key exists |
| dba_fetch(string key, int handle) | string | Fetches the data associated with key |
| dba_firstkey(int handle) | string | Resets the internal key pointer and returns the first key |
| dba_nextkey(int handle) | string | Returns the next key |
| dba_delete(string key, int handle) | bool | Deletes the entry associated with the key |
| dba_insert(string key, string value, int handle) | bool | Inserts value as key, returns false if key already exists |
| dba_replace(string key, string value, int handle) | bool | Inserts value as key, replaces key if key already exists |
| dba_optimize(int handle) | bool | Optimizes (e.g. cleans up vacuums) database |
| dba_sync(int handle) | bool | Synchronizes database |

# Appendix E: PHP Function Reference

PHP must be compiled--with-dbase in order to use these functions.

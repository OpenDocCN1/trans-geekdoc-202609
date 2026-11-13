This column type defines a superset of values. It allows for zero or more values from the list you specify to be included in a field. You will not see this column type used in this book: We do not like to see multiple values in a single field, as it violates very basic rules of database design. (Reread Chapter 1 if you don’t know what we mean by this.) You can see an example of where set makes sense in the MySQL grant tables, which are discussed in Appendix E.

![](bbox=[0.085, 0.235, 0.175, 0.305])

Bear in mind that set columns can yield big savings in storage space and improvements in performance as databases get bigger. Suppose you have 20,000,000,000 rows and you need to store the state of eight binary switches for each row. To normalize this out would require a bigint and a tinyint for each switch. Even without indexes you are looking at about 185GB for the table. Using a set column, you would require only 37.25GB for this problem. However, this isn’t something you’ll see in this book.

# Numeric column types

MySQL provides you with seven column types suitable for storing numeric values. Note that the following are synonyms: int and integer; double, double precision, and real; and decimal and numeric.

+   - int/integer
+   - tinyint
+   - mediumint
+   - bigint
+   - float
+   - double/double precision/real
+   - decimal/numeric

Be aware that real is synonymous with float when running in ANSI mode.

![](bbox=[0.085, 0.805, 0.175, 0.875])

For all numeric types the maximum display size is 255. For most numeric types you will have the option to zerofill a column — to left-pad it with zeros. For example, if you have an int column that has a display size of 10 and you insert a value of 25 into this column, MySQL will store and display 0000000025. The numeric column types may also be defined as signed or unsigned.signed is the default definition.
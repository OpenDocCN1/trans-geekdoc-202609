
## MySQL Data Types

When you create a database table — which you do later in the chapter — the type and size of each field must be defined. A field is similar to a PHP variable except that you can store only the specified type and size of data in a given field. For example, you can’t insert characters into an integer field. MySQL supports three main groups of data types — numeric, date/time, and string — which are outlined in the following sections.

> The descriptions here are fine for everyday use, but they’re not complete. For full details see the MySQL manual at http://dev.mysql.com/doc/.

> This book assumes that you’re using MySQL version 5 (the current version at the time of writing).

## Numeric Data Types

You can store numbers in MySQL in many ways, as shown by the following table. Generally speaking, you should pick the data type most suited for the type of numbers you need to store.

| Numeric Data Type | Description | Allowed Range of Values |
|---|---|---|
| TINYINT | Very small integer | −128 to 127, or 0 to 255 if UNSIGNED |
| SMALLINT | Small integer | −32768 to 32767, or 0 to 65535 if UNSIGNED |
| MEDIUMINT | Medium-sized integer | −8388608 to 8388607, or 0 to 16777215 if UNSIGNED |
| INT | Normal-sized integer | −2147483648 to 2147483647, or 0 to 4294967295 if UNSIGNED |
| BIGINT | Large integer | −9223372036854775808 to 9223372036854775807, or 0 to 18446744073709551615 if UNSIGNED |
| FLOAT | Single-precision floating-point number | Smallest non-zero value: ±1.176 × 10⁻³⁸, largest value: ±3.403 × 10³⁸ |
| DOUBLE | Double-precision floating-point number | Smallest non-zero value: ±2.225 × 10⁻³⁰⁸, largest value: ±1.798 × 10³⁰⁸ |
| DECIMAL(precision, scale) | Fixed-point number | Same as DOUBLE, but fixed-point rather than floating-point. precision specifies the total number of allowed digits, whereas scale specifies how many digits sit to the right of the decimal point. |
| BIT | 0 or 1 | 0 or 1 |

Why not just always use the data types that can hold the biggest range of numbers, such as `BIGINT` and `DOUBLE`? Well, the bigger the data type, the more storage space it takes up in the database. For example, an `INT` field takes up four bytes, whereas a `SMALLINT` field only requires two bytes of storage. If you end up storing millions of records, those extra two bytes can really make a difference! So use the smallest data type that will comfortably hold the range of values you expect to use.

You can add the attribute `UNSIGNED` after a numeric data type when defining a field. An unsigned data type can only hold positive numbers. In the case of the integer types, an unsigned type can hold a maximum value that’s around twice the size of its equivalent signed type. For example, a `TINYINT` can hold a maximum value of 127, whereas an unsigned `TINYINT` can hold a maximum value of 255. However, for the unsigned `FLOAT`, `DOUBLE`, and `DECIMAL` types, the maximum values are the same as for their signed equivalents.

## Date and Time Data Types

As with numbers, you can choose from a range of different data types to store dates and times, depending on whether you want to store a date only, a time only, or both:

| Date/Time Data Type | Description | Allowed Range of Values |
| :--- | :--- | :--- |
| DATE | Date | 1 Jan 1000 to 31 Dec 9999 |
| DATETIME | Date and time | Midnight, 1 Jan 1000 to 23:59:59, 31 Dec 9999 |
| TIMESTAMP | Timestamp | 00:00:01, 1 Jan 1970 to 03:14:07, 9 Jan 2038, UTC (Universal Coordinated Time) |
| TIME | Time | -838:59:59 to 838:59:59 |
| YEAR | Year | 1901 to 2155 |

When you need to specify a literal `DATE`, `DATETIME`, or `TIMESTAMP` value in MySQL, you can use any of the following formats:

- YYYY-MM-DD / YY-MM-DD
- YYYY-MM-DD HH:MM:SS / YY-MM-DD HH:MM:SS
- YYYYMMDD / YYMMDD
- YYYYMMDDHHMMSS / YYMMDDHHMMSS

## String Data Types

MySQL lets you store text or binary strings of data in many different ways, as shown in the following table:

| String Data Type | Description | Allowed Lengths |
|---|---|---|
| CHAR(n) | Fixed-length string of n characters | 0–255 characters |
| VARCHAR(n) | Variable-length string of up to n characters | 0–65535 characters |
| BINARY(n) | Fixed-length binary string of n bytes | 0–255 bytes |
| VARBINARY(n) | Variable-length binary string of up to n bytes | 0–65535 bytes |
| TINYTEXT | Small text field | 0–255 characters |
| TEXT | Normal-sized text field | 0–65535 characters |
| MEDIUMTEXT | Medium-sized text field | 0–16777215 characters |
| LONGTEXT | Large text field | 0–4294967295 characters |
| TINYBLOB | Small BLOB (Binary Large Object) | 0–255 bytes |
| BLOB | Normal-sized BLOB | 0–65535 bytes |
| MEDIUMBLOB | Medium-sized BLOB | 0–16777215 bytes (16MB) |
| LONGBLOB | Large BLOB | 0–4294967295 bytes (4GB) |
| ENUM | Enumeration | The field can contain one value from a predefined list of up to 65,535 values |
| SET | A set of values | The field can contain zero or more values from a predefined list of up to 64 values |

The difference between a CHAR and a VARCHAR field is that CHAR stores data as a fixed-length string no matter how short the actual data may be, whereas VARCHAR uses exactly as many characters as necessary to store a given value. Suppose you insert the string "dodge" into the following fields:

- char_field defined as CHAR(10)
- varchar_field defined as VARCHAR(10)

They will store the same string slightly differently, as follows:

```
char_field: "dodge "   // Right-padded with five spaces
varchar_field: "dodge"   // No padding
```

So generally speaking, `VARCHAR` character fields save you disk space. Don't be tempted to use `VARCHAR` fields for storing every string, though, because that has drawbacks, too. The MySQL server processes `CHAR` type fields much faster than `VARCHAR` type, for one thing, because their length is predetermined. If your strings don't vary in length much, or at all, you're better off using `CHAR` type fields. In fact, when your strings are all the same length, `VARCHAR` takes up more disk space, because it has to store the length of each string in one or two additional bytes.

With the character types — `CHAR`, `VARCHAR`, `TEXT`, and so on — the amount you can store may be less than the maximum shown, depending on the character set used. For example, the UTF-8 (Unicode) character set commonly uses up to 3 bytes per character, so a `VARCHAR` field may only be able to store up to 21,844 UTF-8 characters.

## Using Indexes and Keys

Inexperienced database designers sometimes complain about their database engines being slow — a problem that's often explained by the lack of an _index_. An index is a separate sorted list of the values in a particular column (or columns) in a table. Indexes are also often called _keys_; the two words are largely interchangeable. You can optionally add indexes for one or more columns at the time you create the table, or at any time after the table is created.

To explain why indexing a table has a dramatic effect on database performance, first consider a table without indexes. Such a table is similar to a plain text file in that the database engine must search it sequentially. Rows in a relational database are not inserted in any particular order; the server inserts them in an arbitrary manner. To make sure it finds all entries matching the information you want, the engine must scan the whole table, which is slow and inefficient, particularly if there are only a few matches.

Now consider an indexed table. Instead of moving straight to the table, the engine can scan the index for items that match your requirements. Because the index is a sorted list, this scan can be performed very quickly. The index guides the engine to the relevant matches in the database table, and a full table scan is not necessary.

So why not just sort the table itself? This might be practical if you knew that there was only one field on which you might want to search. However, this is rarely the case. Because it's not possible to sort a table by several fields at once, the best option is to use one or more indexes, which are separate from the table.

A _primary key_ is a special index that, as you saw earlier, is used to ID records and to relate tables to one another, providing the relational database model. Each related table should have one (and only one) primary key.

You can also create an index or primary key based on combinations of fields, rather than just a single field. For a key to be formed in this way, the combination of values across the indexed fields must be unique.

Because an index brings about a significant boost in performance, you could create as many indexes as possible for maximum performance gain, right? Not always. An index is a sure-fire way to increase the speed of searching and retrieving data from a table, but it makes updating records slower, and also increases the size of the table. This is because, when you insert a record into an indexed table, the database engine also has to record its position in the corresponding index or indexes. The more indexes, the slower the updating process and the larger the table.

# Chapter 12: Introducing Databases and SQL

Why not just use the data types that can hold the biggest range of numbers, such as BIGINT and DOUBLE? Well, the bigger the data type, the more storage space it takes up in the database. For example, an INT field takes four bytes, whereas a SMALLINT field requires only two bytes of storage. If you end up storing millions of records, those extra two bytes can really make a difference! Use the smallest data type that could hold the range of values you expect to use.

You can add the UNSIGNED attribute to a numeric data type when defining a field. An unsigned data type can only hold positive numbers. In the case of the integer types, an unsigned data type can hold a maximum value that around twice the size of its equivalent signed type. For example, a TINYINT can hold a maximum value of 127, whereas an unsigned TINYINT can hold a maximum of 255. However, for the unsigned FLOAT, DOUBLE, and DECIMAL types, the maximum values are the same as for their equivalents.

# Date and Time Types

With numbers, you can choose from a range of different data types to store dates and times, depending on whether you want to store a date only, a time only, or both:

| Date/Time Data Type | Description | Allowed Range of Values |
| --- | --- | --- |
| DATE | Date | 1 Jan 1000 to 31 Dec 9999 |
| DATETIME | Date and time | Midnight, 1 Jan 1000 to 23:59:59, 31 Dec 9999 |
| TIMESTAMP | Timestamp | 00:00:01, 1 Jan 1970 to 03:14:07, 9 Jan 2038, UTC (Universal Coordinated Time) |
| TIME | Time | -838:59:59 to 838:59:59 |
| YEAR | Year | 1901 to 2155 |

When you need to specify a literal DATE, DATETIME, or TIMESTAMP value in MySQL, you can use any of the following formats:

+   - YYYY-MM-DD / YY-MM-DD
- YYYY-MM-DD HH:MM:SS / YYYY-MM-DD HH:MM:SS
- YYYYMMDD / YYYYMMDD
- YYYYMMDDHMMSS / YYYYMMDDHMMSS

345
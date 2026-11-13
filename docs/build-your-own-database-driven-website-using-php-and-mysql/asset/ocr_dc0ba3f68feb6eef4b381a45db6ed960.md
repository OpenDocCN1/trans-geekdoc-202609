# # Date/Time Types

DATE

Description: A date.
Range: '1000-01-01' to '9999-12-31', and '0000-00-00'
Storage space: 3 bytes (24 bits)

TIME

Description: A time.
Range: '-838:59:59' to '838:59:59'
Storage space: 3 bytes (24 bits)

DATETIME

Description: A date and time.
Range: '1000-01-01 00:00:00' to '9999-12-31 23:59:59'
Storage space: 8 bytes (64 bits)

YEAR[(2|4)]

Description: A year in 2- or 4-digit (the default) format.
Range: 1901 to 2155, and 0000 in 4-digit format
70 to 69 (1970 to 2069) in 2-digit format
Storage space: 1 byte (8 bits)

TIMESTAMP[(M)]

Description: A timestamp (date/time), in YYYYMMDDHHMMSS format.
Range: 19700101000000 to sometime in 2037 on current systems.
Storage space: 4 bytes (32 bits)

Notes: An INSERT or UPDATE operation on a row that contains one or more TIMESTAMP columns will automatically update the first TIMESTAMP column in the row with the current date/time. This lets you use such a column as the 'last modified date/time' for the row. Assigning a value of NULL to the column will have the same effect, thereby providing a means of 'touching' the date/time. You can also assign actual values as you would for any other column.

Allowable values for M are 14, 12, 10, 8, 6, 4, and 2, and correspond to the display formats YYYYMMDDHHMMSS, YYYYMMDDHHMMSS, YYYYMMDDHHMM, YYYYMMDD, YYMMDD, YYMM, and YY respectively. Odd values from 1 to 13 will automatically be bumped up to the next
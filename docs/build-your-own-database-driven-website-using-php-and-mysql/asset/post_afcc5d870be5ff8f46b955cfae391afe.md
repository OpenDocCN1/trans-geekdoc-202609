
BINARY: By default, comparisons of character values in MySQL (including sorting) are case-insensitive. However, comparisons for BINARY columns are case-sensitive.

For a complete, up-to-date reference to supported SQL functions, see the MySQL Reference Manual at http://www.mysql.com.

## Numerical Types

### TINYINT[(M)]

- **Description**: A tiny integer value.
- **Attributes allowed**: UNSIGNED, ZEROFILL
- **Range**: -128 to 127 (0 to 255 if UNSIGNED)
- **Storage space**: 1 byte (8 bits)

### SMALLINT[(M)]

- **Description**: A small integer value.
- **Attributes allowed**: UNSIGNED, ZEROFILL
- **Range**: -32768 to 32767 (0 to 65535 if UNSIGNED)
- **Storage space**: 2 bytes (16 bits)

### MEDIUMINT[(M)]

- **Description**: A medium integer value.
- **Attributes allowed**: UNSIGNED, ZEROFILL
- **Range**: -8388608 to 8388607 (0 to 16777215 if UNSIGNED)
- **Storage space**: 3 bytes (24 bits)

### INT[(M)]

- **Description**: A regular integer value.
- **Attributes allowed**: UNSIGNED, ZEROFILL
- **Range**: -2147483648 to 2147483647 (0 to 4294967295 if UNSIGNED)
- **Storage space**: 4 bytes (32 bits)
- **Alternative syntax**: INTEGER[(M)]

### BIGINT[(M)]

- **Description**: A large integer value.
- **Attributes allowed**: UNSIGNED, ZEROFILL
- **Range**: -9223372036854775808 to 9223372036854775807 (0 to 18446744073709551615 if UNSIGNED)
- **Storage space**: 8 bytes (64 bits)
- **Notes**: MySQL performs all integer arithmetic functions in signed BIGINT format; thus, BIGINT UNSIGNED values over 9223372036854775807 (63 bits) will only work properly with bit functions (e.g. bitwise AND, OR, and NOT). Attempting integer arithmetic with larger values may produce inaccurate results due to rounding errors.

### FLOAT[(M,D)] FLOAT(precision)

- **Description**: A floating point number.
- **Attributes allowed**: ZEROFILL
- **Range**: 0 and ±1.175494351E-38 to ±3.402823466E+38
- **Storage space**: 4 bytes (32 bits)
- **Notes**: precision (in bits), if specified, must be less than or equal to 24, or else a DOUBLE column will be created instead (see below).

### DOUBLE[(M,D)] FLOAT(precision)

- **Description**: A high-precision floating point number.
- **Attributes allowed**: ZEROFILL
- **Range**: 0 and ±2.2250738585072014E-308 to ±1.7976931348623157E+308
- **Storage space**: 8 bytes (64 bits)
- **Notes**: precision (in bits), if specified, must be greater than or equal to 25, or else a FLOAT column will be created instead (see above). precision may not be greater than 53.
- **Alternative syntax**: DOUBLE PRECISION[(M, D)] or REAL [(M, D)]

### DECIMAL[(M[, D])]

- **Description**: A floating point number stored as a character string.
- **Attributes allowed**: ZEROFILL
- **Range**: As for DOUBLE, but constrained by M and D (see Notes)
- **Storage space**: M+2 bytes (8M+16 bits) (see Notes prior to MySQL 3.23)
- **Notes**: If D is not specified, it defaults to 0 and numbers in this column will have no decimal point or fractional part. If M is not specified, it defaults to 10. In versions of MySQL prior to 3.23, M had to include space for the negative sign and the decimal point, so the storage space required was M bytes (8M bits). The newer format in MySQL 3.23 or later is ANSI SQL compliant.
- **Alternative syntax**: NUMERIC([M[, D]])

## Character Types

### CHAR(M)

- **Description**: A fixed-length character string.
- **Attributes allowed**: BINARY
- **Maximum Length**: M characters
- **Storage space**: M bytes (8M bits)
- **Notes**: CHAR values are stored as strings of length M, even though the assigned value may be shorter. When the string does not occupy the full length of the field, spaces are added to the end of the string to bring it to exactly M characters. Trailing spaces are then stripped off when the value is retrieved.

CHAR columns are quicker to search than variable-length character column types such as VARCHAR, since their fixed-length nature makes the underlying database file format more regular.

M may take any integer value from 0 to 255, with a CHAR(0) column only able to store two values: NULL and "" (the empty string), and occupying only a single bit.

- **Alternative syntax**: CHARACTER (M)

### VARCHAR(M)

- **Description**: A variable-length character string.
- **Attributes allowed**: BINARY
- **Maximum Length**: M characters
- **Storage space**: Length of stored value, plus 1 byte to store length.
- **Notes**: As VARCHAR values occupy only the space they require, there is usually no point to specifying a maximum field length M of anything less than 255 (the maximum). Values anywhere from 1 to 255 are acceptable, however, and will cause strings longer than the specified limit to be chopped to the maximum length when inserted.

Trailing spaces are stripped from values before they are stored.

- **Alternative syntax**: CHARACTER VARYING(M)

### TINYBLOB, TINYTEXT

- **Description**: A short, variable-length character string.
- **Maximum Length**: 255 characters
- **Storage space**: Length of stored value, plus 1 byte to store length.
- **Notes**: Basically equivalent to **VARCHAR(255)** **BINARY** and **VARCHAR(255)**, respectively. However, these column types do not trim trailing spaces from inserted values.

The only difference between **TINYBLOB** and **TINYTEXT** is that the former performs case-sensitive comparisons and sorts while the latter does not.

### BLOB, TEXT

- **Description**: A variable-length character string.
- **Maximum Length**: 65535 characters (65KB)
- **Storage space**: Length of stored value, plus 2 bytes to store length.
- **Notes**: The only difference between **BLOB** and **TEXT** is that the former performs case-sensitive comparisons and sorts, while the latter does not.

### MEDIUMBLOB, MEDIUMTEXT

- **Description**: A medium, variable-length character string.
- **Maximum Length**: 16777215 characters (16.8MB)
- **Storage space**: Length of stored value, plus 3 bytes to store length.
- **Notes**: The only difference between **MEDIUMBLOB** and **MEDIUMTEXT** is that the former performs case-sensitive comparisons and sorts, while the latter does not.

### LONGBLOB, LONGTEXT

- **Description**: A long, variable-length character string.
- **Maximum Length**: 4294967295 characters (4.3GB)
- **Storage space**: Length of stored value, plus 4 bytes to store length.
- **Notes**: The only difference between **LONGBLOB** and **LONGTEXT** is that the former performs case-sensitive comparisons and sorts, while the latter does not.

```
ENUM('value1', 'value2', ...)
```

- **Description**: A set of values from which a single value must be chosen for each row.
- **Maximum Length**: One value chosen from up to 65535 possibilities.
- **Storage space**: 1 to 255 values: 1 byte (8 bits); 256 to 65535 values: 2 bytes (16 bits)

- **Notes**: Values in this type of field are stored as integers that represent the element selected. 1 represents the first element, 2 the second, and so on. The special value 0 represents the empty string "", which is stored if a value that does not appear in column declaration is assigned.

NOT NULL columns of this type default to the first value in the column declaration if no particular default is assigned.

```
SET('value1', 'value2', ...)
```

- **Description**: A set of values, each of which may be set or not set.
- **Maximum Length**: Up to 64 values in a given SET column.
- **Storage space**: 1 to 8 values: 1 byte (8 bits); 9 to 16 values: 2 bytes (16 bits); 17 to 24 values: 3 bytes (24 bits); 25 to 32 values: 4 bytes (32 bits); 33 to 64 values: 8 bytes (64 bits)

- **Notes**: Values in this type of field are stored as integers representing the pattern of bits for set and unset values. For example, if a set contains 8 values, and in a particular row the odd values are set, then the binary representation 01010101 becomes the decimal value 85. Values may therefore be assigned either as integers, or as a string of set values, separated by commas (e.g. "value1,value3,value5,value7" = 85). Searches should be performed either with the LIKE operator, or the FIND_IN_SET() function.

## Date/Time Types

### DATE

- **Description**: A date.
- **Range**: '1000-01-01' to '9999-12-31', and '0000-00-00'
- **Storage space**: 3 bytes (24 bits)

### TIME

- **Description**: A time.
- **Range**: '-838:59:59' to '838:59:59'
- **Storage space**: 3 bytes (24 bits)

### DATETIME

- **Description**: A date and time.
- **Range**: '1000-01-01 00:00:00' to '9999-12-31 23:59:59'
- **Storage space**: 8 bytes (64 bits)

### YEAR[(2|4)]

- **Description**: A year in 2- or 4-digit (the default) format.
- **Range**: 1901 to 2155, and 0000 in 4-digit format; 70 to 69 (1970 to 2069) in 2-digit format
- **Storage space**: 1 byte (8 bits)

### TIMESTAMP[(M)]

- **Description**: A timestamp (date/time), in YYYYMMDDHHMMSS format.
- **Range**: 19700101000000 to sometime in 2037 on current systems.
- **Storage space**: 4 bytes (32 bits)
- **Notes**: An INSERT or UPDATE operation on a row that contains one or more TIMESTAMP columns will automatically update the first TIMESTAMP column in the row with the current date/time. This lets you use such a column as the 'last modified date/time' for the row. Assigning a value of NULL to the column will have the same effect, thereby providing a means of 'touching' the date/time. You can also assign actual values as you would for any other column.

Allowable values for M are 14, 12, 10, 8, 6, 4, and 2, and correspond to the display formats YYYYMMDDHHMMSS, YYYYMMDDHHMMSS, YYYYMMDDHHMM, YYYYMMDD, YYMMDD, YYMM, and YY respectively. Odd values from 1 to 13 will automatically be bumped up to the next

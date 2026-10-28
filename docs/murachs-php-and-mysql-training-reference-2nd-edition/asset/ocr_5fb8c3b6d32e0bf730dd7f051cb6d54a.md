# Common numeric data types

| Type | Description |
|---|---|
| `INT[(size)]` | An integer between -2,147,483,648 and 2,147,483,647 where size is the maximum display size. Default size is 11. |
| `TINYINT[(size)]` | An integer between -127 and 128 where size is the maximum display size. Default size is 4. |
| `DECIMAL[(p,s)]` | Decimal numbers with fixed precision (p) and scale (s). The maximum precision is 65 and the default is 10. The maximum scale is 30 and the default is 0. |

# Common string data types

| Type | Description |
|---|---|
| `VARCHAR(size)` | Variable-length characters where size is the maximum number of characters. The size argument is required. The maximum size is 65,535. |
| `CHAR[(size)]` | Fixed-length characters where size is the number of characters. The default size is 1. The maximum size is 255. |
| `TEXT` | Variable-length characters up to a maximum size of 65,535 bytes. |

# Common date and time data types

| Type | Description |
|---|---|
| `DATE` | Dates from January 1, 1000 through December 31, 9999. The default format for entry and display is “yyyy-mm-dd”. |
| `TIME` | Times in the range -838:59:59 through 838:59:59. The default format for display and entry is “hh:mi:ss”. |
| `DATETIME` | Date and time from January 1, 1970 through December 31, 9999. The default format for display and entry is “yyyy-mm-dd hh:mi:ss”. |

# Description

+   - By default, MySQL uses the *Latin-1 character set*, which provides for 256 characters with 1 byte per character.
+   - The *Unicode character set* provides for over 65,000 characters, usually with 2 bytes per character.
+   - The CHAR data type is typically used for *fixed-length strings*. This data type uses the same amount of storage regardless of the actual length of the string. If you insert a value that’s shorter than the specified type, the end of the value will be padded with spaces.
+   - The VARCHAR data type is typically used for *variable-length strings*. This data type uses only the amount of storage needed for a given string.
+   - The *precision* of a DECIMAL type indicates the total number of digits that can be stored in the data type. The *scale* indicates the number of decimal digits that can be stored to the right of the decimal point. The decimal point and minus sign for the number aren’t counted in the precision.

Figure 17-2   An introduction to MySQL data types
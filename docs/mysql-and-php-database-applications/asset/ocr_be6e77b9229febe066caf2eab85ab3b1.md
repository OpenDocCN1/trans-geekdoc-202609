# Chapter 2: The Structured Query Language for Creating and Altering Tables

| Size | Format |
|---|---|
| 2 | YY |
| 4 | YYMM |
| 6 | YYMMDD |
| 8 | YYYYMMDD |
| 10 | YYYMMDDHMM |
| 12 | YYYMMDDHMMSS |
| 14 | YYYYMMDDHMMSS |

# ### TIME

Usage: *time*
Stores time in HH:MM:SS format and has a value range from –838:59:59 to 838:59:59. The reason for the large values is that the time column type can be used to store the result of mathematical equations involving times.

# ### YEAR

Usage: `year[(2|4)]`
 this post-Y2K days it's hard to imagine that you'd want to store your years in two-digit format, but you can. In two-digit format, allowable dates are between 1970 and 2069. The digits 70-99 are prepended with 19 and 01–69 are prepended with 20.

Four-digit year format allows values from 1901 to 2155.

# # Creating Indexes

Starting in version 3.23.6 MySQL can create an index on any column. There can be a maximum of 16 columns for any table. The basic syntax is:

```
index index_name (indexed_column)
```
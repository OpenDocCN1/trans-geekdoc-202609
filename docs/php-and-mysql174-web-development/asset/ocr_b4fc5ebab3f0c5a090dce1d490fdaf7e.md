# Chapter 12 Advanced MySQL Administration

Obviously, the smaller you can make this number, the better. At present, you have a negligible amount of data in the database, but when the database starts to increase in size, this query would increase in execution time. We return to this matter shortly.

The possible_keys column lists, as you might expect, the keys that MySQL might use to join the table.

The key column is either the key from the table MySQL actually used or NULL if no key was used.

The key_len column indicates the length of the key used. You can use this number to tell whether only part of a key is used. The key is relevant when you have keys that consist of more than one column.

The ref column shows the columns used with the key to select rows from the table.

Finally, the Extra column tells you any other information about the way the join was performed. Some possible values you might see in this column are shown in Table 12.10. For a complete list http://dev.mysql.com/doc/refman/5.6/en/explain-output.html#explain-extra-information.

# Table 12.10 Some Possible Values for Extra Column as Shown in Output from EXPLAIN

| Value | Meaning |
|---||
| Distinct | After the first match is found, MySQL stops trying to find rows. |
| Not exists | The query has been optimized to use LEFT JOIN. |
| Range checked for each record | For each row in the set of rows from the other tables in the join, MySQL tries to find the best index to use, if any. |
| Using filesort | Two passes are required to sort the data. (This operation obviously takes twice as long.) |
| Using index | All information from the table comes from the index; that is, the rows are not actually looked up. |
| Using join buffer | Tables are read in partitions, using the join buffer; the rows are extracted from the buffer to complete the query. |
| Using temporary | A temporary table needs to be created to execute this query. |
| Using where | A WHERE clause is being used to select rows. |

You can fix problems you spot in the output from EXPLAIN in several ways. First, you can check column types and make sure they are the same. This applies particularly to column widths. Indexes can't be used to match columns if they have different widths. You can fix this problem by changing the types of columns to match or by building this in your design from the start.
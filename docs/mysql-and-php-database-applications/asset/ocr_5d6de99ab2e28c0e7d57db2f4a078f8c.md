# Appendix C: MySQL Utilities

| Flag | Alternate Flag | Description |
| --- | --- | --- |
| -r | --raw | Write column values without escape conversion. Used with '--batch' |
| --safe-mode (new to 3.23) | | Sends the following command to the MySQL server when opening the connection: SET SQL_SAFE_UPDATES=1,SQL_SELECT_LIMIT=#select_limit#,SQL_MAX_JOIN_SIZE=#max_join_size# where '#select_limit#' and '#max_join_size#' are variables that you can set from the mysql command line. |

Effect of the previous command is:

+   - You are not allowed to UPDATE or DELETE if you don't have a key constraint in the WHERE part. One can however force an UPDATE/DELETE by using LIMIT: UPDATE table_name=Set not_key_column=some value WHERE not_key_column=some value LIMIT 1;
- All results are automatically limited to #select_limit# rows.
- SELECTs that will probably need to examine more than #max_join_size row combinations will be aborted.

Table C-4 lists additional mysql command-line client options.

# Table C-4 COMMON MYSQL COMMAND-LINE CLIENT OPTIONS, PART IV

| Flag | Alternate Flag | Description |
| --- | --- | --- |
| -t | --table | Output in table format. This is default in non-batch mode. |
 -u | --user=# | User for login if not current user. |
 -w | --wait | Wait and retry if connection is down instead of aborting. |
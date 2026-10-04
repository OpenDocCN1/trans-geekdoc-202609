# 434 Part V: Appendixes

# **TABLE C-9 MORE MYSQLDUMP COMMAND-LINE OPTIONS (Continued)**

| Flag | Alternate Flag | Description |
| --- | --- | --- |
| -u user_name, | --user=user_name | The MySQL user name to use when connecting to the server. |
| -w | --where='where-condition' | Dump only selected records; Note that QUOTES are mandatory! <br><br>Example:<br>--where='user=*jimf*' <br>--wuserid>1* <br>--wuserid<1* |

Table C-10 displays the mysqldump command line options that are new to version 3.23.

# **TABLE C-10 MYSQLDUMP COMMAND-LINE OPTIONS NEW IN VERSION 3.23**

| Flag | Alternate Flag | Description |
| --- | --- | --- |
| -A | --all-databases | Dump all the databases. This is the same as --databases with all databases selected. |
| -B | --databases | Dump several databases. Note the difference in usage; in this case no tables are given. All name arguments are regarded as database names. Use db_name; will be included in the output before each new database. |
| -e | --extended-insert | Use the new multiline INSERT syntax.|
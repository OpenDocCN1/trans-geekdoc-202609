| Table 5-1 | MySQL Account Permissions |
|---|---|
| Permission | Description |
| ALL | All permissions |
| ALTER | Can alter the structure of tables |
| CREATE | Can create new databases or tables |
| DELETE | Can delete rows in tables |
| DROP | Can drop databases or tables |
| FILE | Can read and write files on the server |
| GRANT | Can change the permissions on a MySQL account |
| INSERT | Can insert new rows into tables |
| SELECT | Can read data from tables |
| SHUTDOWN | Can shut down the MySQL server |
| UPDATE | Can change data in a table |
| USAGE | No permissions at all |

![](bbox=[0.1, 0.5, 0.2, 0.6])

Granting ALL is not a good idea because it includes permissions for administrative operations, such as shutting down the MySQL server. You are unlikely to want anyone other than yourself to have such sweeping privileges.

# Setting Up MySQL Accounts

When creating a new account, you specify the password, the name(s) of the computer(s) allowed to access the database using this account, and the permissions; however, you can change these at any time. All the account information is stored in a database named mysql that is automatically created when MySQL is installed. To add a new account or change any account information, you must use an account that has the proper permissions on the mysql database.

You need at least one account in order to access the MySQL server. When MySQL is installed, it automatically sets up some accounts, including an account called root that has all permissions. If you have MySQL access through a company Web site or a Web hosting company, the MySQL administrator for the company should give you the account; the account is probably not named root, and it might or might not have all permissions.
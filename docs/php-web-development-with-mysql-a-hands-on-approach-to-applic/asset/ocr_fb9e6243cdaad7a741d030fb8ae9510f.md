# # 12. INSERTING DATA INTO A MYSQL DATABASE

Then in Bash:

```
```bash
sudo mysql
```
```

Next, we create the user for our FullName database.

```
```sql
GRANT ALL PRIVILEGES ON FullName.* TO 'testuser'@'localhost';
FLUSH PRIVILEGES;
exit
```
```

Your MySQL command line should look similar to Figure 12.17.

![](bbox=[0.407, 0.287, 0.918, 0.598])

Now let’s log back into the MySQL CLI tool as testuser:

```
```bash
mysql -u testuser -p
```
```

Next, let’s create our database, which we need to call FullName. We’ll do that with the following SQL command:

```
```sql
CREATE DATABASE FullName;
```
```

Next, we need to USE our FullName database to work with it.

```
```sql
USE FullName;
```
```

Now let’s create our fullName table using the following CREATE TABLE command for all the fields in our table using the following SQL command. You can type this all on one line. The CLI ignores returns and looks for a ; to terminate a command.

![](bbox=[0.545, 0.625, 0.916, 0.742])

![](bbox=[0.547, 0.775, 0.916, 0.868])
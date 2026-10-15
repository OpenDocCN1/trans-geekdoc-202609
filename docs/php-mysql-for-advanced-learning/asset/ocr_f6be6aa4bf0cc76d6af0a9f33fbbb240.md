```
```sql
use Chanchal;
```
```

# To check how many tables are there in the present database?

```
```sql
show tables;
```
```

# To insert record in table like in columns i.e. name, email and phone

```
```sql
insert into users(name,email,phone) values ('chanchal', 'chanchal@gmail.com', '878787');
```
```

![](bbox=[0.124, 0.344, 0.711, 0.628])

# To display All records from Table Called - Users

```
```sql
SELECT * FROM users order by name DESC;
```
```

# To display selective columns from the table Only Name and Phone

```
```sql
SELECT name,phone FROM users;
```
```
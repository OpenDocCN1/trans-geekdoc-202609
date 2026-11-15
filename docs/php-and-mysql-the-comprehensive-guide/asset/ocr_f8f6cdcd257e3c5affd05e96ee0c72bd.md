```
$db->beginTransaction();
$sql = "INSERT INTO my_table (field) VALUES ('value13');";
$db->exec($sql);
$sql = "INSERT INTO my_table (field) VALUES ('value14');";
$db->exec($sql);
$db->commit(); //only now the SQL is executed!
?>
```

Listing 18.5 Filling a Table with PDO within a Transaction ("pdo-transaction.php")

# 18.3 Guestbook

A small application example follows here. It implements something very simple, but also commonplace and therefore relevant to practice. Despite the simple structure, all the essential elements of database programming are built into the functionality.

# 18.3.1 Create Table

The guestbook entries are saved in a single table called guestbook. This consists of the fields shown in Table 18.1.

| Field Name | Data Type | Description |
|---|---|---|
| id | INTEGER PRIMARY KEY* | ID |
| heading | VARCHAR(1000) | Title of the entry |
| entry | VARCHAR(5000) | The actual entry |
| author | VARCHAR(50) | Name of the registrant |
| email | VARCHAR(100) | Email address of the registrant |
| date | TIMESTAMP | Time of entry |
| \*Depending on the database, the data type is called something different. | | |

Table 18.1 The Fields of the Guestbook Table

The following listing only creates the table.

```
<?php
try {
    $db = new PDO("mysql:dbname=PHP;host=localhost",
        "user",
        "password");
    $sql = "CREATE TABLE guestbook (
        id INTEGER AUTO_INCREMENT PRIMARY KEY,
```
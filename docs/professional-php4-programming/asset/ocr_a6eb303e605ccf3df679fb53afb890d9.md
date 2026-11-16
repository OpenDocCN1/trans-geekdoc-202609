```
library=# INSERT INTO title
library=# VALUES ('1861005156', 'Beginning Databases with PostgreSQL')
library=# ;
INSERT 101798 1
```

If you attempt to insert a new entry that contains the same primary key value as an existing entry, the insertion attempt will fail.

# DELETE

```
DELETE FROM [ONLY] table [WHERE condition]
```

DELETE is used to remove records from a table. The WHERE clause is an important component of DELETE, UPDATE, and SELECT queries, as it allows you to specify conditions that determine which records your query will affect. The query below will only delete records that have a value of "1861003730" in the ISBN field:

```
Library=# DELETE FROM title WHERE ISBN = '1861003730';
DELETE 1
```

> If you omit the WHERE clause from a DELETE statement, every record in the table will be deleted.

# UPDATE

```
UPDATE [ONLY] table SET col = expression [, ...] [FROM fromlist]
[WHERE condition]
```

UPDATE is used to change the data in existing records in the database. It is important to specify the WHERE condition carefully. The query below only affected one row, but it had the potential to change many rows if more than one record had the same ISBN. This is impossible in this particular example because ISBN is a primary key:

```
library=# UPDATE title SET book_title='New Title' WHERE ISBN='1861003730';
UPDATE 1
```

Even though PostgreSQL honors the notion of referential integrity, there is no automatic protection for it built into the UPDATE or DELETE actions. For example, if author_ID was renamed or removed from the author table, there may still be records in the author_title table that refer to the now non-existing record. Thus, referential integrity has been compromised by the UPDATE or DELETE operation.

> If you omit the WHERE clause from an UPDATE statement, every record in the table will be updated.
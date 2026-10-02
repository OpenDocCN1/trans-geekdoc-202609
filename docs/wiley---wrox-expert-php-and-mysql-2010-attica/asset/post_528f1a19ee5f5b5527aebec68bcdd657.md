
some practical examples of how you can employ triggers to use these UDFs to do things such as work as a sequence, as well as store data in memcached whenever there is a change to a row in a table.

1. The first thing this file creates is a simple table called urls that contains two columns: an id which is the primary key, and url which is a string in which URL values are stored.

```
drop table if exists urls;
create table urls (
  id int(3) not null,
  url varchar(64) not null default '',
  primary key (id)
);
```

2. It then sets up the connection to memcached:

```
select memc_servers_set('localhost:11211');
```

And a simple sequence object that will start at 0:

```
select memc_set('urls:sequence', 0);
```

3. Then the insert trigger is created:

```
DELIMITER |

DROP TRIGGER IF EXISTS url_mem_insert |
CREATE TRIGGER url_mem_insert
BEFORE INSERT ON urls
FOR EACH ROW BEGIN
  SET NEW.id = memc_increment('urls:sequence');
  SET @mm = memc_set(concat('urls:',NEW.id), NEW.url);
END |
```

The trigger url_mem_insert does two things upon (before) the insert of a row to urls:

- Increments the counter object urls:sequence by one.
- Sets the URL value keyed by concatenating the string urls: with the new id value, which was just incremented and then calls memc_set(). The SQL statement SET must be used because you cannot call SELECT from within a trigger.

For instance, the first record inserted will increment urls:sequence to 1, which the value of id will assume, hence the key created will be urls:1, then whatever url value is being inserted into urls will also be inserted into memcached as urls:1.

4. Next, an update trigger:

```
DROP TRIGGER IF EXISTS url_mem_update |
CREATE TRIGGER url_mem_update
BEFORE UPDATE ON urls
FOR EACH ROW BEGIN
  SET @mm = memc_replace(concat('urls:',OLD.id), NEW.url);
END |
```

The trigger url_mem_update is executed any time a record in urls is updated. It uses the same scheme to create a memcached key by concatenating urls: with the id of the record being updated. For example, the first record initially has the value of http://www.foo.com, which, if updated with the URL value of http://www.fee.com, in the updated trigger, results in the call of memc_replace('urls:1', 'http://www.fee.com'); replaces the URL value in memcached as well. The syntax SET is used because you cannot call SELECT from within a trigger.

5. Then finally, a delete trigger:

```
DROP TRIGGER IF EXISTS url_mem_delete |
CREATE TRIGGER url_mem_delete
BEFORE DELETE ON urls
FOR EACH ROW BEGIN
  SET @mm = memc_delete(concat('urls:',OLD.id));
END |
```

## Trigger Execution

The trigger url_mem_delete is executed on the deletion of any row in urls. It also uses the scheme to build a memcached key that the other two triggers use. For example, upon the deletion of a record that contains http://www.fee.com, which has the id value of 1, the UDF memc_delete('urls:1') is called.

trigger_fun.sql, which comes with the source distribution, also has some use case SQL statements to show the triggers in action.

1. First, the data is inserted:

```
insert into urls (url) values ('http://google.com');
insert into urls (url) values ('http://lycos.com/');
insert into urls (url) values ('http://tripod.com/');
insert into urls (url) values ('http://microsoft.com/');
insert into urls (url) values ('http://slashdot.org');
insert into urls (url) values ('http://mysql.com');
insert into urls (url) values ('http://northscale.com/');
insert into urls (url) values ('http://memcached.org/');
```

2. An SQL statement to verify that the data exists in the table is issued:

```
select * from urls;
```

Yet another handy SQL statement verifies each value that you expect to be stored as a result of the previous inserts statements. You can use memc_get() within a query to return several results to select the id from urls for all URLs in the urls table. This constructs a key that can fetch the items cached in memcached.

```
select id, memc_get(concat('urls:', id)) from urls;
```

One of the records is updated and immediately the key for this record is selected from the table as well as fetched from memcached. It should have the updated value — the same value as the select statement following the update:

```
update urls set url= 'http://mysql.com/sun' where url = 'http://mysql.com';
select url from urls where url = 'http://mysql.com/sun';
select memc_get('urls:6');
```

The same type of test is performed, except this time deleting a record:

```
delete from urls where url = 'http://microsoft.com/';
select * from urls where url = 'http://microsoft.com/';
select memc_get('urls:4');
```

Now you can run trigger_fun.sql by command line to verify that these triggers work as advertised:

```
mysql --user root --password test < trigger_fun.sql

memc_servers_set('localhost:11211')
1
memc_set('urls:sequence', 0)
1
```

This is the output of selecting all records from the urls table after inserting the eight records:

| Id | url |
|----|-----|
| 1 | http://google.com |
| 2 | http://lycos.com |
| 3 | http://tripod.com |
| 4 | http://microsoft.com |
| 5 | http://slashdot.org |
| 6 | http://mysql.com |
| 7 | http://northscale.com |
| 8 | http://memcached.org |

The following is the output of fetching the items from memcached using the aggregate query of the id column of the urls table to call memc_get() for each key. You'll see that all the values were in fact stored via the trigger and exactly match the output of the previous query against the urls table:

| Id | memc_get(concat('urls:', id)) |
|----|-------------------------------|
| 1 | http://google.com |
| 2 | http://lycos.com |
| 3 | http://tripod.com |
| 4 | http://microsoft.com |
| 5 | http://slashdot.org |
| 6 | http://mysql.com |
| 7 | http://northscale.com |
| 8 | http://memcached.org |

The following code is the output after the update statement in trigger_fun.sql:

```
update urls set url= 'http://mysql.com/sun' where url = 'http://mysql.com';
```

Then the urls table is queried with the query:

```
select url from urls where url = 'http://mysql.com/sun';
```

| url |
|-----|
| http://mysql.com/sun |

Then the query is run:

```
select memc_get('urls:6');
```

Resulting in the output:

| memc_get('urls:6') | http://mysql.com/sun |

...verifying that the URL http://mysql.com was updated to http://mysql.com/sun both in the urls table and memcached!

Then finally, the record is deleted. Of course, the select from urls for the url http://microsoft.com yields nothing, but for memcached NULL is returned (correct).

| memc_get('urls:4') |
|--------------------|
| NULL |

So, you can see all the triggers work as advertised!

Using triggers can hide all of these details from the application. Values are automatically cached upon writing to the database. This is very convenient and powerful in that it offers an integration of durable data store as well as a method of organizing the keys for the cached items (MySQL) and lightweight, fast caching (memcached)!

> You don't want to use insert or update triggers that automatically set values in memcached when you work with tables that have huge data sets that frequently update; you could end up calling set() or replace() when it's not needed. This is because a trigger doesn't check whether the item in memcached should be set or replaced in the first place; a trigger runs regardless of whether an item in memcached needs to be updated. It's reasonable to use the insert or update triggers on more “static” (tables that don't change often) or small tables that don't have huge data sets. You can definitely use delete triggers on any size table.

## Read-Through Caching with Simple Select Statements

One last part of this chapter is to show how you can use these UDFs to cache data in a single select.

As you saw in Chapter 6, a user would be fetched from the database and memcached in separate SQL statements. You can combine obtaining data and caching in one step.

For example, you can cache a single user, in this case the user with the username of capttofu.

```
mysql> SELECT uid, username, email, firstname, surname,
    -> memc_set(concat('users:uid:',username), uid),
    -> memc_set(concat('users:username:',uid), username),
    -> memc_set(concat('users:email:', username), email),
    -> memc_set(concat('users:firstname:', username), firstname),
    -> memc_set(concat('users:surname:', username), surname)
    -> from users where uid = 1\G
*************************** 1. row ***************************
                      uid: 1
                 username: capttofu
                    email: capttofu@capttofu.org
                firstname: Patrick
                  surname: Galbraith
memc_set(concat('users:uid:',username), uid): 0
memc_set(concat('users:username:',uid), username): 0
```

# Designing the Database

We covered the normalization process in Chapter 1 and before long we'll put these normalization skills to work. For this application the set of information is pretty simple. So simple, in fact, that a single table will do the job. Actually, this isn't quite true. For administrative purposes, you should create a table against which user names and passwords can be authenticated. Here are the create statements that will make the tables.

```
create table guestbook (
  entry_id    integer not null auto_increment,
  name        varchar(40) null,
  location    varchar(40) null,
  email       varchar(40) null,
  url         varchar(40) null,
  comments    text null,
  created     timestamp,
  remote_addr varchar(20) null
  key guestbook_key (entry_id);
```

```
create table guestbook_admin (
  username  varchar(50) not null,
  password  varchar(255) not null
);
```

When adding a user to the guestbook_admin table, it would be best to encrypt the password. The easiest way to do this is by using MySQL's password function.

```
insert into guestbook_admin (username, password)
values ('jay', password('rules'));
```

After you run this command, the actual value stored in the password column is 05cb7f12aad9fe3. When you need to find out whether a user knows the password, you can use the password function.

```
select * from guestbook_admin where
username = 'jay' and
password = (password('rules'));
```
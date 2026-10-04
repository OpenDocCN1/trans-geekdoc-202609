# Part I: Working with MySQL

MySQL date and time types are flexible, accepting either strings or numbers as part of insert statements. Additionally, MySQL is pretty good at interpreting dates that you give it. For instance, if we create this table:

```
create table date_test(
  id int unsigned auto_increment,
  the_date date
);
```

The following insert statements are all interpreted correctly by MySQL:

```
insert into date_test (a_date) values ('00-06-01');
insert into date_test (a_date) values ('2000-06-01');
insert into date_test (a_date) values ('20000601');
insert into test6 (a_date) values (000601);
```

> MySQL prefers to receive dates as strings. '0000601' is a better choice than a similar integer. Using strings for date values may save you from encountering errors down the road.

Extracting information from date and time columns can be a challenge. MySQL provides many functions that help manipulate these columns.

# DATE

Usage: date
The date column type stores values in the format YYYY-MM-DD. It will allow values between 1000-01-01 and 9999-12-31.

# DATETIME

Usage: datetime [null | not null] [default]
The datetime type stores values in the format YYYY-MM-DD HH:MM:SS. It will allow values between 1000-01-01 00:00:00 and 9999-12-31 23:59:59.

# TIMESTAMP

Usage: timestamp(size)
This is a handy column type that will automatically record the time of the most recent change to a row, whether it is an insert or an update. Size can be defined as any number between 2 and 14. Table 2-3 shows the values stored with each column size. The default value is 14.
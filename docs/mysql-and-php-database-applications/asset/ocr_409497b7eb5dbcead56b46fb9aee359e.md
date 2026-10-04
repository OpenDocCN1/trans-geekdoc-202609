# Part I: Working with MySQL

# USING BETWEEN

You can also choose values within a range by using the between predicate between works for numeric values as well as dates. In the following query, lastchanged is a timestamp column. If you wanted to find the people who signed up on the day of June 14, 2000, you could use this query:

```
select * from users where lastchanged between 20000614000000 and 20000614235959
```

Remember that the default column type stores dates in the form YYYYMMDDHMMSS, to get all entries for a single day, you need to start your range at midnight (00:00:00) and end at 11:59:59 pm (23:59:59).

You can also use between on text strings. If you wanted to list all the names in the first half of the alphabet, this query would work. Note that the following query will not include names that start with "m",

```
select * from users where lname between 'a' and 'm'
```

# USING/NOT IN

The in predicate is helpful if there are several possible values for a single column that can be returned. If you wanted the users to get all the states in New England, you could write the query like this:

```
select * from users
where state = 'RI' or
state = 'NH' or
state = 'VT' or
state = 'MA' or
state = 'ME'
```

Using in, you can specify a set of possible values and simplify this statement. The following query would achieve the result.

```
select * from users
where state in ('RI', 'NH', 'VT', 'MA', 'ME')
```

If you need to get the same effect but in reverse, you can use the not in predicate. To get a listing of all people in the table not living in New England, simple through the word 'not':

```
select * from user where
state not in ('RI', 'NH', 'VT', 'MA', 'ME')
```
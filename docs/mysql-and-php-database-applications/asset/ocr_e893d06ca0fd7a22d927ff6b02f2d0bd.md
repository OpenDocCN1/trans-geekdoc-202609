# Part I: Working with MySQL

Within a group, you can also indicate a specific field that is to be counted count will look for the number of non-null values. Take, for example, the table in 3-6.

![](bbox=[0.166, 0.178, 0.737, 0.532])

Figure 3-6: users_ages table

It may not seem that there's much use in counting non-null values from this table. However, if you're the type that's really into statistics, you could use this table to figure out what percentage from each city feels comfortable your age. First you would need a count of all the entries from each specific city and state; following that, you would need a count of all the non-null values in the field.

```
Select city, state, count(*) from user_ages group by state, city
```

From the result in Figure 3-7, you can see that Chicagoans are far more forthcoming than the coasts. This is a good time as any to introduce aliases. There will be times, particularly when you're working with functions, when the column name returned by the query isn't what you'd like it to be. For example, in Figure 3-7 you might wish for a table header more descriptive than count(*).

You can follow any function or column name with the word as and then specify a name you prefer as simply designates an alias. If you need a column name that is more than one word, surround the text string with single quotes.
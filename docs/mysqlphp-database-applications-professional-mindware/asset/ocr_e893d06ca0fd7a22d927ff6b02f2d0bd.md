Within a group by, you can also indicate a specific field that is to be counted. count will look for the number of non-null values. Take, for example, the table in Figure 3-6.

![](bbox=[0.16, 0.19, 0.75, 0.53])

Figure 3-6: users_ages table

It may not seem that there's much use in counting non-null values from this table. However, if you're the type that's really into statistics, you could use this table to figure out what percentage from each city feels comfortable indicating its age. First you'd need a count of all the entries from each specific city and state; following that, you'd need a count of all the non-null values in the age field.

```
Select city, state, count(*), count(age) from user_ages
group by state, city
```

From the result in Figure 3-7, you can see that Chicagoans are far more forthcoming than those from the coasts.

This is as good a time as any to introduce aliases. There will be times, particularly when you're working with functions, when the column name returned by the query isn't what you'd like it to be. For example, in Figure 3-7 you may wish for a table header a bit more descriptive than count(*).

You can follow any function or column name with the word as and then specify a name you prefer. as simply designates an alias. If you need a column name that is more than one word, surround the text string with single quotes.
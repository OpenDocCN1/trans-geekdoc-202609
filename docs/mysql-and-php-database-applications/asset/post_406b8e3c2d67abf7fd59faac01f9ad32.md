
## Chapter 3: Getting What You Want with select

MySQL may not actually create a temporary table for each group; however, the actual inner workings of a group are pretty complex, and this is a good way to think about MySQL is doing.

## COUNT()

Once again, the goal of your query is to find out the number of people from each state that are in your users table. To do that you will use group by count().

Remember that when the group by clause is used, you can imagine MySQL creating a temporary table where it assembles rows. The count() function (you guessed it) counts the number of rows in each of the groups. Check out the following query and the result returned in Figure 3-5.

```sql
select state, count(*) from users group by state
```

![](img/245156cc770929860a3ede93c01f9981_89_0.png)

Figure 3-5: Results of query using select state, count(*) from users group state

Here the asterisk (*) indicates that all rows within the group should be counted. The count(*) function is also handy for getting the total number of rows in a table.

```sql
select count(*) from users
```

Within a group, you can also indicate a specific field that is to be counted; count() will look for the number of non-null values. Take, for example, the table in 3-6.

![](img/245156cc770929860a3ede93c01f9981_90_0.png)

Figure 3-6: users_ages table

It may not seem that there's much use in counting non-null values from this table. However, if you're the type that's really into statistics, you could use this table to figure out what percentage from each city feels comfortable your age. First you would need a count of all the entries from each specific city and state; following that, you would need a count of all the non-null values in the field.

```sql
select city, state, count(*) from user_ages group by state, city
```

From the result in Figure 3-7, you can see that Chicagoans are far more forthcoming than the coasts. This is a good time as any to introduce aliases. There will be times, particularly when you're working with functions, when the column name returned by the query isn't what you'd like it to be. For example, in Figure 3-7 you might wish for a table header more descriptive than count(*).

You can follow any function or column name with the word as and then specify a name you prefer as simply designates an alias. If you need a column name that is more than one word, surround the text string with single quotes.

![](img/245156cc770929860a3ede93c01f9981_91_0.png)

**Figure 3-7:** Results of query count() function

While on the topic of aliases, I'll also mention that there are a variety of functions available in MySQL (see Appendix I). They range from simple math functions to more complex operations. Below I've thrown in some math to clarify the purpose of the query. Notice the use of the as clause and how it affects the display of the query (shown in Figure 3-8).

```sql
select city, state, count(*) as 'Total Rows',
count(age) as 'The Willing',
(count(age)/count(*)*100) as 'Percent Responding'
from user_ages
group by state, city
```

You can use aliases on tables. This will be particularly helpful when dealing with multiple tables. I'll discuss this in further detail in the section "Multi-table join."

## SUM()

The sum() function returns the sum of a given column and is always used with a group clause. For instance, if you are running an application for a non-profit, you might want to know the total contributions from each state. The table you're working with might look like the one in Figure 3-9.

![](img/245156cc770929860a3ede93c01f9981_92_0.png)

Figure 3-8: Results of query using functions and aliases

![](img/245156cc770929860a3ede93c01f9981_92_1.png)

Figure 3-9: Table when using sum() would be helpful

To get the total from each state, you'd run the following query:

```sql
select state, sum(contribution) from contributions group by state
```

## MIN()

The min() function pulls out the lowest value in each grouping. To find the lowest contribution from any state just make a small change to the previous query:

```sql
select state, min(contribution) from contributions group by state
```

## MAX()

As probably guessed, max() will return the highest value in a group:

```sql
select state, max(contribution) from contributions group by state
```

## AVG()

avg() returns the average of the group:

```sql
select state, sum(contribution) from contributions group by state
```

You could throw all these together to create a pretty useful query:

```sql
select state, sum(contribution) as 'Total',
avg(contribution) as 'Average',
min(contribution) as 'Minimum',
max(contribution) as 'Maximum'
from contributions
group by state
```

## GROUP BY

Most databases require that fields in the select clause be used in the group by clause. But MySQL gives you more options; for instance, if you wanted to find out the number of people in each city, you could run the following:

```sql
select city, count(*) from users group by city
```

## HAVING

The having predicate restricts the rows displayed by group by. This is not the same as the where clause. The where clause actually restricts the rows that go into the calculations. If you needed to find the average amount of donations for all the states where the average was over 100, you would have to use having:

```sql
select avg(donations) as avg_contrib, state
from contributions
group by state
having avg(donations) > 100
```

## Joining Tables

If you read Chapter 1, you know that relational databases work so well because they segment information. Different tables hold information on different topics, and fields are inserted into the tables to maintain relationships. After you finish the normalization process, it's likely that none of your tables will be usable without the others. That is why you'll need to join tables in your select statements.

## Two-table join (the equi-join)

For the sake of continuity, we're going to reprise a couple of tables first in Chapter 1. Take a look at the tables in Figure 3–11.

| company_id | company_name | address |
|---|---|---|
| 1 | Big Co Company | 1121 43rd St |
| 2 | Little Co Company | 4444 44th St |

| contract_id | company_id | Name | Title | Phone | Email |
|---|---|---|---|---|---|
| 1 | 1 | Jay Greenspan | Vice President | 415551212 | 1121 43rd St |
| 2 | 1 | Brad Bulder | President | 415555222 | 4444 44th St |
| 3 | 2 | John Doe | Lucky | 2125556666 | 4444 44th St |

Figure 3–11: Tables in a need of join

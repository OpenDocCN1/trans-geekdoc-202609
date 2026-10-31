![](bbox=[0.18, 0.1, 0.77, 0.45])

Figure 3-7: Results of query using count() function

While on the topic of aliases, I'll also mention that there are a variety of functions available in MySQL (see Appendix I). They range from simple math functions to more complex operations. Below I've thrown in some math to clarify the purpose of the query. Notice the use of the as clause and the way it affects the display of the query (shown in Figure 3-8).

```
Select city, state, count(*) as 'Total Rows',
    count(age) as 'The Willing',
    (count(age)/count(*)*100) as 'Percent Responding'
from user_ages
group by state, city
```

You can also use aliases on tables. This will be particularly helpful when dealing with multiple tables. I'll discuss this in further detail in the section “Multi-table join.”

# SUM()

The sum() function returns the sum of a given column and is almost always used with a group by clause. For instance, if you are running an application for a non-profit, you might want to know the total contributions from each state. The table you're working with might look like the one in Figure 3-9.
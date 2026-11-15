SQL Server supports subqueries in a **from** clause, but not in a **check** clause. Some SQL dialects limit their subquery support to the three SQL-89 cases, each of which embeds the subquery in a where clause of an outer query, thus:

```
select ...     -- outer query
from ...
where ...
    (select ... -- subquery
    from ... )
```

If the subquery is self-contained (i.e., it makes no reference to the outer query), it is said to be **uncorrelated**. In this case, it is evaluated first and replaced by its result (e.g., a bag of values) before the outer query is processed. In contrast, **correlated subqueries** refer to their outer query. This section considers only simple, uncorrelated membership and comparison subqueries. Existential and correlated subqueries are covered later.

**Country:**

| countryName | population |
|---|---|
| Australia | 26,477,504 |
| India | 1,428,627,663 |
| Netherlands | 17,618 299 |
| USA | 340,265,309 |

**Mountain:**

| mtName | countryName |
|---|---|
| Kosciuszko | Australia |
| Mana | India |
| McKinley | USA |
| Rainier | USA |

FIG. 12.52 Some countries and some of their mountains (if any).

Let’s now consider **membership subqueries**. The condition *expression in (subquery)* returns True if and only if the value of the expression is included in the subquery result. If the subquery returns the null set, the condition evaluates to unknown. The outer query result includes only the rows where the condition evaluates to True.

To discuss some examples, consider the tables shown in Fig. 12.52. Assume that there is a subset constraint from Mountain.countryName to Country.countryName. The opposite constraint does not apply (e.g., The Netherlands has no mountains). To save space, only some mountains are shown for the countries.

Consider the query, Which mountains are located in a country with more than 100 million people? We could begin by finding the countries with the relevant populations, and then finding the mountains in those countries. This may be set out in SQL as follows:

```
select mtName from Mountain
where countryName in
    (select countryName from Country
    where population > 100000000)
```

The subquery is evaluated first, resulting in the bag (“India”, “USA”). After the subquery has been replaced by this intermediate result, the outer query is evaluated, finally resulting in a list of three mountains: Mana, McKinley, and Rainier. Of course, this query could have been phrased instead using a join. As an exercise, you may wish to do this.
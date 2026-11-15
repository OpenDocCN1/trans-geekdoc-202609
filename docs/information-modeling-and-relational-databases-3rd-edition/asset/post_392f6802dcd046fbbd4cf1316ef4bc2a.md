
| shortName | nationality |
|---|---|
| Colleen | Irish |
| JimO | American |
| Lance | American |
| Norma | Aussie |
| Terry | Aussie |
| Walter | American |

| driver | carModel |
|---|---|
| Colleen | Ford |
| JimO | Honda |
| Lance | Ford |
| Lance | Honda |
| Terry | Saturn |

Who is an American or drives a Ford?

```
select shortName from Person
where nationality = 'American'
union
select driver from Drives
where carModel = 'Ford'
```

| shortName |
|---|
| Colleen |
| Lance |
| Walter |
| JimO |

FIG. 12.50 By default, union eliminates duplicates.

In SQL-92 (and later), a **corresponding** option may be added to specify the common columns used for the union. For example, if the driver in Fig. 12.50 were instead named “shortName”, the query could be declared as **select * from Person union corresponding by (shortName) Drives**. This option is not yet supported by most SQLs, including SQL Server.

Now consider the query, Who drives a Ford, Holden, or Honda (i.e., who drives at least one of these car models)? Although we could formulate this using two unions, the query can be answered with one scan of the rows from the Drives table. So, it is simpler (and more efficient) to use the **or** operator, thus:

```
select driver from Drives
where carModel = 'Ford' or carModel = 'Holden' or carModel = 'Honda'
```

When the operands of a **union** operator are disjoint (i.e., mutually exclusive), the **union** operator is sometimes used to add descriptions to the output even when only one base table is involved. As an example, consider the Expert and Novice tables in Fig. 12.51. Suppose that we want to list the names of the judo players as well as a label to indicate who are the experts and who are the novices. To obtain the names, we can union a **select** query for the judo experts with another **select** query for the judo novices. We could then identify the expert and novice judoka by including the strings “expert judoka” and “novice judoka” in the relevant **select** lists.

We can improve on this by introducing “judo level” as an alias for the labels. This provides a meaningful column header for the labels and allows us to shorten the labels to just “expert” and “novice”, as shown. Notice the use of double quotes in “judo level” to allow an embedded space.

Expert:
| person | sport |
|---|---|
| Ann | aikido |
| Ann | judo |
| Bill | judo |
| John | bujotsu |

Novice:
| person | sport |
|---|---|
| Ann | karatedo |
| Bill | karatedo |
| Cathy | aikido |
| Cathy | judo |
| David | kendo |

select person, 'expert' as "judo level"
from Expert
where sport = 'judo'
union
select person, 'novice' as "judo level"
from Novice
where sport = 'judo'
order by "judo level", person

| person | judo level |
|---|---|
| Ann | expert |
| Bill | expert |
| Cathy | novice |

FIG. 12.51 Constants may be used with union to indicate the source of the rows.

Although this technique of adding descriptive strings in unions is handy when the operands are disjoint, it is not of much use if they overlap. Any originally overlapping rows become disjoint when the string values are added into the rows (because those values differ). Hence, such rows would appear more than once in the union.

In SQL-92 (but not SQL-89), the **intersect** operator is provided for *set intersection* and the **except** operator handles *set difference*. These work analogously to the **union** operator. They are allowed only between **select** queries that return union-compatible tables. Duplicates are removed from the result unless the **all** option is specified.

Refer back to the tables *Person*( shortName, nationality ) and *Drives*( driver, carModel ) in Fig. 12.50. Now consider the query, Which Americans drive a Ford? This means, Who is an American and drives a Ford? Because the nationality facts and carModel facts are in separate tables, this logical “and” operator can naturally be implemented by a table intersection operator, as follows, yielding the result {“Lance”}.

```
select shortName from Person
where nationality = 'American'
intersect
select driver from Drives
where carModel = 'Ford'
```

Similarly, the query “Which Americans do not drive a Ford?” can be formulated as a set difference as follows, yielding the result {“JimO”, “Walter”}.

```
select shortName from Person
where nationality = 'American'
except
select driver from Drives
where carModel = 'Ford'
```

Unlike union and intersection, the difference operator is not commutative. For example, reversing the order of the operands in the previous query results in {“Colleen”} because the reversed query has the different meaning, “Which Ford drivers are not American?”

If the **all** option is used after **intersect** or **except**, it returns a bag intersection or bag difference, respectively. In general, if a row appears _m_ times in one table and _n_ times in another, then it appears min(_m_, _n_) times in the bag intersection and max(_m - n_, 0) times in the bag difference.

Although all the main commercial SQL dialects support the **union** operator, several do not yet support the **intersect** and **except** operators. As we now discuss, these two operators can be emulated using subqueries, so their absence does not entail a loss of functionality.

SQL **subqueries** are like component queries within nested formulations in relational algebra. Although SQL subqueries are queries in their own right, they must be enclosed in parentheses (unlike **select** queries that are unioned), and they have some limitations on their use. Ideally, a language ought to be orthogonal—wherever a value or result is legal, an expression that returns that value or result should be legal. In SQL-89, however, subqueries are allowed only in a few places where their result is legal. Although SQL-92 removed these restrictions, few commercial SQLs are fully orthogonal.

A subquery is a parenthesized **select** query embedded in another query. Let Θ denote one of the comparison operators (=, <>, >, <, <=, >=). In SQL-89, a subquery is legal only in the following three contexts:

- expression [not] **in** (subquery) -- membership subquery
- expression Θ [all | some | any] (subquery) -- [quantified] comparison subquery
- exists (subquery) -- existential subquery

A **membership subquery** follows an **in** operator. In SQL-89, a membership subquery must be a **singleton** query (i.e., it must return a single column). This is consistent with the use of the **in** operator with a bag of values (a column is just a bag of values, displayed vertically). In SQL-92, the **in** operator may be preceded by a row value expression, in which case the subquery may return a multicolumn table.

A **comparison subquery** follows a comparator (e.g., =). If the comparator is modified by one of the quantifiers **all**, **some**, or **any**, this is a _quantified comparison_. In SQL-89, a comparison subquery must return a single column; if the comparison is not quantified, the subquery must return a single value. This is consistent with the normal use of comparison operators. In SQL-92, a comparator may be preceded by a row value expression, in which case the subquery may return a multicolumn table or, if unquantified, a row value. An **existential subquery** appears after the **exists** quantifier and may return any table.

In SQL-92, subqueries may be used in other places (e.g., **from** clauses and **check** clauses), as long as their result table makes sense there (orthogonality). **From** clause subqueries require an alias for the derived table even if not needed. The syntax is:

```
... **from** (subquery) [**as**] _alias_
```

SQL Server supports subqueries in a **from** clause, but not in a **check** clause. Some SQL dialects limit their subquery support to the three SQL-89 cases, each of which embeds the subquery in a where clause of an outer query, thus:

```
select ...     -- outer query
from ...
where ...
    (select ... -- subquery
    from ... )
```

If the subquery is self-contained (i.e., it makes no reference to the outer query), it is said to be **uncorrelated**. In this case, it is evaluated first and replaced by its result (e.g., a bag of values) before the outer query is processed. In contrast, **correlated subqueries** refer to their outer query. This section considers only simple, uncorrelated membership and comparison subqueries. Existential and correlated subqueries are covered later.

Country:
| countryName | population |
|---|---|
| Australia | 26,477,504 |
| India | 1,428,627,663 |
| Netherlands | 17,618,299 |
| USA | 340,265,309 |

Mountain:
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


Here, the same table name “Human” appears in the **from** clause of both inner and outer queries. So, to distinguish the gender column in the inner table from the gender column in the outer table, the alias `X` is introduced for the outer table. This allows us to specify the correlation condition as “gender = `X`.gender”, rather than “gender = gender” (which, of course, would always be true). Here, `X` is said to be a *correlation variable*. You can think of `X` as an extra copy of the Human table.

Alternatively, you can think of it as a tuple variable that ranges over the rows of the Human table, as depicted in [Fig. 12.60](#Ch012_539-646_B9780443237904000268_2.xhtml#f0305). Despite its set-oriented syntax, SQL queries are processed one row at a time. Here, `X` is successively assigned each row of the Human table, passing through six states (in this example), in each of which it holds one row. For each of these states, the inner query is evaluated, computing the average height for the gender currently assigned to `X`. If you’re familiar with programming languages, this should remind you of a nested **for** loop.

![Fig. 12.60 In the outer query, X is successively assigned one of the six rows.](images/B9780443237904000268/f12-60-9780443237904.jpg)

[Fig. 12.60](#Ch012_539-646_B9780443237904000268_2.xhtml#B-f0305) In the outer query, X is successively assigned one of the six rows.

Let’s walk through the execution of the query. At the outer level, we start at the top row, so `X` is assigned the tuple (“Ann”, “F”, 160). Hence, in the outer level, gender = “F” and height = 160. In other words, `X`.gender = “F” and `X`.height = 160. In the subquery, the correlation condition “gender = `X`.gender” now becomes “gender = ‘F’”. So, the subquery returns the average height of the females, which for the given data is 165.

The condition in the outer query now becomes “160 > 165”, which is false. Because the top row does not satisfy the condition, it is filtered out, so Ann is excluded from the result.

At the outer level, we now move on to the second row, so `X` is assigned the tuple (“Bill”, “M”, 180). Hence, `X`.gender = “M” and height = 180. In the subquery, the condition “gender = `X`.gender” becomes “gender = ‘M’”. So, the subquery returns the average height of the males, which is 175. The condition in the outer query now becomes “180 > 175”, which is true. So, Bill’s firstname and height (“Bill”, 180) are included in the result.

Similarly, we move through rows 3, 4, 5, and 6 at the outer level, recomputing the subquery each time. Carol is accepted (170 > 165 is true) but the others are rejected (because the conditions 175 > 175, 165 > 165, and 170 > 175 are all false). So, the final result lists the firstname and height of just Bill and Carol as shown earlier in [Fig. 12.59](#Ch012_539-646_B9780443237904000268_2.xhtml#f0300).

Now consider the table scheme `Employee` (empNr, empName, pay, [bossNr]), where pay stores the weekly pay and bossNr is the employee number of the boss of the employee on that row. The foreign key constraint bossNr **references** empNr also applies. A sample population is shown in [Table 12.16](#Ch012_539-646_B9780443237904000268_2.xhtml#t0085).

[Table 12.16](#Ch012_539-646_B9780443237904000268_2.xhtml#B-t0085)

Who earns at least 80% of his/her boss’s pay?

| ![t12-16-9780443237904](images/B9780443237904000268/t12-16-9780443237904.jpg) |

| --- |

Consider the query: Who earns at least 80% of his/her boss’s pay? Let’s try answering the question first, using the sample data: Employee 1 is eliminated because he/she has no boss. Employee 2 earns 900/1000 or 90% of his/her boss’s pay, employee 3 earns 70% of his/her boss’s pay, and employee 4 earns 780/900 or 86.67% of his/her boss’s pay. So, the result should list employees 2 and 4.

How can we formulate the query in SQL to work with any set of data? You might like to try it yourself before reading on.

The inclusion of the pronoun “his/her” in the question is a clue that the query can be formulated with a correlated subquery, as set out later. `E` is used to denote the employee at the outer level. Although not needed, a second alias `B` has been used to help indicate that the inner employee is a boss.

```
select empNr
```

```
from Employee as E
```

```
where pay >=
```

```
            (select 0.8 * pay
```

```
             from  Employee as B
```

```
             where B.empNr = E.bossNr)
```

As an alternative, you can formulate the query using a self-join as follows:

```
select E.empNr
```

```
from Employee as E join Employee as B
```

```
on E.bossNr = B.empNr
```

```
and E.pay >= 0.8 * B.pay
```

To help you understand the join approach, the following list shows rows formed from the join before the final projection is made on E.empNr.

```
 E                       B empNr empName pay  bossNr empNr empName  pay  bossNr - - - - - - - - - - - - - - - - - -  - - - - - - - - - - - - -- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -. 2     Jones, E  900    1    1     Davis, J   1000   ? 4     Brown, T  780   2    2     Jones, E    900   1
```

As this example suggests, computing a correlated subquery is basically equivalent to computing a join, so some care is needed in the formulation of correlated subqueries to avoid unacceptable performance.

Now, let’s consider *existential subqueries*. In predicate logic, the proposition “There is a frog” may be formulated as “∃*x Fx*”. Here, “∃” is the existential quantifier, with the meaning “there exists at least one”, “*x*” is an individual variable standing for some object, and “*F* …” abbreviates the predicate “… is a frog”.

An existential subquery in SQL is somewhat similar. It appears in an *existential condition* of the form:

```
exists ( subquery )
```

Here, **exists** is used instead of “∃” for the existential quantifier, and subquery is effectively a tuple variable ranging over rows returned by the subquery. The **exists** quantifier may be thought of as a Boolean function, *returning True if the subquery returns a row and False otherwise.*

The **exists** quantifier may be preceded by the logical **not** operator. The possible cases are shown here. The term “a row” means “at least one row”. Because the system always knows whether or not a row is returned, a simple two-valued logic applies—existential conditions evaluate to True or False, never Unknown.

```
exists ( subquery )                    →     True      - - a row is returned (by the subquery)
```

```
                                                                                  →     False     - - no row is returned
```

```
not exists ( subquery )          →     True       - - no row is returned
```

```
                                                                                  →     False     - - a row is returned
```

Existential subqueries may be used within search conditions in a **where** clause, leading to overall queries of the following form:

```
select …
```

```
from  …
```

```
where [ not ] exists
```

```
            ( select * …)
```

Because the mere existence of a row is all that counts in the subquery result, it is normal to simply use “*” instead of a column list in the **select** list for the existential subquery.

Prior to SQL-92, existential subqueries were the only subqueries that could return multiple columns because in SQL-89, both membership and comparison subqueries had to return a single column. Some SQL dialects still have this restriction.

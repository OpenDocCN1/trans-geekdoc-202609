| firstname | gender | height |
| :--- | :--- | :--- |
| Ann | F | 160 |
| Bill | M | 180 |
| Carol | F | 170 |
| David | M | 175 |
| Emily | F | 165 |
| Fred | M | 170 |

```
select firstname, height
from Human as X
where height >
(select avg(height)
from Human
where gender = X.gender)
```

| firstname | height |
| :--- | :--- |
| Bill | 180 |
| Carol | 170 |

List the name and height of those above average height for their gender correlation pronoun

FIG. 12.59 Correlation between inner and outer tables with the same base name.

Here, the same table name “Human” appears in the from clause of both inner and outer queries. So, to distinguish the gender column in the inner table from the gender column in the outer table, the alias X is introduced for the outer table. This allows us to specify the correlation condition as “gender = X.gender”, rather than “gender = gender” (which, of course, would always be true). Here, X is said to be a correlation variable. You can think of X as an extra copy of the Human table.

Alternatively, you can think of it as a tuple variable that ranges over the rows of the Human table, as depicted in Fig. 12.60. Despite its set-oriented syntax, SQL queries are processed one row at a time. Here, X is successively assigned each row of the Human table, passing through six states (in this example), in each of which it holds one row. For each of these states, the inner query is evaluated, computing the average height for the gender currently assigned to X. If you’re familiar with programming languages, this should remind you of a for loop.

| firstname | gender | height |
| :--- | :--- | :--- |
| Ann | F | 160 |
| Bill | M | 180 |
| Carol | F | 170 |
| David | M | 175 |
| Emily | F | 165 |
| Fred | M | 170 |

FIG. 12.60 In the outer query, X is successively assigned one of the six rows.

Let’s walk through the execution of the query. At the outer level, we start at the top row, so X is assigned the tuple (“Ann”, “F”, 160). Hence, in the outer level, gender = “F” and height = 160. In other words, X.gender = “F” and X.height = 160. In the subquery, the correlation condition “gender = X.gender” now becomes “gender = ’F”". So, the subquery returns the average height of the females, which for the given data is 165.

The condition in the outer query now becomes “160 > 165”, which is false. Because the top row does not satisfy the condition, it is filtered out, so Ann is excluded from the result.
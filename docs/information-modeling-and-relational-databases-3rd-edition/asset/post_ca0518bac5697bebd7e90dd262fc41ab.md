
Because of the uniqueness constraint on Speaks, the number of Canadian languages spoken by a country is now the number of rows in the group for that country. So, the left count (*) of the having condition returns the values 1, 1, 2, and 2 for Australia, Belgium, Canada, and Dominica, respectively. The second subquery evaluates to 2, so the overall query returns Canada and Dominica.

This approach can be adapted to handle cases when the relevant column association is not unique by using the distinct option. For example, consider the relation schemas Localization (productCode, "language") and LanguageUse ("language", country, nrSpeakers). The query "Which products are localized into all languages spoken by a country where at least 10 million speak that language?" requires count (distinct ("language")) instead of count (*) in the subquery of the having clause. As discussed later, this grouping approach can be extended to cater for queries that involve set comparisons other than those covered by relational division.

We have now covered most of the basic working of SQL's select statement. The BNF syntax covered so far may be summarized as shown. Unlike the syntax shown here, the SQL standard actually allows a having clause without a group by clause (effectively meaning “group by no columns”) but the semantics are problematic, so we'll ignore this option.

```
select [all | distinct ] * | expression ([ as ] column-alias )[ ,...]
from table ([ as ] alias )
   [| cross join table ([ as ] alias )
   | natural [ inner | { left | right | full } [ outer ] ] join table ([ as ] alias )
   | [ inner | { left | right | full } [ outer ] ] join table ([ as ] alias )
       { on condition | using ( col-list ) }
   | union join table ([ as ] alias )
       [...] ]
[ where col-condition ]
[ group by colname [ ,...]
   [having group-condition ] ]
[ union | intersect | except ... ]
[ order by col [ asc | desc ] [ ,...] ]
```

Of the nine table operations of relational algebra, we have discussed the equivalent SQL formulation for the general case of five (projection, selection, Cartesian product, $\Theta$-join, and union) and for special cases of three (intersection, difference, and division). The rename operation of relational algebra is handled using a view (see later chapter). The general cases of intersection, difference, and division can be handled using joins, and also with correlated and existential subqueries, as discussed in the next section.

## Exercise 12.10

- 1. This question refers to the library database discussed in Exercise 12.9. The relational schema is repeated here.

![](img/1344db3eba3d550e6edb009556fcd95c_653_0.png)

- 2. Assume ISBN is based on a character data type. Formulate SQL queries for the following requests.

  - (a) How many authors of each gender are there?
  - (b) Place authors into groups of the same gender and nationality, indicating how many there are in each group, with the larger groups shown first.
  - (c) Considering only the books published after 1980, list the publishers and the total number of copies of their books in the library.
  - (d) For each publisher having an average number of library copies per book above two, show the earliest publication year.
  - (e) List the ISBN and the number of authors for each book published before 1986 that has more than one author.
  - (f) Restricting attention to male authors of a book published by Hall or Possum, list the number of such authors for each nationality that has at least as many authors of this kind as there are copies in the library of the book with ISBN “444”。

- 3. The relational schema for a dietary database is shown (for a sample population, see Exercise 12.8). Formulate the following queries in SQL

![](img/1344db3eba3d550e6edb009556fcd95c_653_1.png)

  - (a) Who eats all the foods?
  - (b) Which foods are eaten by all eaters?

## 12.11 SQL: Correlated and Existential Subqueries

This section extends the subquery work in Section 12.8 by considering correlated and existential subqueries. The subqueries discussed earlier were simple, uncorrelated subqueries. An uncorrelated subquery is computed once, replaced by its result, and the outer query is run. In contrast, a _correlated subquery_ relates its search condition to each row of a table named in the outer query and is effectively recomputed for each outer row (see Fig. 12.58).

![](img/1344db3eba3d550e6edb009556fcd95c_654_0.png)

Because of repeated computation, correlated subqueries can sometimes be slow to run. However, they significantly extend the range of queries that can be expressed as a single SQL query and are well worth mastering. Let us refer to the condition inside the correlated subquery as the correlation condition. This condition typically takes the form:

```
a \Theta b
```

where _a_ is an _inner column_ (listed in the _from_ clause of the subquery), _b_ is an _outer column_ (listed in the _from_ clause of the outer query), and \(\Theta\) is a _comparator_ (e.g., =, >).

To avoid ambiguity, the column names for _a_ or _b_ may need to be qualified by a table name. The basic cases are summarized in Table 12.15. Local scope is assumed by default, so we may normally leave _a_ unqualified (unless it occurs in two inner tables). However, if _a_ and _b_ have the same unqualified name, we need to distinguish _b_ by qualifying it with its outer table name. If the outer table has the same name as the inner table, introduce an alias for it to distinguish it from the inner table.

| Case | Situation | Declaration |
|---|---|---|
| 1 | _a_ is the name of a column in inner table only _b_ is the name of a column in outer table only | _a_ \Theta _b_ |
| 2 | _a_, _b_ are the same column name but in different tables _T_ is the base name of the outer table | _a_ \Theta _T.b_ |
| 3 | inner and outer tables have the same base name _X_ is an alias introduced for the outer table | _a_ \Theta _X.b_ |

For example, consider the table scheme _Human_ (firstname, gender, height). For simplicity, assume that people in this UoD can be identified by their firstname. A sample population is provided in Fig. 12.59, along with a correlated subquery to retrieve the name and height (in cm) of those who are above average height for _their_ gender. In English, correlations are often made with a _pronoun_, such as “their”, “his/her”, “its”, and “that”. In this context, pronouns effectively function as object variables.

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

Let’s walk through the execution of the query. At the outer level, we start at the top row, so X is assigned the tuple (“Ann”, “F”, 160). Hence, in the outer level, gender = “F” and height = 160. In other words, X.gender = “F” and X.height = 160. In the subquery, the correlation condition “gender = X.gender” now becomes “gender = “F””. So, the subquery returns the average height of the females, which for the given data is 165.

The condition in the outer query now becomes “160 > 165”, which is false. Because the top row does not satisfy the condition, it is filtered out, so Ann is excluded from the result.

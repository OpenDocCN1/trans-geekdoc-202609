
The condition c used to express this comparison of attributes between tables is called the join condition. The join condition may be composite (e.g., a1 < b1 and a2 < b2). Because of the Cartesian product, the resulting table has a number of columns equal to the sum of the number of columns in A and B, but because of the selection operation, it typically has far fewer rows than the product of the numbers of rows of the joined tables.

With most joins, the comparison operator used is =. The Θ-join is then called an equijoin. Thus, the equijoin of A and B equating values in column a of A with column b of B is A × B restricted to the rows where A.a = B.b. If the join column names are different in each table, there is no need to qualify them with table names. We write this as shown here. In general, the join condition may contain many equalities.

```
(A × B) where A.a = B.b
or
(A × B) where a = b   { if a, b occur in only one of A, B }
```

Let's consider an example. Fig. 12.17 includes a simple conceptual schema and its corresponding relational schema.

![](img/1344db3eba3d550e6edb009556fcd95c_575_0.png)

FIG. 12.17 The ORM schema (a) maps to the relational schema (b).

A sample population is given in Fig. 12.18.

**Employee:**
| empNr | empName | gender |
|---|---|---|
| 001 | Haggar, T | M |
| 002 | Wong, S | F |
| 003 | Jones, E | F |
| 004 | Mifune, K | M |

**Drives:**
| empNr | carRegNr |
|---|---|
| 001 | ABC123 |
| 003 | ABC123 |
| 003 | TAH007 |

FIG. 12.18 A sample population for the schema in Fig. 12.17.

Before formulating queries, familiarize yourself with the structure and contents of the database. From the schema, we see that employees are identified by their employee number, and their name and gender must also be recorded. An employee may drive many cars, and the same car may be driven by many employees. The population is not significant because it does not include instances where the same name applies to more than one employee. However, it does illustrate that driving cars is optional (employees 002 and 004), that an employee may drive more than one car (employee 003), and that the same car may be driven by more than one employee (car ABC123).

Now consider the following query: “List the employee number, name, and cars for each employee who drives a car.”

We could specify this by the equijoin in Fig. 12.19, which joins the tables by equating their empNr attributes. To help explain this, dotted lines have been added between the base tables to indicate which rows match on their empNr value. Only the first and third rows from the Employee table are able to find a match. The third row (003) finds two matches. Check the result for yourself.

Because these join columns have the same local name “empNr”, qualified names are used to distinguish the columns in the query and the join result. The join columns don’t have to have the same (unqualified) name, but must belong to the same domain. For example, if the employee number column in the Drives table was named “empId”, the join condition could be specified as “empNr = empId”.

| empNr | empName | gender |
|---|---|---|
| 001 | Hagar, T | M |
| 002 | Wong, S | F |
| 003 | Jones, E | F |
| 004 | Mifune, K | M |

| empNr | carRegNr |
|---|---|
| 001 | ABC123 |
| 003 | ABC123 |
| 003 | TAH007 |

(Employee × Drives) where Employee.empNr = Drives.empNr

| Employee.empNr | empName | gender | Drives.empNr | carRegNr |
|---|---|---|---|---|
| 001 | Hagar, T | M | 001 | ABC123 |
| 003 | Jones, E | F | 003 | ABC123 |
| 003 | Jones, E | F | 003 | TAH007 |

FIG. 12.19 An equijoin.

An equijoin contains two matching columns resulting from each join attribute (note the two empNr columns). If these columns refer to the same thing in the UoD (and they typically do), then one of these columns is redundant. In this case, we lose no information if we delete one of these matching columns (by performing a projection on all but the column to be deleted). This is done in Fig. 12.20.

(Employee × Drives)
where Employee.empNr = Drives.empNr
[Employee.empNr, empName, gender, carRegNr]

| Employee.empNr | empName | gender | carRegNr |
|---|---|---|---|
| 001 | Hagar, T | M | ABC123 |
| 003 | Jones, E | F | ABC123 |
| 003 | Jones, E | F | TAH007 |

FIG. 12.20 The duplicate column is removed by projection on the equijoin.

If the columns used for joining have the same name in both tables, then the unqualified name is used in the join result. The resulting table is then said to be the natural inner join of the original tables. Because “inner” is assumed by default, the natural inner join may be expressed simply as natural join (outer joins are discussed later). This is by far the most common join operation in practice. The natural join of tables A and B may be written as A ⋈ B, or in words as “A natural join B”. This may be summarized as follows.

- To compute A ⋈ B:
- Form A × B
- For each column name c that occurs in both A and B
- Apply the restriction A.c = B.c
- Remove B.c
- Rename A.c to c

There is no need to name the join columns because these are the ones with the same names in both tables (and of course these must be based on the same domain). To help remember the bow-tie “⋈” notation, note that “⋈” looks like a cross “×” with two vertical lines added, suggesting that a natural join is a Cartesian product plus two other operations (selection of rows with equal values for the common columns, followed by projection to delete redundant columns). Fig. 12.21 shows the natural join for our driving example. Note that the empNr column appears just once and is unqualified.

![](img/1344db3eba3d550e6edb009556fcd95c_577_0.png)

If the tables have no column names in common, then the natural join is simply the Cartesian product. Like the Cartesian product, natural join is associative: (A ⋈ B) ⋈ C = A ⋈ (B ⋈ C). So, expressions of the form A ⋈ B ⋈ C are unambiguous.

Tables being joined may have zero, one, or more common columns. In any case, the natural join is restricted to those rows where all the common attributes have the same value in both tables. The number of columns in A ⋈ B equals the sum of the number of columns in A and B, minus the number of columns common to both.

To illustrate a natural join on many attributes, consider the UoD in Fig. 12.22. First examine the conceptual schema. Within a bank branch, an account may be identified by its local account number. But different accounts in different branches may have the same local account number. So, globally, the bank identifies accounts by a combination of branch and account number. Clients are identified by a global client number and have a name (not necessarily unique). Not all clients need an account. The relational schema is included in Fig. 12.22.

![](img/1344db3eba3d550e6edb009556fcd95c_578_0.png)

FIG. 12.22 Account has a composite identification scheme.

Notice the subset and equality constraints between the tables shown in Fig. 12.22. Joins are usually, although not always, made across such constraint links. Simple joins may be performed on clientNr, and composite joins on branchNr-accountNr pairs (which identify accounts). Fig. 12.23 shows sample data.

| branchNr | accountNr | balance |
|---|---|---|
| 10 | 54 | 3000.00 |
| 10 | 77 | 500.55 |
| 23 | 54 | 1000.00 |

| clientNr | clientName |
|---|---|
| 1001 | Jones, ME |
| 1002 | Jones, TA |
| 2013 | Jones, ME |
| 7654 | Seldon, H |
| 8005 | Shankara, TA |

| branchNr | accountNr | clientNr |
|---|---|---|
| 10 | 54 | 1001 |
| 10 | 54 | 1002 |
| 10 | 77 | 2013 |
| 23 | 54 | 7654 |

FIG. 12.23 Sample population for the bank schema.

The two queries in Fig. 12.24 use natural joins to display users and balances of accounts. The first query matches accounts by joining on both branchNr and accountNr. To add client names, the second query also matches clients by joining on clientNr.

In rare cases, comparison operators other than equality are used in joins. As a simple example, consider the Drinker and Smoker tables in Fig. 12.25. These might result from a decision to map subtypes of Patient to separate tables.

Suppose we wanted a list of drinker, smoker pairs, where the drinker and smoker are distinct persons. This can be formulated by a <>-join as shown. Here, the comparison operator is “<>”. Notice that because drinkers and smokers overlap, some patient doubles may appear twice (in different order). Similarly, <-joins, ->joins, <=-joins and >=-joins may be defined.

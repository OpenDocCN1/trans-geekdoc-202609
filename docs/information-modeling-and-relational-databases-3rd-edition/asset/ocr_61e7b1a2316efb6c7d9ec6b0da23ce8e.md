+   (l) List the kind, composition, and extra status of all the statements, giving precedence to statements extra to Pascal. Statements with the same extra status should be listed starting with those of simple composition, with those of similar composition being shown in reverse alphabetic order.

+   (m) List alphabetically the kinds of statements that are neither structured nor extra to Pascal.

+   (n) List in reverse alphabetic order the kinds of those statements that are either structured and extra to Pascal or simple.

+   (o) As for (n) but exclude the exit statement from consideration and include the composition of each. Show all the structured statements first, in reverse alphabetic order, followed by the simple statements, in reverse alphabetic order.

# 12.6 SQL: Joins

We have seen how to choose, and order, columns and rows from a single table. But suppose the information we need from a single query is spread over many tables. SQL provides two main methods to access such information. The first of these uses relational **joins** and is discussed in this section. The second involves subqueries and is treated in a later section.

A **cross join** (Cartesian product) of tables pairs all the rows of one with all the rows of the other. In SQL-89, a cross join is specified by listing the tables in the **from** clause, using a **comma** “”, for the Cartesian product operator (× in relational algebra). A **conditional join** (Θ-join) selects only those rows from the Cartesian product that satisfy a specified condition. In SQL-89, the condition is specified in a **where** clause. So, the query expressions in Table 12.7 are equivalent.

| Join type | Relational algebra | SQL-89 |
| --- | --- | --- |
| Cross join | A × B | select * from A, B |
| Conditional join | A × B where A.a Θ B.b | select * from A, B where A.a Θ B.b |

The SQL-89 syntax has drawbacks. First, it fails to distinguish join conditions (intertable comparisons) from nonjoin conditions (intratable comparisons on the same base row), instead lumping them together in a single **where** clause.

Second, it uses a comma for the cross join operation. This is unintuitive and also overloads the comma with different meanings. Third, it does not provide any direct support for operations such as outer joins, which can occur in practical queries.

For such reasons, SQL-92 (and later) uses special syntax for various kinds of join. In addition to supporting the SQL-89 syntax, the newer standards include special notations for the following types of join (here, any text after “—” is a comment):
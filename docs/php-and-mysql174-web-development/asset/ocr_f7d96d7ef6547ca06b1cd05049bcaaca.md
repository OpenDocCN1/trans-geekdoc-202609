In this case, a single value is returned from the subquery (the maximum amount) and then used for comparison in the outer query. This is a good example of subquery because this particular query cannot be elegantly reproduced using joins in ANSI SQL.

The same output, produced by this join query:

```
SELECT CustomerID, Amount
FROM Orders
ORDER By Amount DESC
LIMIT 1;
```

Because it relies on LIMIT, this query is not compatible with most RDBMSs.

One of the means that MySQL did not get subqueries for so long was there is very little that you cannot do without.

You can use subquery values in this way with all the normal comparison operators. Some special comparison operators are also available and detailed in the next section.

# Subqueries and Operators

There are five special subquery operators. Four are used with regular operators, and one (EXISTS) is used only with correlated subqueries and is covered in the next section. The four regular subquery operators are shown in Table 10.4.

Table 10.4 Subquery Operators
| Name | Sample Syntax | Description |
| ANY | SELECT c1 FROM t1 WHERE c1 > ANY (SELECT c1 FROM t2); | Returns true if the comparison is true for any of the rows in the subquery |
| IN | SELECT c1 FROM t1 WHERE c1 IN (SELECT c1 from t2); | Equivalent to =ANY |
| SOME | SELECT c1 FROM t1 WHERE c1 > SOME (SELECT c1 FROM t2)! | Alias for ANY; sometimes reads better to the human ear |
| ALL | SELECT c1 FROM t1 WHERE c1 > ALL (SELECT c1 from t2); | Returns true if the comparison is true for all of the rows in the subquery |

Each of these operators can appear only after a comparison operator, except for IN, which has its comparison operator (=) "rolled in," so to speak.
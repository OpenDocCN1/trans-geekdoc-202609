the Y columns in A and B so that we know which column in B corresponds to which column in A.

The result of A ÷ B is formed by restricting the result to those X entries in A whose associated Y entries in A include all the row entries of B. The expression A ÷ B may also be written as A divide-by B. Fig. 12.26 shows a trivial example, where the attribute domains are denoted by X1, X2, Y1.

![](bbox=[0.24, 0.23, 0.72, 0.34])

FIG. 12.26 A simple example used to explain relational division.

Although not used very often, the division operation can be useful in listing rows that are associated with at least all rows of another table expression (e.g., who can supply all the items on our stock list?).

As a practical example, suppose the table Speaks (country, language) stores facts about which countries speak (i.e., use) which languages. A sample population is shown in the large table within Fig. 12.27. Now consider the query: Which countries speak all the languages spoken in Canada? To answer this, we first find all the languages spoken in Canada, using the expression Speaks where country = ‘Canada’ [language]. This returns the table {English, French}. We then divide the Speaks table by this result, as shown, to obtain the final answer {Canada, Dominica}.

![](bbox=[0.22, 0.61, 0.75, 0.76])

FIG. 12.27 A practical example of relational division.

# Renaming

Recall Fig. 12.7, where we defined an alias for a table name. Relational assignment can also be used to provide a new table name, but it cannot be used to change the attribute names. For that, we need the rename operator. A relational algebra expression may include any of the relational operations discussed earlier (union, projection, selection, join, etc.) and is essentially a query that returns a table. In general, the rename operator applied to a
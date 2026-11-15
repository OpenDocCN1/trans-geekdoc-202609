Looking at the tables, we can now see that all three tables are needed. The Account table holds the balances, the Client table holds the client names, and the AcUser table indicates who uses what account.

Because we have sample data, we can first try to answer the English query, examine what we did, and finally try to express this in the formal language of relational algebra. If we were answering the request ourselves, we might go to the Account table and select just the rows where the balance exceeded $700. This yields the account (10, 54) and the account (23, 54). We might then look at the AcUser table to see who uses these accounts. This yields the clients numbered 1001, 1002, and 7654. Now we look to the Client table to find out their names (“Jones, ME”, “Jones, TA” “Seldon, H”). So, our answer is {(1001, “Jones, ME”), (1002, “Jones, TA”), (7654, “Seldon, H”)}.

Retracing and generalizing our steps, we see that we joined the Account and AcUser tables by matching the account (branchNr and accountNr), and we linked with the Client table by joining on clientNr. Because these attributes have the same names over the tables, we can use natural joins. We may set this out in relational algebra as:

```
(Account where balance > 700) [ branchNr, accountNr ]
>< AcUser
>< Client [ clientNr, clientName ]
```

This isn't the only way we could express the query. For instance, using a top-down approach, both joins could have been done before selecting or projecting, thus:

```
(Account >< AcUser >< Client
where balance > 700
[ clientNr, clientName ]
```

Notice how queries may be spread over many lines to make them more readable. A useful syntax check is to ensure that you have the same number of opening and closing brackets. Although these two queries are logically equivalent, if executed in the evaluation order shown, the second query is less efficient because it involves a larger join.

Relational algebra can be used to specify transformation rules between equivalent queries to obtain an optimally efficient, or at least a more efficient, formulation. SQL database systems include a query optimizer to translate queries into an optimized form before executing them. So, in practice we often formulate queries in ways that are easy for us to think about them rather than worrying about efficiency considerations.

Because relational algebra systems are not used in practice, you can ignore efficiency considerations when doing exercises in the algebra. However, for complex queries in SQL, practical optimizers are not perfect, and you may need to tune your queries to achieve the desired performance. In some cases, hand tuning a complex query can reduce its execution time dramatically (e.g., from hours to minutes).

As our next example, let's return to the Speaks table mentioned earlier. Consider the query: list each pair of countries that share a common language. For example, one pair
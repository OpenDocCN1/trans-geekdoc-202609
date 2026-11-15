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
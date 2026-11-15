| right outer | select * from A natural right [outer] join B -- other cases: cf. left join | select B.c, ... -- omit A.c ... -- rest as for left join, -- but swap A and B |
| --- | --- | --- |
| full outer | select * from A natural full [outer] join B -- other cases: cf. left join; -- rarely used | union of left and right outer joins |
| union | select * from A union join B -- rarely used | select A.cols, ' ', ... -- ' ' U B col from A union all select ' ', ..., B.cols -- ' ' U A col from B |

| firstname | height |
| --- | --- |
| Dick | 72 |
| Necito | 70 |
| Pat | 68 |
| Scot | 72 |

| firstname | height |
| --- | --- |
| Linda | 60 |
| Mary | 62 |

| Male.firstname | Female.firstname |
| --- | --- |
| Dick | Linda |
| Dick | Mary |
| Necito | Linda |
| Necito | Mary |
| Pat | Mary |
| Pat | Linda |
| Scot | Linda |
| Scot | Mary |

```
select Male.firstname, Female.firstname
from Male cross join Female
<->
```

FIG. 12.41 Listing all possible Male-Female pairs.

Most dialects of SQL now support the new syntax for cross joins and qualified joins (including outer joins), but some do not yet support the newer syntax for natural joins. Let's now consider each of the new join notations.

For cross join, the cross join syntax may be used instead of a comma. This syntax is best reserved for unrestricted joins (full Cartesian products). As an example, Fig. 12.41 shows details of Male and Female tennis players. The query lists possible male-female pairs for mixed-doubles teams. Cross joins are fairly rare in practice.

Much more common are conditional joins. The new syntax includes the join operator in the from clause, and the join condition in an on clause. Fig. 12.42 shows a relational schema, a sample population, and a conditional join query to retrieve the name of each female employee and her department. To aid readability, it's a good idea to indent the on clause, as shown. Each column mentioned in the query occurs in just one of the tables, so there is no need to qualify column names with table names. In this case, the join takes place along the foreign key reference shown in Fig. 12.42. Although joins often involve foreign key references, they don't have to. All we need is that the columns being joined are based on the same domain.

Column-list joins match values in the specified columns with the same local name in both tables. The new syntax uses the word join in the from clause, with the relevant
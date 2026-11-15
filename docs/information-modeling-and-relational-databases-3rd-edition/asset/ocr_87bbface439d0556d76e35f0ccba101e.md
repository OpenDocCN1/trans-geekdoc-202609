which are similar to the examples we used when discussing XQuery. If this xmltable function call is contained in a select statement, the value being passed could be selected from a suitable xml column in a table.

```
xmltable ('//movies'
passing movieXML
columns
"Seqno" for ordinality,
"MovieNr" int path '@movieNr',
"Movie Name" varchar (50) path 'title',
"Release Year" char(4) path 'released'
"Director" varchar(50) path 'director' )
```

The resulting table would have the following form, and could be aliased and so on, in the same way as a table produced by other means.

In this case, values in the automatically generated SeqNo column and the retrieved MovieNr column are coincidentally the same. Had the XML data been in a different order, the SeqNo column would remain unchanged, but the MovieNr column (and the other retrieved columns) would reflect the XML element ordering.

| SeqNo | MovieNr | Movie Name | Release year | Director |
|---|---|---|---|---|
| 1 | 1 | Cosmology | 2006 | Lee Lafferty |
| 2 | 2 | Kung Fu Hustle | 2004 | Stephen Chow |
| 3 | 3 | The Secret Garden | 1987 | Alan Grint |
| 4 | 4 | The Secret Garden | 1993 | Agnieszka Holland |
| 5 | 5 | The Da Vinci Code | 2006 | Ron Howard |

# Exercise 16.2

The following schema shows part of a database that holds information about repair technicians and the types of assemblies that they are competent to repair. Different technicians may be competent at repairing different assemblies.

![](bbox=[0.233, 0.801, 0.743, 0.955])
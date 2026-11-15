Alternatively, we could replace any of the subqueries by a join. For example, the following formulation uses three joins and no subqueries:

```
select customerNr, customerName, invoiceNr
from       Customer natural join Invoice
natural join Lineitem
natural join Item
```

If your SQL dialect doesn't support the natural join syntax, use either the conditional join syntax or the old SQL-89 join syntax instead.

As a negated example of subqueries, the following query lists the countries with no mountains. For the given population, this results in just one country, The Netherlands.

```
select countryName from Country
where countryName not in
(select countryName from Mountain)
```

Can you replace a negated subquery with an inner join? No! However, you can replace it with an outer join. For example, the aforementioned query may be reformulated as:

```
select countryName
from Country natural left outer join Mountain
where mtName is null
```

The query may also be formulated using a set difference operation, thus:

```
select countryName from Country
except
select countryName from Mountain
```

To list those countries that do have mountains, the following query could be used:

```
select countryName from Country
where countryName in
(select countryName from Mountain)
```

This performs a set intersection and is equivalent to:

```
select countryName from Country
intersect
select countryName from Mountain
```

So, when just single columns are required, the use of **in** and **not in** with subqueries enables set intersection and set difference operations to be formulated even in SQL-89. To discuss this further, recall the Person ( shortName, nationality) and Drives ( driver, carModel) tables from the previous section. For convenience, the sample population for these tables is repeated in Fig. 12.54.
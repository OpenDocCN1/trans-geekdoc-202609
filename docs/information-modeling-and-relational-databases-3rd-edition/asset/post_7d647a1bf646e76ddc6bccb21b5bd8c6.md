
In many versions of SQL, the use of **group by** causes a default ordering equivalent to a matching **order by** clause (e.g., **order by family** in this case). However, this is not part of the SQL standard. The syntax of the **group by** clause is:

```
group by col-name [, ...]
```

Members of the same group must have matching values for all the columns named in the **group by** clause.

The next example places particles into groups having both the same family name and the same charge.

```
select family, charge, count(*) as tally
from Particle
group by family, charge
order by family, charge
```

| family | charge | tally |
| :--- | :--- | :--- |
| baryon | -1 | 2 |
| baryon | 0 | 4 |
| baryon | 1 | 2 |
| lepton | -1 | 2 |
| lepton | 0 | 2 |
| meson | -1 | 2 |
| meson | 0 | 3 |
| meson | 1 | 2 |

If more than one column is used for grouping, the order in which these columns are specified is irrelevant to the content of the result. This is because the same set of groups must be formed. For example, if we group by attributes a, b, or b, a then the group with values a=a1, b=b1 is the same as the group with values b=b1, a=a1, and so on.

However, if the row order is based on the group order, the order of rows in the result may be different. For example, the following query returns the same rows as the previous query, in a different order. You can adjust the **order by** clause to change the order:

```
select family, charge, count(*) as tally
from Particle
group by charge, family
order by charge, family
```

| family | charge | tally |
| :--- | :--- | :--- |
| baryon | -1 | 2 |
| lepton | -1 | 2 |
| meson | -1 | 2 |
| baryon | 0 | 4 |
| lepton | 0 | 2 |
| meson | 0 | 3 |
| baryon | 1 | 2 |
| meson | 1 | 2 |

If a function call in the **select** list is used as an ordering criterion, you should introduce an alias for it so that you can reference it by name in the **order by** clause. For example, the following query lists each family and the mass of its lightest particle, ordering by that minimum mass. As an undesirable alternative, you can reference it by its position in the **select** list (e.g., **order by 2**).

```sql
select family, min (mass) as minMass
from Particle
group by family
order by minMass
```

| family | minMass |
| :--- | :--- |
| lepton | 0 |
| meson | 264 |
| baryon | 1836 |

Use of a group by clause implies that items in the `select` list are to be applied to each group as a whole, returning just one value for each group. So, any columns mentioned in the `select` list must either be grouped columns or must appear there as an argument to a built-in function (e.g., family and mass in the aforementioned query). So, when grouping is being performed it makes no sense, and is in fact illegal, to include a nongrouped column as a whole item in the `select` list. For example:

```sql
select family, mass from Particle  -- Error!
group by family
```

Because the same family may include several particles of different mass, this request is plain silly (which mass would we choose?). We can, however, obtain a single grouped value related to mass by using a built-in function, such as `min (mass)` or `avg (mass)`, as we did with the previous query.

Although the `select` list must not include any nongrouped columns, it is legal to group by columns that are not mentioned in the `select` list. For example, the following query lists the minimum mass, but not the name, of each family.

```sql
select min (mass) as minMass
from Particle
group by family
```

| minMass |
| :--- |
| 0 |
| 264 |
| 1836 |

Within the `select` statement, a `where` clause may be included to filter out unwanted rows before the groups are formed and functions are applied. Sensibly, the `where` clause must be placed before the `group by` clause. For example, the following query lists each family and the average mass of its uncharged particles. To cater for dialects such as SQL Server that truncate averages, the mass has been coerced to real by multiplying by 1.0, and the `cast` function is used to display just two digits after the decimal point. Note that it's legal to apply a scalar function to a bag function, for example, `cast (avg (...))`. It is, however, illegal to apply a bag function to a bag function, for example, `min (avg (...))`.

```sql
select family, cast (avg (1.0*mass) as decimal (6,2)) as avgUnchargedMass
from Particle
where charge = 0
group by family
```

| family | avgUnchargedMass |
| :--- | :--- |
| baryon | 2232.25 |
| lepton | 0.00 |
| meson | 770.65 |

Sometimes, we wish to restrict our attention to only those groups that satisfy a certain condition. Just as a **where** clause may be used to impose a search condition on individual rows, a **having** clause may be used to impose a search condition on individual groups. In this case, the **having** clause must be placed straight after the **group by** clause to which it is logically connected. The syntax is:

```
group by col-name [, ...]
having group-condition
```

The usual rules for search conditions apply. Logical and comparison operators may be included in the condition. Each comparison compares some property of the group, such as min (mass), with a constant or another group property. (Although rare, it is possible to include a **having** clause without an associated **group by** clause; in this case, the entire table is treated as one group.) As a simple example, the following query lists the families with more than four particles, and the number of particles for each. Although it makes sense to allow aliases (e.g., tally) in the **having** clause, this is not allowed in many SQLs (e.g., SQL Server).

```
select family, count (*) as tally
from Particle
group by family
having count (*) > 4
```

| family | tally |
|--------|-------|
| baryon | 8 |
| meson | 7 |

The next example is harder. To help clarify how it works, the numbers 1 through 6 have been added to indicate the order in which the query lines are processed. These numbers are not part of the query. Trace through the steps yourself to make sure that you follow this order. With respect to the **having** clause, note that the charged leptons are included (uncharged leptons with zero mass are filtered out by the **where** clause) and that the charged baryons are excluded (their maximum mass exceeds 2000).

Considering only the charged particles, form groups with the same family name, where the group's lightest particle has a mass above 0 and the group's heaviest particle has a mass below 2000. List the family name, number of particles, and largest mass for each group, showing groups with more members first.

```
5 select family, count (*) as chargedTally, max(mass) as maxChargedMass
1 from Particle
2 where charge <> 0
3 group by family
4 having min (mass) > 0 and max (mass) < 2000
6 order by chargedTally desc
```

| family | chargedTally | maxChargedMass |
|--------|--------------|----------------|
| meson | 4 | 966 |
| lepton | 2 | 207 |

One trivial use of grouping is simply to avoid duplicates. For example, the following query may be used as an alternative to select distinct family from Particle:

```
select family from Particle
group by family
```

| family |
| --- |
| baryon |
| lepton |
| meson |

Now suppose we issue the following query. What will be the result?

```
select family from Particle
group by family
having count (*) = 4
```

Comparing this with the previous query, you may feel that the count of each family will be 1 and hence no rows will be returned (i.e., the result is the null set). No! When the group by clause does its work, each group still has all its members (which of course all have the same group value). The having clause now filters out those groups that do not satisfy its search condition. Finally, the select list determines which group properties are listed. The groups are first sorted into three families, two of these families are eliminated (the baryons and mesons), and finally just the family name “lepton” of the remaining group (the four leptons) is listed.

As a further application of grouping, let’s consider how simple cases of relational division can be handled. Fig. 12.57 shows an SQL query for an example handled earlier in Fig. 12.27 by relational division. Here, the column name “language” is double quoted because it is a reserved word.

Although SQL provides no operator for relational division, we achieve the same effect by grouping as shown. The first subquery yields (“English,” “French”), so the where clause filters out the Dutch and Spanish rows before the groups are formed.

| country | language |
| --- | --- |
| Australia | English |
| Belgium | Dutch |
| Belgium | French |
| Canada | English |
| Canada | French |
| Cuba | Spanish |
| Dominica | English |
| Dominica | French |

Which countries speak all the languages spoken in Canada?

```
select country from Speaks
where "language" in
(select "language" from Speaks
where country = 'Canada')
group by country
having count (*) =
(select count(*) from Speaks
where country = 'Canada')
```

| country |
| --- |
| Canada |
| Dominica |

FIG. 12.57 Grouping can be used to perform relational division.

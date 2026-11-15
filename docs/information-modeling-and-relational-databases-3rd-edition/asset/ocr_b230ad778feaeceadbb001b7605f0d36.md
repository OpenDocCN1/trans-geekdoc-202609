```
```sql
select family, min (mass) as minMass
from Particle
group by family
order by minMass
```
```

| family | minMass |
| :--- | :--- |
| lepton | 0 |
| meson | 264 |
| baryon | 1836 |

Use of a group by clause implies that items in the `select` list are to be applied to each group as a whole, returning just one value for each group. So, any columns mentioned in the `select` list must either be grouped columns or must appear there as an argument to a built-in function (e.g., family and mass in the aforementioned query). So, when grouping is being performed it makes no sense, and is in fact illegal, to include a nongrouped column as a whole item in the `select` list. For example:

```
```sql
select family, mass from Particle → Error!
group by family
```
```

Because the same family may include several particles of different mass, this request is plain silly (which mass would we choose?). We can, however, obtain a single grouped value related to mass by using a built-in function, such as `min (mass)` or `avg (mass)`, as we did with the previous query.

Although the `select` list must not include any nongrouped columns, it is legal to group by columns that are not mentioned in the `select` list. For example, the following query lists the minimum mass, but not the name, of each family.

```
```sql
select min (mass) as minMass
from Particle
group by family
```
```

| minMass |
| :--- |
| 0 |
| 264 |
| 1836 |

Within the `select` statement, a `where` clause may be included to filter out unwanted rows before the groups are formed and functions are applied. Sensibly, the `where` clause must be placed before the `group by` clause. For example, the following query lists each family and the average mass of its uncharged particles. To cater for dialects such as SQL Server that truncate averages, the mass has been coerced to real by multiplying by 1.0, and the `cast` function is used to display just two digits after the decimal point. Note that it's legal to apply a scalar function to a bag function, for example, `cast (avg (...))`. It is, however, illegal to apply a bag function to a bag function, for example, `min (avg (...))`.

```
```sql
select family, cast (avg (1.0*mass) as decimal (6,2)) as avgUnchargedMass
from Particle
where charge = 0
group by family
```
```

| family | avgUnchargedMass |
| :--- | :--- |
| baryon | 2232.25 |
| lepton | 0.00 |
| meson | 770.65 |
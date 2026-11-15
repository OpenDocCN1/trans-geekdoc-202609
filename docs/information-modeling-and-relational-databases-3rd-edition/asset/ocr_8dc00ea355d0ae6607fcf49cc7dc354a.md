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
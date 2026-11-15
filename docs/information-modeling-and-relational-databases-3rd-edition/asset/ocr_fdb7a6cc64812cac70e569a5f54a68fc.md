query returns all the populations because each is not equal to some (i.e., at least one) of the populations, and SQL treats “<> any” to mean “<> some”.
As a proper use of a quantified comparison, consider the query: Which country has the largest population? This may be formulated as follows.

```
select countryName
from Country
where population >= all (select population from Country)
```

Remember that all is interpreted distributively as “each, taken individually” rather than collectively. The query result correctly lists India. As discussed in the next section, a max function could alternatively be used to reformulate the search condition as population=(select max(population) from Country). As discussed later, however, quantified comparisons can also handle some cases not amenable to functions (e.g., group extrema).

# Exercise 12.8

1. A database is used to store information on diets. The relational schema and a sample population are provided. Weight (or, more correctly, mass) is measured in kilograms.

![](bbox=[0.375, 0.497, 0.625, 0.61])

| person | weight | gender |
|---|---|---|
| Ann | 70 | F |
| Bill | 70 | M |
| Humphrey | 150 | M |
| Sue | 60 | F |

| foodName | foodClass |
|---|---|
| apple | fruit |
| beef | meat |
| chicken | meat |
| orange | fruit |
| peas | vegetable |
| potato | vegetable |

| person | foodName |
|---|---|
| Ann | apple |
| Ann | beef |
| Ann | potato |
| Bill | apple |
| Bill | potato |
| Humphrey | apple |
| Humphrey | beef |
| Humphrey | chicken |
| Humphrey | orange |
| Humphrey | peas |
| Humphrey | potato |
| Sue | apple |
| Sue | chicken |
| Sue | orange |
| Sue | peas |
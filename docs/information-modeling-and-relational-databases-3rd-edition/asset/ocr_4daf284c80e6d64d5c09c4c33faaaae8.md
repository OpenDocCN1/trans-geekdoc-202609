after the first event pop(Country) changes from { } to {US, JP}, and pop(CountryCode) changes from { } to {“US”, “JP”}. Assuming the universe of discourse (UoD) is just about the Olympics, the entity type Country is the set of all countries that might possibly compete in the Olympic Games.

A predicate occurs within an elementary fact type or reference type (a.k.a. existential fact type. Reference types are usually abbreviated as a parenthesized reference mode. Roles in a reference type are called referential roles. Roles in an elementary fact type are called “fact roles”. Each entity type in a completed conceptual schema plays at least one referential role and, unless it is declared independent (see Section 6.3), at least one fact role. In general, the population of an entity type equals the union of the population of its roles. Unless the entity type is independent, its population is the union of the populations of its fact roles.

For example, the populated schema in Fig. 5.3 indicates the size (in square kilometers) and carbon dioxide emissions (as a percentage of worldwide emissions) of some countries as measured in 2020. The Country entity type might include many countries (e.g., from Afghanistan to Zimbabwe), but this state of the database lists only four countries. Each instance in the database population of Country plays the role r1, r2, or both. So, the current population of Country is the set of all the instances referenced in either the r1 column or the r2 column.

```
We could set this out as:
pop(Country) = pop(r1) ∪ pop(r2)
= {AU, FR, US} ∪ {AU, CN, US}
= {AU, CN, FR, US}
```

Here, “∪” is the operator for set union. The union of two sets is the set of all the elements in either or both. For instance, {1,2} ∪ {2, 3, 4} = {1, 2, 3, 4}. In the case just given, Australia and the United States occur in both role populations while China and France occur in only one.

![](bbox=[0.15, 0.75, 0.72, 0.91])
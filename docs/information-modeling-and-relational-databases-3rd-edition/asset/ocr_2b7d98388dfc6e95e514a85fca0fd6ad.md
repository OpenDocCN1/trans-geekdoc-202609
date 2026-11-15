We can imagine unaries or binaries that should be split, but in practice not even a novice designer is likely to verbalize one (e.g., “The Barrister with surname ‘Rumpole’ smokes and drinks”). So, the question of splittability is really an issue only with ternaries and longer fact types.

To help decide when to split in such cases, the so-called “n–1 rule” may be used: each n-ary fact type has a key length of at least n – 1. If this rule is violated, the fact type is not elementary, and hence should be split. Various cases of this rule are set out in Table 4.6. A proof is sketched later in the section.

If a fact type is elementary, all its keys must be of the same length. Either there is exactly one key, which spans the whole fact type, or there are one or more keys and each is one role shorter than the fact type. So, if two or more roles in a predicate are not part of a key, the fact type is compound and must be split.

# Table 4.6 Key length check for ternaries and longer fact types.

| Arity of fact type | Minimum key length | Illegal key lengths |
|---|---|---|
| 3 | 2 | 1 |
| 4 | 3 | 1, 2 |
| 5 | 4 | 1, 2, 3 |
| n | n − 1 | 1, ..., n − 2 |

# Table 4.7 Country data.

| Country | Population | Area (sq. km) |
|---|---|---|
| Australia | 26,477,504 | 7,686,850 |
| Germany | 83,294,633 | 356,910 |
| United States | 340,265,309 | 9,372,610 |

To start with the simplest case, a ternary fact type can be split if it has a simple key. Consider the sample extract of geographic data shown in Table 4.7. The first row of data may be verbalized: “The Country with name ‘Australia’ has a Population of 26,477,504 people and an Area of 7,686,850 square kilometers”. The presence of “and” suggests that the fact is splittable. Suppose, however, that we ignore this linguistic clue and model using the ternary Country has Population and Area.

Our familiarity with the UoD tells us that, at any given time, each country has at most one population and at most one area. So, there is a UC on the Country column of the fact table. Although the populations and areas in Table 4.7 are unique, our common sense indicates that this is not significant. For example, the population of India is projected to soon equal China’s population, and it is certainly possible to have two countries of the same size. The combination of population and area need not be unique either. This leaves us with the simple UC on the Country role as shown in Fig. 4.45.
As an exercise, draw a model for the following marriage conventions: polyandry (a woman may have many husbands but not vice versa); polygyny (a man may have many wives but not vice versa); and polygamy (a man may have many wives, and a woman may have many husbands).

UCs are best understood in the context of a populated schema diagram, as discussed in this section. With this understanding, for any given fact type each role is associated with a corresponding column of the fact table.

In terms of logical predicates, the role boxes are the “object holes”. For a set of relationship instances of this type, the holes expand to columns. Marking a single role with a uniqueness bar means that entries in the associated column must be unique in that column (i.e., no duplicates are allowed in that column).

A spanning UC requires that each fact row be unique in the table. This whole row constraint applies to any asserted fact type. If we have a stronger UC, then the whole row constraint is implied by this and hence is redundant. For this reason, we never mark the whole row constraint across a fact type unless that is the only UC that applies.

With this understanding, we must choose exactly one of the four constraint patterns shown in Fig. 4.17 for any binary predicate. For brevity, a and b denote object variables, and “a R’s b” means “a bears the relation R to b”.

(a)
R
--
a b
No duplicates are allowed in a’s column.
Each a R’s at most one b.

(b)
R
--
a b
No duplicates are allowed in b’s column.
Each b is R’d by at most one a.

(c)
R
--
a b
Both the foregoing constraints apply.

(d)
R
--
a b
No duplicate (a, b) rows are allowed.
Each a may R many b and vice versa.

FIG. 4.17 The four uniqueness constraint patterns for a binary.

Provided a significant example is supplied, the UCs on a predicate can be determined simply by looking for duplicates in its fact table. If we are not familiar with the application, we may be unsure as to whether the population is significant. Consider for example the output report of Table 4.1.

# Table 4.1 An output report of doubtful significance.

| Reviewer | Paper Nr |
|---|---|
| Jones E | 1 |
| Smith JB | 2 |
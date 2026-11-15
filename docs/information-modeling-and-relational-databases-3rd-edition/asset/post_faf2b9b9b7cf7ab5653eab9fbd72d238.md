
Conceptually, the situation is summarized by the following equivalence:

Person seeking Degree studies Subject iff   Person seeks Degree
                                             and studies Subject.

Here “iff” abbreviates “if and only if”. The projection corresponds to the conditional: if the ternary is true then the conjunction is true. The join corresponds to the conditional: if the conjunction is true then the ternary is true. Any compound fact can always be formulated as a logical conjunction (using “and”).

In principle (although of little use in practice, as discussed later), the following projection-join check can be applied to test whether a fact type is compound (and hence splittable).

![](img/1344db3eba3d550e6edb009556fcd95c_177_0.png)

FIG. 4.55 Compound fact types can be split by projection and restored by join.

- Provide a significant fact table for the fact type.
- Split this table into two or more projections.
- Recombine by natural (inner) join.
- The fact type is splittable in this way iff the result is the same as the original.

An inner join is acceptable because the conceptual fact table (and hence its projections) cannot have nulls. We chose a significant population for the ternary example just discussed, so the test confirms that ternary’s splittability.

Now consider our familiar ternary example about people scoring ratings for subjects. A significant fact table is provided for it in Fig. 4.56(a). Suppose we suspect that this ternary is splittable on Person. For example, we might feel that in this UoD, the following equivalence holds:

Person scored Rating for Subject iff   Person scored Rating
                                        and studied Subject.

To test this way to split, we could form the two binary projections shown in Fig. 4.56(b), and then recombine by joining on Person. The result is shown in Fig. 4.56(c). As an exercise, please confirm this result. In forming the join, several new rows (marked in bold italics) appeared that were not in the original table. Any one of these new rows is enough to prove that the fact type cannot be split this way (i.e., on Person).

### (a)

![](img/1344db3eba3d550e6edb009556fcd95c_178_0.png)

T1:
| Adams | 7 | CS112 |
| Adams | 6 | CS110 |
| Adams | 7 | PD102 |
| Brown | 6 | CS112 |
| Brown | 7 | PD102 |
| Collins | 7 | CS112 |

### (b)

![](img/1344db3eba3d550e6edb009556fcd95c_178_1.png)

T2:
| Adams | 7 |
| Adams | 6 |
| Brown | 6 |
| Brown | 7 |
| Collins | 7 |

T3:
| Adams | CS112 |
| Adams | CS110 |
| Adams | PD102 |
| Brown | CS112 |
| Brown | PD102 |
| Collins | CS112 |

### (c)

![](img/1344db3eba3d550e6edb009556fcd95c_178_2.png)

T4:
| Adams | 7 | CS112 |
| **Adams** | **7** | **CS110** |
| Adams | 7 | PD102 |
| **Adams** | **6** | **CS112** |
| **Adams** | **6** | **PD102** |
| Adams | 6 | CS110 |
| Brown | 6 | CS112 |
| Brown | 6 | PD102 |
| **Brown** | **6** | **PD102** |
| **Brown** | **7** | **CS112** |
| Brown | 7 | PD102 |
| Collins | 7 | CS112 |

new rows

Consider for instance the fact from the first row of our original table: The person with surname “Adams” scored a rating of 7 for the subject CS112. We attempted to split this fact into the two separate facts: Adams scored a rating of 7; Adams studied CS112 (see first rows of the two projections). If this splitting is legitimate, the two separate facts must, in combination, be equivalent to the original fact. But they are not. Adams can score more than one rating and study more than one subject. Knowing that Adams scored a 7 does not tell us the subject(s) for which Adams scored this rating. It could be any of Adams’s subjects (CS112, CS110, or PD102).

Joining the projections causes each rating of Adams to be paired with each subject of Adams. Some of these rows were not present in the original, and the join does not tell us which ones apply to the original ternary. Because we are unable to construct the population of the original ternary from the new ternary population, information has been lost. Hence, the new ternary fact type is not equivalent to the original fact type. So, the original ternary fact type cannot be split this way.

This projection-join check invalidated the proposed equivalence Person scored Rating for Subject iff Person scored Rating and studied Subject. The forward conditional of the equivalence does hold (if ternary then conjunction). However, the backward conditional fails (it is not generally true that if conjunction then ternary). Simply understanding the English verbalization of the fact types should be enough for us to understand that “Person scored Rating for Subject” differs in meaning from “Person scored Rating and studied Subject” if we read “and” in a purely conjunctive sense. Another way to spot the difference is that the UC on the join in fact type in Fig. 4.56(c) is weaker than that of the original in Fig. 4.56(a).

If you use some insight, it should be clear that trying to split on Subject, Rating, or all three would be pointless. In this case, you may conclude that the fact type is unsplittable and leave it as a ternary. If this is not clear, then you can use the algorithm to test all possible ways of splitting. You will find that none of them work.

In general, for a ternary A-B-C there are four ways in which it might split: A-B, A-C; B-A, B-C; C-A, C-B; and A-B, A-C, B-C. In the fourth case, the schema diagram is triangular in shape; this is referred to as three-way splitting. As an exercise, draw these four possibilities. With three-way splitting, the join should be done in two stages. For example, first join A-B and A-C (with A common); then join the A-B-C result of this join with B-C (with B and C common).

A classic example of testing for three-way splitting involves the fact type Agent sells Car for Company. Even if the key spans the whole fact type, the fact type can be split into three binaries if a derivation rule allows the ternary to be deduced from the binaries. Such examples are very rare in practice. For an n-ary fact type, if the n-way split fails (by generating new rows in the final join) then all other ways of splitting can be ruled out too: the fact type is unsplittable.

Although useful for understanding splittability, the projection-join test is of little practical value for determining splittability. The problem is that it only works if the population is significant. But to know the population is significant implies that we know all the constraints, and have crafted a population to illustrate these constraints. If we already know what the constraints are, it is obvious whether the fact type is elementary, so there’s no need to do any projection-join test.

In Fig. 4.55(a), for example, if we already know that each person seeks at most one degree, then we need to separate out the underlying binary. In Fig. 4.56(a), there was no similar constraint because a person can score many ratings. Formally this is the only difference between the two cases, but it’s enough for us to determine splittability without resorting to the tedious projection-join test. The best test for splittability is to work linguistically with the domain expert to see if a fact can be phrased as a conjunction, and to test this with carefully chosen instances. We have more to say on the semantic dependencies in Section 4.6. In case you feel like you’ve just wasted a lot of time learning a projection-join check that is of theoretical interest only, please don’t be upset. It’s very useful to understand what the projection and join operations are at both conceptual and logical levels. Apart from their modeling impact, these operations are used extensively in both conceptual and relational query languages, as we’ll discuss later.

## Exercise 4.6

- 1. A template for a ternary fact type is outlined here. The population shown is significant.

![](img/1344db3eba3d550e6edb009556fcd95c_180_0.png)

- (a) Add the UCs for this fact type.
- (b) Use the projection-join test to show that this fact type cannot be split into two binaries with C as the common node.
- (c) Use the projection-join test to show that this can be split on B into two binaries.
- (d) Draw a schema outline for this result.

## 4.7 Summary

In step 4 of the CSDP, we add UCs and check the arity of fact types. UCs come in two varieties: internal and external. An internal (or intrapredicate) UC applies to one or more roles of the same predicate. It is marked as a bar across the constrained role(s). If the roles are noncontiguous, the bar is divided, with a dotted line connecting its active parts.

Redundancy is repetition of an elementary fact. Because redundancy is not permitted in a conceptual fact table, each row must be unique. This is shown as a UC across the whole predicate, unless a stronger UC exists. If an internal UC spans just some of the roles spanned by another internal UC, the former UC implies the latter UC, and the implied UC should not be displayed.

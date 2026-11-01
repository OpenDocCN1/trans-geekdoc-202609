
# Version Space Representation

## Incremental Property and Hypothesis Space

One important property of this approach is that it is incremental: one never has to go back and reexamine the old examples. All remaining hypotheses are guaranteed to be consistent with them already. But there is an obvious problem. We already said that the hypothesis space is enormous, so how can we possibly write down this enormous disjunction?

The following simple analogy is very helpful. How do you represent all the real numbers between 1 and 2? After all, there are an infinite number of them! The answer is to use an interval representation that just specifies the boundaries of the set: \[1,2\]. It works because we have an ordering on the real numbers.

## Boundary Sets G-set and S-set

We also have an ordering on the hypothesis space, namely, generalization/specialization. This is a partial ordering, which means that each boundary will not be a point but rather a set of hypotheses called a boundary set. The great thing is that we can represent the entire version space using just two boundary sets: a most general boundary (the `G-set`) and a most specific boundary (the `S-set`). Everything in between is guaranteed to be consistent with the examples. Before we prove this, let us recap:

<p class="sidebar">Boundary set</p> <p class="sidebar">G-set</p> <p class="sidebar">S-set</p>

•The current version space is the set of hypotheses consistent with all the examples so far. It is represented by the `S-set` and `G-set`, each of which is a set of hypotheses.
•Every member of the `S-set` is consistent with all observations so far, and there are no consistent hypotheses that are more specific.
•Every member of the `G-set` is consistent with all observations so far, and there are no consistent hypotheses that are more general.

We want the initial version space (before any examples have been seen) to represent all possible hypotheses. We do this by setting the `G-set` to contain `True` (the hypothesis that contains everything), and the `S-set` to contain `False` (the hypothesis whose extension is empty).

## Sufficiency of Boundary Representation

[Figure 20.4](#Chapter20-01.xhtml#fig20-4) shows the general structure of the boundary-set representation of the version space. To show that the representation is sufficient, we need the following two properties:

Description
Two sets called `s-set`, and `g-set` are shown at the top and bottom part of the image. The G set consists of the following: `G_1`, `G_2`, `G_3`, up to `G_m`. The `S-set` consists of the following: `S_1`, `S_2`, `S_3`, up to `S_m`. A trapezoidal section is shown above the `G-set` and below the `S-set`, and are labeled, This region all inconsistent. Several nodes re shown below `G-set` and above `S-set`. Each elements in the G set are connected to certain nodes, which then forms a network toward `S-set`. An arrow labeled More general points upward, and another arrow labeled More specific points downward.

×![](images/Fig-294.jpg)

Figure 20.4 The version space contains all hypotheses consistent with the examples.

1. Every consistent hypothesis (other than those in the boundary sets) is more specific than some member of the `G-set`, and more general than some member of the `S-set`. (That is, there are no “stragglers” left outside.) This follows directly from the definitions of `S` and `G`. If there were a straggler `h`, then it would have to be no more specific than any member of `G`, in which case it belongs in `G`; or no more general than any member of `S`, in which case it belongs in `S`.
2. Every hypothesis more specific than some member of the `G-set` and more general than some member of the `S-set` is a consistent hypothesis. (That is, there are no “holes” between the boundaries.) Any `h` between `S` and `G` must reject all the negative examples rejected by each member of `G` (because it is more specific), and must accept all the positive examples accepted by any member of `S` (because it is more general). Thus, `h` must agree with all the examples, and therefore cannot be inconsistent. [Figure 20.5](#Chapter20-01.xhtml#fig20-5) shows the situation: there are no known examples outside `S` but inside `G`, so any hypothesis in the gap must be consistent.

Description
The tree diagram starts with a root node represented by a small box at the bottom. An arrow from the root node points toward the upper left toward a node labeled Grandparent (George, Anne). A line from the root node joins a node on the upper right labeled Negation Grandparent (George, Anne). An arrow from Grandparent (George, Anne) is labeled open curly bracket y slash Annie close curly bracket and points toward a node on the upper left labeled Negation Parent (Elizabeth, y) or Grandparent (George, y). A line from Grandparent (George, Anne) joins a node on the upper right labeled Parent (Elizabeth, Anne). An arrow from Negation Parent (Elizabeth, y) or Grandparent (George, y) is labeled open curly bracket x slash George, z slash Elizabeth close curly bracket and points toward a node on the upper left labeled Negation Parent (x, z) or Parent (z, y) or Grandparent (x, y). A line from Negation Parent (Elizabeth, y) or Grandparent (George, y) joins a node on the upper right labeled Parent (George, Elizabeth).

×![](images/Fig-295.jpg)

Figure 20.5 The extensions of the members of `G` and `S`. No known examples lie in between the two sets of boundaries.

We have therefore shown that if `S` and `G` are maintained according to their definitions, then they provide a satisfactory representation of the version space. The only remaining problem is how to update `S` and `G` for a new example (the job of the `VERSION-SPACE-UPDATE` function). This may appear rather complicated at first, but from the definitions and with the help of [Figure 20.4](#Chapter20-01.xhtml#fig20-4), it is not too hard to reconstruct the algorithm.

## Updating S and G

We need to worry about the members `Si` and `Gi` of the `S-set` and `G-set`. For each one, the new example may be a false positive or a false negative.
1. False positive for `Si`: This means `Si` is too general, but there are no consistent specializations of `Si` (by definition), so we throw it out of the `S-set`.
2. False negative for `Si`: This means `Si` is too specific, so we replace it by all its immediate generalizations, provided they are more specific than some member of `G`.
3. False positive for `Gi`: This means `Gi` is too general, so we replace it by all its immediate specializations, provided they are more general than some member of `S`.
4. False negative for `Gi`: This means `Gi` is too specific, but there are no consistent generalizations of `Gi` (by definition) so we throw it out of the `G-set`.

We continue these operations for each new example until one of three things happens:
1. We have exactly one hypothesis left in the version space, in which case we return it as the unique hypothesis.
2. The version space collapses—either `S` or `G` becomes empty, indicating that there are no consistent hypotheses for the training set. This is the same case as the failure of the simple version of the decision tree algorithm.
3. We run out of examples and have several hypotheses remaining in the version space. This means the version space represents a disjunction of hypotheses. For any new example, if all the disjuncts agree, then we can return their classification of the example. If they disagree, one possibility is to take the majority vote.

We leave as an exercise the application of the `VERSION-SPACE-LEARNING` algorithm to the restaurant data.

## Drawbacks

There are two principal drawbacks to the version-space approach:
•If the domain contains noise or insufficient attributes for exact classification, the version space will always collapse.
•If we allow unlimited disjunction in the hypothesis space, the `S-set` will always contain a single most-specific hypothesis, namely, the disjunction of the descriptions of the positive examples seen to date. Similarly, the `G-set` will contain just the negation of the disjunction of the descriptions of the negative examples.

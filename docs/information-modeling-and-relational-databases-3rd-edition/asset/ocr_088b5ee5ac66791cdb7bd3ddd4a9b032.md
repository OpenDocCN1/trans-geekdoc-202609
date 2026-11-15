synonym transitivity, constrained by a maximum length of the transitivity chain and relativized to group meanings.

Now consider the marriage fact type in Fig. 7.17. The husband and wife roles are mutually exclusive. In contrast to an irreflexive constraint, which requires inequality between entries on the same row, an exclusion constraint applies between columns and hence is much stronger. If no entry may occur in both columns, we cannot have two rows of the form (a, b) and (b, a). So, exclusion implies asymmetry. Moreover, asymmetry implies irreflexivity. Because they are implied, neither the asymmetric nor the irreflexive constraint should be added to the schema.

Now, let's return to the populated parenthood model in Fig. 7.18(a). There is still a problem with it. Can you spot it? Let us agree that incest cannot occur in our UoD (if it can, we instead declare a deontic rule, as discussed in Chapter 10). If Ann is a parent of Bill and Bill is a parent of Colin, then Ann cannot be a parent of Colin. The parenthood relation is intransitive (i.e., if one person is a parent of a second and the second person is parent of a third, then the first person cannot be parent of the third). In general, for any relation type R:

> $R$ is intransitive iff \(\forall x,y,z [(xRy \& yRz) \rightarrow \sim xRz]\)

Fig. 7.18(b) shows an intuition icon for intransitivity, with a bar across the forbidden jump. A simplified version of this icon (without arrow tips) is used as shown on the right in Fig. 7.18(b). Fig. 7.18(c) signifies that parenthood is both intransitive and asymmetric by combining the constraints in a single icon. The population is changed to satisfy the constraints.

![](bbox=[0.24, 0.535, 0.46, 0.705])

FIG. 7.17 The exclusion constraint implies asymmetry and hence irreflexivity.

![](bbox=[0.105, 0.755, 0.9, 0.93])

FIG. 7.18 The parenthood relation is asymmetric and intransitive.
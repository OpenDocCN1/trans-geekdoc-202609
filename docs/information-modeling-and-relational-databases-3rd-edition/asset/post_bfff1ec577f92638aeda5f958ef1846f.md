
Fig. 7.15(a) uses different-colored nodes to indicate the objects are different. A simplified version of this icon, without arrow tips, is used to depict an *antisymmetric constraint*, as shown in Fig. 7.15(b). The equivalence at the bottom of Fig. 7.15(b) indicates that asymmetry combines antisymmetry and irreflexivity.

```
$R$ is *antisymmetric* iff $\forall x, y [(x \neq y \& xRy) \rightarrow \neg yRx]$
```

![](img/1344db3eba3d550e6edb009556fcd95c_308_0.png)

FIG. 7.15 Antisymmetry.

Before continuing with the parenthood example, let’s look at some other examples to clarify the ideas discussed so far. Our first case deals with a system to record synonyms. A synonym for a word has roughly the same meaning as that word. A sample taken from a poorly designed book of synonyms is shown in Table 7.1.

## Table 7.1 Extract from a poorly constructed table of synonyms.

| Word | Synonyms |
| :--- | :--- |
| abate | diminish, lessen, reduce, decline |
| abbreviate | shorten, reduce, condense |
| : | : |
| condense | compress, consolidate, abridge |
| : | : |
| reduce | shorten, weaken, abate |
| : | : |

![](img/1344db3eba3d550e6edb009556fcd95c_308_1.png)

FIG. 7.16 Examples of (a) symmetric and irreflexive, and (b) asymmetric fact types.

Suppose we decide to store this information in the has-synonym binary shown in Fig. 7.16(a). Is this reflexive? Although we might argue that each word is a synonym of itself, this is a trivial result that we are not usually interested in seeing. So, as far as this relation goes, let us agree that no word is its own synonym. This makes the relation irreflexive, as shown by the inner ring constraint.

If one word is a synonym of another, then the other is a synonym for it. So has-synonym is symmetric. But Table 7.1 violates this condition. For example, the pair ("abbreviate", "reduce") appears in this order only. If we look up the word "reduce", we won't see "abbreviate" as one of its synonyms. This is a defect of the synonym book to avoid in a computerized synonym system. How can we avoid this problem?

One solution is to add the constraint that the has-synonym predicate is symmetric. This is specified on the diagram using a simplified (no arrow tips) version of the symmetry icon in Fig. 7.10, shown as the outer ring constraint in Fig. 7.16(a). The symmetric and irreflexive constraints are combined into one icon to save space. ORM 1 uses the alternative `O sym` notation for symmetry constraints.

Suppose the symmetric constraint is declared, the table is currently empty, and the following update is attempted: **add**: Word ‘abbreviate’ has synonym Word ‘shorten’. A naive information processor would simply reject this for violating the symmetry constraint. A sophisticated processor might accept the fact and automatically add its converse: “shorten” has synonym “abbreviate”. A consistent scheme would be adopted for the delete operation. Although this approach works, it doubles the size of the table because each pair of synonyms is stored twice, once for each ordering.

To save space, we could store each pair in one order only. The post-synonym binary in Fig. 7.16(b) has the second word alphabetically after the first. The pair (“abandon”, “leave”) is stored in this order only. The relation is then asymmetric, as indicated. The larger synonym relation can now be derived, using a derivation rule such as

```
Word₁ has synonym Word₂   iff       Word₁ has post_synonym Word₂
                                      or
                                      Word₂ has post_synonym Word₁.
```

In SQL, the derived relation could be defined as a view on the base relation by using the **union** operator. For speed, both columns can be indexed. Users might perform updates on the base relation, but issue queries on the derived relation. Thus, we can sometimes choose whether to capture an aspect of the UoD in terms of a database constraint or as a derivation rule. Here, we distinguished the asserted and derived fact types by name. It is also possible to have the fact type semiderived.

What about transitivity of synonymy? This issue is complex. You may be familiar with the “bald-hairy paradox” based on the claim that always if we add one hair to the head of a bald man, he is still bald (where is the paradox?). A similar slippery-slope argument argues against synonym transitivity (sequences of approximations finally lead to nonapproximations). Moreover, the same word may have different meanings, leading to different synonym groups. If we still want to retain some transitivity, we may include a derivation rule for synonym transitivity, constrained by a maximum length of the transitivity chain and relativized to group meanings.

Now consider the marriage fact type in Fig. 7.17. The husband and wife roles are mutually exclusive. In contrast to an irreflexive constraint, which requires inequality between entries on the same row, an exclusion constraint applies between columns and hence is much stronger. If no entry may occur in both columns, we cannot have two rows of the form (a, b) and (b, a). So, exclusion implies asymmetry. Moreover, asymmetry implies irreflexivity. Because they are implied, neither the asymmetric nor the irreflexive constraint should be added to the schema.

Now, let's return to the populated parenthood model in Fig. 7.18(a). There is still a problem with it. Can you spot it? Let us agree that incest cannot occur in our UoD (if it can, we instead declare a deontic rule, as discussed in Chapter 10). If Ann is a parent of Bill and Bill is a parent of Colin, then Ann cannot be a parent of Colin. The parenthood relation is intransitive (i.e., if one person is a parent of a second and the second person is parent of a third, then the first person cannot be parent of the third). In general, for any relation type R:

> $R$ is intransitive iff \(\forall x,y,z [(xRy \& yRz) \rightarrow \sim xRz]\)

Fig. 7.18(b) shows an intuition icon for intransitivity, with a bar across the forbidden jump. A simplified version of this icon (without arrow tips) is used as shown on the right in Fig. 7.18(b). Fig. 7.18(c) signifies that parenthood is both intransitive and asymmetric by combining the constraints in a single icon. The population is changed to satisfy the constraints.

![](img/1344db3eba3d550e6edb009556fcd95c_310_0.png)

FIG. 7.17 The exclusion constraint implies asymmetry and hence irreflexivity.

![](img/1344db3eba3d550e6edb009556fcd95c_310_1.png)

FIG. 7.18 The parenthood relation is asymmetric and intransitive.

![](img/1344db3eba3d550e6edb009556fcd95c_311_0.png)

| a | b |
|---|---|
| b | c |
| a | c |

FIG. 7.19 An irreflexive, functional relation must be intransitive.

As an exercise, prove that intransitivity implies irreflexivity (Hint: x, y, and z need not be distinct). The term “atransitive” is sometimes used instead of “intransitive”. Saying a relation is intransitive is stronger than saying it is not transitive. Antisymmetry, asymmetry, and intransitivity are not intra-row constraints because their enforcement requires comparing the row in question with other existing rows.

If an irreflexive relation includes a functional role (rather than being m:n), it must also be intransitive. Fig. 7.19 illustrates the proof of this by reductio ad absurdum. Let R be an irreflexive relation whose first role is functional (i.e., it has a simple uniqueness constraint). Now, populate R with the first two rows shown. Because R is irreflexive, a≠b and b≠c. Assume that R is not intransitive. This allows us to add the third row shown. Because b≠c, rows 1 and 3 are distinct rows. This means a plays the first role of R twice. But this contradicts the uniqueness constraint. So, row 3 must be rejected (shown by the dotted line through row 3). Hence, the relation must be intransitive. The implied intransitive constraint is usually best left implicit; if shown explicitly it is colored green, as in Fig. 7.19(c). This implication also applies if the second role is functional.

Are we finished with ring constraints? Not quite. Have a look at the parenthood population in Fig. 7.18(c). All the specified constraints are satisfied, but something is still wrong. Can you spot the problem?

Here, Ann is a parent of Bill, who is a parent of Colin who is a parent of Ann. This makes Ann a great grandparent of herself. While reincarnation might make this possible, let’s assume that we wish to exclude this possibility from our UoD. We can do this by declaring the relation to be acyclic. This means the relation has no cycles (i.e., there is no path via the relation from an object back to itself).

![](img/1344db3eba3d550e6edb009556fcd95c_311_1.png)

| Ann | Bill |
|---|---|
| Fred | Bill |
| Ann | Eve |
| Bill | Colin |
| Colin | Dolly |

FIG. 7.20 In an acyclic relation, no loops are allowed.

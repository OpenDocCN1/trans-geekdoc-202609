
The predicate *T* in [Fig. 14.33](#Ch014_681-771_B9780443237904000189.xhtml#f0170) is a logical disjunction, so may be verbalized using the "**or**" to connect verbalizations of the compatible \[sub-\]predicates. In terms of populations, the objectified relation *T* in [Fig. 14.33](#Ch014_681-771_B9780443237904000189.xhtml#f0170) is the *union* of the compatible \[sub-\]relations., that is, *T* = *R\[a,b\]* ∪ *S\[a,b\]*.

Suppose we remove the equality constraint in [Fig. 14.32](#Ch014_681-771_B9780443237904000189.xhtml#f0165)(a). If no other set-comparison constraint exists, we replace the two mandatory role constraints in [Fig. 14.32](#Ch014_681-771_B9780443237904000189.xhtml#f0165)(b) by an inclusive-or constraint: **Each** assessment included **an** assignment **or an** exam mark **or both**. The uniqueness constraints in the flat version correspond to the simple UCs in the nested version (see corollary 1 in [Fig. 14.33](#Ch014_681-771_B9780443237904000189.xhtml#f0170)).

Adding a pair-subset constraint from the first two roles of *S* to the first two roles of *R* is equivalent to adding a subset constraint from the first role of *V* to the first role of *U*. In the context of the disjunctive mandatory constraint, this means that *U* becomes mandatory (see corollary 2). In terms of populations, it also means that the *T* relation becomes *R\[a,b\]* because if one set is a subset of a second, then their union is just the second set. Compare this with the result in [Fig. 14.31](#Ch014_681-771_B9780443237904000189.xhtml#f0160).

A subset constraint in both directions is an equality constraint. So adding an equality constraint between *R\[a,b\]* and *S\[a,b\]* in [Fig. 14.33](#Ch014_681-771_B9780443237904000189.xhtml#f0170) makes both *U* and *V* mandatory in the nested version. [Fig. 14.32](#Ch014_681-771_B9780443237904000189.xhtml#f0165) provides an example.

If an exclusion constraint exists between *R\[a,b\]* and *S\[a,b\]* in [Fig. 14.33](#Ch014_681-771_B9780443237904000189.xhtml#f0170), and we decide to nest, we must add an exclusion constraint between the attached roles in the nested version. For example, suppose that for any given subject, a student can be awarded either an actual grade or a notional grade, but not both (a notional grade might be awarded on the basis of performance in a similar subject from another university). As an exercise, schematize this in both flat and nested versions.

A relation is said to be *partial* if it is a projection of a longer relation; otherwise, it is said to be *whole*. Sometimes, we run into a case where a whole relation must be a subset of another. Consider [Table 14.6](#Ch014_681-771_B9780443237904000189.xhtml#t0035), for instance. Here, "?" is an ordinary null. In this UoD, we want to know what subjects students have passed, but are not interested in their actual ratings.

[Table 14.6](#Ch014_681-771_B9780443237904000189.xhtml#B-t0035)

Student enrollments and passes (if known).

| ![t14-06-9780443237904](images/B9780443237904000189/t14-06-9780443237904.jpg) |

| --- |

[Fig. 14.34](#Ch014_681-771_B9780443237904000189.xhtml#f0175)(a) schematizes this using a flattened approach. We can nest this by objectifying enrollment, and then using a unary to indicate which enrollments resulted in a pass, as in [Fig. 14.34](#Ch014_681-771_B9780443237904000189.xhtml#f0175)(b). By default, the flat version maps to two relational tables while the nested version maps to one. So, the nested version is usually preferred in such a case. You can decide for yourself whether to take an open- or closed-world approach when mapping the unary.

![Fig. 14.34 ORM schemas for Table 14.6: (a) (flat version) and (b) nested version.](images/B9780443237904000189/f14-34-9780443237904.jpg)

[Fig. 14.34](#Ch014_681-771_B9780443237904000189.xhtml#B-f0175) ORM schemas for [Table 14.6](#Ch014_681-771_B9780443237904000189.xhtml#t0035): (a) (flat version) and (b) nested version.

The **overlap algorithm** in [Fig. 14.35](#Ch014_681-771_B9780443237904000189.xhtml#f0180) summarizes the main cases of the N/Fm equivalence. This shows how to nest when two or more fact types include compatible role sequences, each with at least two roles. For simplicity, the diagram shows just two predicates with compatible role pairs (shaded). The predicates may have additional roles.

![Fig. 14.35 Overlap algorithm for nesting when compatible subpredicates exist.](images/B9780443237904000189/f14-35-9780443237904.jpg)

[Fig. 14.35](#Ch014_681-771_B9780443237904000189.xhtml#B-f0180) Overlap algorithm for nesting when compatible subpredicates exist.

Let *P* and *Q* be the compatible \[sub-\]predicates. The nesting action depends on the amount of overlap allowed between the populations of *P* and *Q*. In any given case, this overlap condition is specified by replacing the pair connection marked "?" by a pair-subset (either direction), pair-equality or pair-exclusion constraint, or by no constraint (proper overlap is possible).

In [Fig. 14.35](#Ch014_681-771_B9780443237904000189.xhtml#f0180), a subset constraint upward from *P* to *Q* is denoted "↑", a downward subset constraint is shown as "↓", and an equality constraint appears as "↕". Recall that a predicate is partial if it is embedded in a longer predicate.

The five cases are based on which set-comparison constraint is explicitly *displayed*. An equality constraint must be specified if it exists. Hence, in this context, display of a subset constraint is taken to imply that an equality constraint does not exist. In any situation, exactly one of the five cases listed will apply.

As an example of the "↑" case, consider the transformation from [Fig. 14.29](#Ch014_681-771_B9780443237904000189.xhtml#f0150) to [Fig. 14.30](#Ch014_681-771_B9780443237904000189.xhtml#f0155). Here, *Q* is the whole enrollment predicate while *P* is the partial predicate comprising the first two roles of the fact type Student for Subject scored Rating.

As an example of the "↑" case where *Q* is partial, replace the enrollment predicate in [Fig. 14.29](#Ch014_681-771_B9780443237904000189.xhtml#f0150) by the ternary: Student enrolled in Subject on Date. The nested version in [Fig. 14.30](#Ch014_681-771_B9780443237904000189.xhtml#f0155) must now be modified by adding the mandatory binary: Enrollment occurred on Date. As an example when both *P* and *Q* are whole, consider the transformation of [Fig. 14.34](#Ch014_681-771_B9780443237904000189.xhtml#f0175)(a) to (b).

As an example of the "↕" case, consider reshaping [Fig. 14.32](#Ch014_681-771_B9780443237904000189.xhtml#f0165)(a) to (b). Here, *P* and *Q* are partial, and their conjunction is reworded as "was assessed in". As an example of the "↕" case where neither *P* nor *Q* is partial, remove the mark information from [Fig. 14.32](#Ch014_681-771_B9780443237904000189.xhtml#f0165)(a) to give two binaries: Student did assignment in Subject; Student did exam in Subject. The equality constraint enables these to be replaced by a single binary: Student did assignment and exam in Subject (or Student was assessed in Subject). Derivation rules may be specified for the former binaries if desired.

As an example of the "⊗" case where both *P* and *Q* are partial, recall this exclusive disjunction instance of [Fig. 14.33](#Ch014_681-771_B9780443237904000189.xhtml#f0170): Student for Subject obtained actual Grade; Student for Subject obtained notional Grade. This may be modeled by objectifying Student was assessed in Subject and attaching the mandatory, exclusive disjunction: resulted in actual Grade; resulted in notional Grade.

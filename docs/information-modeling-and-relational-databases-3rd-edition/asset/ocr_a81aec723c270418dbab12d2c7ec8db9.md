example, we might store Drives and derive Owns, or collapse both to IsOwnerDriverOf. However, if a role pair is embedded in a longer predicate, an equality constraint is not equivalent to a derivation rule (why not?). Fig. 6.26 summarizes the case of pair equality for contiguous roles.

Exclusion constraints may be specified between two or more role sequences. As a simple example, suppose we want to record information about cars that people own and cars that they want to buy. Clearly, nobody would want to buy a car that they already own. We can indicate this by the pair-exclusion constraint shown in Fig. 6.27.

This constraint is weaker than an exclusion constraint between just the first roles of these predicates (which would instead say that no car owner wants to buy any car, and hence would disallow Fred’s appearance in both the fact tables shown). Although we must record each person’s gender, both the “owns” and the “wants-to-buy” roles are optional (even disjunctively). For example, Linda neither owns nor wants to buy a car.

![](bbox=[0.14, 0.36, 0.88, 0.495])

![](bbox=[0.14, 0.535, 0.88, 0.81])

In this section, set-comparison constraints have been considered between pairs of role sequences, where each role sequence comes from a single predicate. More generally, set-comparison constraints may be defined between compatible role paths formed by joining different predicates (join constraints are covered in Section 10.1).
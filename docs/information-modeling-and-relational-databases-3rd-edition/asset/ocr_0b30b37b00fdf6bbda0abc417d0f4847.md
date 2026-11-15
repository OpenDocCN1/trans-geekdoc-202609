# 1.1 Flatten any objectified predicate that plays just a single, mandatory role

![](bbox=[0.3, 0.125, 0.71, 0.19])

if another compatible, composite key can be formed by absorbing a low cardinality object type into a predicate with a key of arity 3 then do so

![](bbox=[0.35, 0.225, 0.72, 0.3])

# 1.2 if n nonfunctional, whole predicates form compatible, composite, exclusive keys and are incompatible with all other (sub)-predicates then generalize them to a single longer predicate by extracting an object type of cardinality n

![](bbox=[0.36, 0.36, 0.74, 0.44])

# 1.3 Apply the overlap algorithm to any pattern of compatible, composite keys (see Figure 14.35; sometimes the ⊗ and no-constraint cases are best left as is.)

![](bbox=[0.36, 0.485, 0.49, 0.56])

FIG. 14.42 Optimization step 1: unifying compatible, composite keys.

Step 2 examines object types with both a functional and a nonfunctional role, and typically attempts to replace the latter by functional roles that can be grouped into the same table as the former (see Fig. 14.43).

Most of step 2.1 amounts to predicate specialization using enumerated object types or frequency constraints. Several examples were discussed earlier. The predicate generalization case with a restricted UC is rare (e.g., recall Fig. 14.10).

The first case of step 2.2 for pattern (a) uses PSG3 with its second corollary (see Fig. 14.20). The second case for pattern (a) is extremely rare and was ignored in earlier transformations.

As an example, consider the fact type Official holds Position {'president', 'secretary', 'treasurer'}. We may transform to three unaries: Official is president; Official is secretary; Official is treasurer. Assuming that each position is held by at most one official, we also need to add a role cardinality constraint declaring # ≤ 1 on each unary.

The final stage of step 2.2 (pattern (b)) uses PSG2 and its second corollary. As an example, consider the main and backup driver UoD of Fig. 14.15 and add the functional fact type Car is of CarModel. Specializing the drives predicate enables all the information to be mapped to a single Car table instead of a Driver and a Car table.
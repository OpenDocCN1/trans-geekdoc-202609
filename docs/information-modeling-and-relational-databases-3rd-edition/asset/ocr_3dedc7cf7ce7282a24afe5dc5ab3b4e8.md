in a vice, where vice has two specific cases. If we transform in the opposite direction, we specialize indulging in a vice into two predicates, one for each case.

Predicate specialization and generalization are similar notions to object type specialization and generalization, except that it is rare to specify any subtype connections between predicates (the predicates must be objectified for this).

A predicate may be specialized if a value constraint or a frequency constraint indicates that it has a finite number of cases. Examples with value constraints are more common, so we examine these first. The drinker-smoker example provides one illustration, where Vice has the value constraint {“S”, “D”}. As another example, recall the Olympic Games schema reproduced in Fig. 14.4(a).

There are exactly three kinds of medals, so the ternary may be specialized into three binaries, one for each medal kind, as in Fig. 14.4(b). You may visualize the transformation from schema (a) into schema (b) as absorbing the object type MedalKind into the ternary predicate to divide (or specialize) it into the three binaries. Hence, this transformation is also known as object type absorption.

The reverse transformation from (b) to (a) generalizes the three binaries into the ternary by extracting the object type MedalKind—this may be called object type extraction. In the vices example, a binary is specialized into unaries. With the games example, a ternary is specialized into binaries. In general, when an n-valued object type is absorbed into a predicate, the n specialized predicates that result each have one less role than the original (because the object type has been absorbed).

Although the equivalence is set out diagrammatically to aid understanding, there is a formal mapping of the diagrams to predicate logic where the actual equivalence proofs were made (Halpin, 1989b). In this sense, the results may be called theorems. This general result is set out in Fig. 14.5.

![](bbox=[0.11, 0.59, 0.86, 0.73])

![](bbox=[0.11, 0.76, 0.86, 0.91])
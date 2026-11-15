These different stances with respect to aggregation are somewhat reminiscent of the different modeling positions with respect to nulls. Although more than 20 kinds of null have been distinguished in the literature, the relational model recognizes only one kind of null. Codd's version 2 of the relational model includes two kinds of null, and ORM argues that nulls have no place in base conceptual models (because all its asserted facts are atomic). But let's return to the topic at hand.

Shared aggregation is denoted in UML as a binary association with a hollow diamond at the “whole” or “aggregate” end of the association. Composition (composite aggregation) is depicted with a filled diamond. For example, Fig. 9.43(a) depicts a composition association from Club to Team and a shared aggregation association from Team to Person.

In ORM, which currently has no special notation for aggregation, this situation would be modeled as shown in Fig. 9.43(b). Does Fig. 9.43(a) convey any extra semantics not captured in Fig. 9.43(b)? At the conceptual level, it is doubtful whether there is any additional useful semantics. At the implementation level, however, there is additional semantics. Let’s discuss this in more detail.

The UML specification declares that “both kinds of aggregation define a transitive ... relationship”. The use of “transitive” here is somewhat misleading because it refers to indirect aggregation associations rather than base aggregation associations. For example, if Club is an aggregate of Team, and Team is an aggregate of Person, it follows that Club is an aggregate of Person.

![](bbox=[0.28, 0.495, 0.73, 0.635])

![](bbox=[0.28, 0.68, 0.73, 0.95])
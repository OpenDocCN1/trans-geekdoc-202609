diagrams, an attribute-free approach has advantages for conceptual analysis, including simplicity, stability, and ease of validation. If you are used to modeling in ER or the unified modeling language (UML) (see later), this approach may seem strange at first, but please keep an open mind about it.

ORM allows relationships of any arity (number of roles), so unary (single role) relationships are allowed. Each fact type has at least one predicate reading, corresponding to one way of traversing its roles. Any number of readings may be provided for each role ordering. For a binary association, forward and inverse predicate readings may be shown separated by a slash “/”. As in logic, a predicate is a sentence with object holes in it.

Mixfix notation enables the object terms to be mixed in with the predicate reading at various positions (as required in languages such as Japanese). An object placeholder is indicated by an ellipsis “...” (e.g., the ternary predicate “... at ... is booked for ...”). For unary postfix predicates (e.g., “... smokes”) or binary infix predicates (e.g., “... has ...”), the ellipses may be omitted.

For each fact type, a fact table may be added with a sample population to help validate the constraints. Each column in a fact table is associated with one role. The lines beside the role boxes depict internal uniqueness constraints, indicating which roles or role combinations must have unique entries.

ORM schemas may be represented in diagrammatic or textual form, and some ORM tools can automatically transform between the two representations. Models are validated with domain experts in two main ways: verbalization and population.

For example, the uniqueness constraints on the ternary association verbalize as: For each Room and HourSlot, that Room at that HourSlot is booked for at most one Activity; For each HourSlot and Activity, at most one Room at that HourSlot is booked for that Activity.

The ternary fact table has a satisfying population (each Room-HourSlot combination and each HourSlot-Activity combination is unique). The uniqueness constraints on the binary verbalize as: Each Activity has at most one ActivityName; Each ActivityName refers to at most one Activity. The 1:1 nature of this association is illustrated by the population, where each column entry occurs only once in its column.

The solid dot on Activity is a mandatory role constraint, indicating that each instance in the population of Activity must play that role. This verbalizes as Each Activity has some ActivityName. A role that is not mandatory is optional. Because sample data are not always significant, additional data (such as STM in the binary fact type) may be needed to illustrate some rules. The optionality of the other role played by Activity is shown by the absence of STM in its population.

Because ORM schemas can be specified in unambiguous sentences backed up by illustrative examples, it is not necessary for domain experts to understand the diagram notation at all. Modelers, however, find diagrams very useful for thinking about the UoD.

To double check a constraint, a counterexample to that constraint may be presented. The counter-rows appended to the fact tables test the uniqueness constraints. For instance, the first row and counter-row of the ternary indicate that room 20 at 9 a.m.
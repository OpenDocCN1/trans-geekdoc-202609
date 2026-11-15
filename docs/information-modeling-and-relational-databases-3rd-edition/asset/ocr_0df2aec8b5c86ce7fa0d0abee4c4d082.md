![](bbox=[0.13, 0.1, 0.83, 0.34])

FIG. 8.1 The original ER notation used by Chen.

![](bbox=[0.29, 0.41, 0.68, 0.45])

FIG. 8.2 An ambiguous ER schema.

Roles may be annotated with a maximum cardinality of 1 or many. For example, read left to right, the Proj-Mgr relation is one-to-many (each employee manages zero or more projects, and each project is managed by at most one employee).

As shown in Fig. 8.1, Chen used noun phrases for relationships, eliminating natural verbalization. Even if verb phrases are used, the direction in which relationship names are to be read is formally undecided, unless we add additional marks (e.g., arrows) or rules (e.g., always read from left to right and from top to bottom). For example, does the employee manage the project or does the project manage the employee? Although we can use our background knowledge to informally disambiguate this example, it is easy to find examples of relationships whose direction can only be guessed at by anybody other than the model's creator.

This problem is exacerbated if the verb phrase used to name the relationship is shortened to one word (e.g., "work"), unfortunately still a fairly common practice. As a simple example, is the ER diagram in Fig. 8.2 meant to capture the fact type Person killed Animal, or Animal killed Person? We could disambiguate this diagram by adding role names (e.g., "victim", "killer") but there is no requirement to do so.

Similarly, if we populate the Component relationship in Fig. 8.1 with the pair (a, b), we don't know whether this means a is a component of b, or vice versa. To disambiguate this, we need to add role names (e.g., "subpart", "superpart") or use a verb phrase (e.g., "is a component of") with a defined direction.

A rectangle with a double border denotes a weak entity type. This means that the entity type's identification scheme includes a relationship to another entity type. In Fig. 8.3(a), for example, an instance of Dependant might be identified by having the name "Eve Jones"
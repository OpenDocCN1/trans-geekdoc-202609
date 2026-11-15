# Step

+   1a. Verbalize familiar information examples as facts.
+   1b. Refine these into formal, elementary facts, and apply quality checks.
+   2. Draw the fact types, and apply a population check.
+   3. Check for entity types that should be combined, and note any arithmetic derivations.

Step 1 is the most important. This is seeded by data use cases, which are relevant information examples (e.g., tables, forms, diagrams) that are familiar to the domain expert. These are verbalized in terms of elementary facts. The domain expert verbalizes the examples informally as facts in natural language sentences (step 1a).

The modeler completes step 1 by refining these into elementary facts (step 1b). An elementary fact is a simple assertion that an object has some property or that one or more objects participate together in some relationship. With respect to the UoD, an elementary fact cannot be split into smaller facts without information loss.

Elementary facts are expressed as instantiated logical predicates. A logical predicate is a declarative sentence with object holes in it. To complete the sentence, the placeholders are filled in by object terms. With simple reference schemes, an entity term is a definite description that includes the name of the entity type, reference mode, and value (e.g., "the Scientist with surname 'Einstein'"). A value term includes the name of the value type and a literal value (e.g., "the Surname 'Einstein'").

Each object hole corresponds to a role (part in a relationship). A predicate with one role is unary, with two roles is binary, with three roles is ternary, with four roles is quaternary, and with n roles is n-ary. The value n is the arity of the predicate.

In CSDP step 2, we draw the fact types and apply a population check. Fig. 3.32 summarizes the graphic notations met so far. Object types are depicted as named, soft rectangles (solid lines for entity types and dashed lines for value types). An n-ary predicate is shown as a named, contiguous sequence of n role-boxes. Predicates are ordered. The predicate reading is placed next to the predicate shape. Each role is played by exactly one object type, as shown by a connecting line.

A simple 1:1 reference scheme involves a reference predicate between an entity type and a value type, where each entity is associated with exactly one value, and each value is associated with only one entity. This kind of scheme may be abbreviated by enclosing the reference mode in parentheses next to the entity type name.

Popular reference modes are preceded by a dot, such as Country (.Code). Unit-based reference modes are appended by a colon, such as Height (cm:), possibly followed by the unit's dimension, such as (cm: Length). General reference modes may share their value types with other entity types, such as (URL).

Once a fact type is drawn, it should be checked by populating it with at least one fact and reading it back in natural language. Each column in the associated fact table corresponds to a specific role. To talk about an object corresponding to a relationship, an objectified association is formed from the fact type. This nominalization process is also known as nesting.
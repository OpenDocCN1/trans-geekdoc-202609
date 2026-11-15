
## Step

- 1a. Verbalize familiar information examples as facts.
- 1b. Refine these into formal, elementary facts, and apply quality checks.
- 2. Draw the fact types, and apply a population check.
- 3. Check for entity types that should be combined, and note any arithmetic derivations.

Step 1 is the most important. This is seeded by data use cases, which are relevant information examples (e.g., tables, forms, diagrams) that are familiar to the domain expert. These are verbalized in terms of elementary facts. The domain expert verbalizes the examples informally as facts in natural language sentences (step 1a).

The modeler completes step 1 by refining these into elementary facts (step 1b). An elementary fact is a simple assertion that an object has some property or that one or more objects participate together in some relationship. With respect to the UoD, an elementary fact cannot be split into smaller facts without information loss.

Elementary facts are expressed as instantiated logical predicates. A logical predicate is a declarative sentence with object holes in it. To complete the sentence, the placeholders are filled in by object terms. With simple reference schemes, an entity term is a definite description that includes the name of the entity type, reference mode, and value (e.g., "the Scientist with surname 'Einstein'"). A value term includes the name of the value type and a literal value (e.g., "the Surname 'Einstein'").

Each object hole corresponds to a role (part in a relationship). A predicate with one role is unary, with two roles is binary, with three roles is ternary, with four roles is quaternary, and with n roles is n-ary. The value n is the arity of the predicate.

In CSDP step 2, we draw the fact types and apply a population check. Fig. 3.32 summarizes the graphic notations met so far. Object types are depicted as named, soft rectangles (solid lines for entity types and dashed lines for value types). An n-ary predicate is shown as a named, contiguous sequence of n role-boxes. Predicates are ordered. The predicate reading is placed next to the predicate shape. Each role is played by exactly one object type, as shown by a connecting line.

A simple 1:1 reference scheme involves a reference predicate between an entity type and a value type, where each entity is associated with exactly one value, and each value is associated with only one entity. This kind of scheme may be abbreviated by enclosing the reference mode in parentheses next to the entity type name.

Popular reference modes are preceded by a dot, such as Country (.Code). Unit-based reference modes are appended by a colon, such as Height (cm:), possibly followed by the unit's dimension, such as (cm: Length). General reference modes may share their value types with other entity types, such as (URL).

Once a fact type is drawn, it should be checked by populating it with at least one fact and reading it back in natural language. Each column in the associated fact table corresponds to a specific role. To talk about an object corresponding to a relationship, an objectified association is formed from the fact type. This nominalization process is also known as nesting.

In step 3 of the CSDP, we check for entity types that should be combined and note any arithmetic derivations. For any given UoD, each entity belongs to exactly one of the primitive entity types that have been selected (e.g., Person, Car). Hence, if we have drawn two entity types that may have a common instance, we should normally combine them.

![](img/1344db3eba3d550e6edb009556fcd95c_132_0.png)

FIG. 3.32 Some basic symbols used in conceptual schema diagrams.

Even if they don't overlap, entity types that can be meaningfully compared (e.g., to compute ratios) may often be combined. If unit-based, either collapse the entity types into one or ensure that their units have the same unit dimension.

If the same kind of information is to be recorded for different entity types, these should often be combined, and if needed a fact type should be added to preserve the original distinction.

If a fact type is arithmetically derivable from others, an appropriate derivation rule should be declared in relational style (using predicates) or in attribute style (using attributes derived from role names). The derived fact type may be omitted from the diagram, but if included its derivation status should be marked “*” (simply derived) or “+” (semi-derived). If derived facts are also stored, append a final asterisk.

## Chapter Notes

Bentley (1998) suggests the following alternative yardsticks for language design: orthogonality, generality, parsimony, completeness, similarity, extensibility, and openness. Some of these criteria (e.g., completeness, generality, extensibility) may be subsumed under expressibility. Parsimony may be treated as one aspect of simplicity. Another criterion sometimes mentioned is convenience (how convenient, suitable, or appropriate a language feature is to the user). We treat convenience as another aspect of simplicity.

The parsimony-convenience trade-off is nicely illustrated by two-valued propositional calculus, which allows for 4 monadic and 16 dyadic logical operators. All 20 of these operators can be expressed in terms of “a single logical operator (e.g. nand)”, but while this might be useful in building electronic components, it is too inconvenient for direct human communication. For example, “not p” is far more convenient than “p nand p”. In practice, we use several operators (e.g., not, and, or, if-then) because their convenience far outweighs the parsimonious benefits of having to learn only one operator such as nand.

When it comes to proving metatheorems about a given logic, it is often convenient to adopt a somewhat parsimonious stance regarding the base constructs (e.g., treat “not” and “or” as the only primitive logical operators while introducing other constructs as derived (e.g., define “if p then q” as “not p or q”). Similar considerations apply to modeling languages.

A classic paper on linguistics that influenced the early development of a number of modeling methods is Fillmore (1968). Use case specification was central to the former Objectory approach of Ivar Jacobson, one of the main contributors to UML. For an overview of logicians’ approaches to proper names and descriptions, see Chapter 5 of Haack (1978). Some heuristics to help with step 1 in interpreting common forms used in business are discussed in Choobineh et al. (1992).

Although ordered, mixfix predicates are preferred for naturalness; you could also treat a fact as a named set of (object, role) pairs: F(o1,r1), ..., (on,rn)). Here, each object oi is paired with the role ri that it plays in the fact F. For example, the fact that Wirth designed Pascal might be specified as Design{ (The Person with surname “Wirth”, agentive), (The Language named “Pascal”, objective) }. Instead of the case-adjectives “agentive” and “objective”, other role names could be used (e.g., “designer” and “language”, or “designing” and “being designed by”). By pairing objects with their roles, the order in which the pairs are listed is irrelevant. This approach is used in reference and idea language (RIDL) (Meersman, 1982).

In this book, the term “line” is used informally to mean “line segment” or “edge” (in geometry, lines have no beginning or end). The following notes provide a brief history of ORM.

In the 1970s, especially in Europe, substantial research was carried out to provide high-level semantics for modeling information systems. Abrial (1974), Senko (1975), and others modeled binary relationships. In 1973, Eckhard Falkenberg generalized their work to n-ary relationships and decided that attributes should not be used at the conceptual level because they involved “fuzzy” distinctions and they also complicated schema evolution. Later, Falkenberg (1976) proposed the fundamental ORM framework, which he called the “object-role model”. This framework allowed n-ary and nested relationships, but depicted roles with arrows lines.

Nijssen (1976) adapted this framework by introducing the circle-box notation for objects and roles and adding a linguistic orientation and design procedure to provide a modeling method called ENALIM (Evolving Natural Language Information Model) (Nijssen, 1977). A major reason for the role-box notation was to facilitate validation using sample populations. Nijssen led a group of researchers at Control Data in Belgium who developed the method further, including Franz van Assche, who classified object types into lexical object types (LOTs) and nonlexical object types (NOLOTs). Today, LOTs are often called “value types” and NOLOTs are called “entity types”. Kent (1977) provided several semantic insights and clarified many conceptual issues.

Robert Meersman added subtypes and made major contributions to the RIDL query language with Falkenberg and Nijssen. The method was renamed “an Information Analysis Method” (NIAM) and was summarized in a paper by Verheijen and van Bekkum (1982). In later years, the acronym “NIAM” was given different expansions, and is now known as the “natural language information analysis method”. Two matrix methods for subtypes were developed: one (the role-role matrix) by Dirk Vermeir (1983) and another by Falkenberg and others.

In the 1980s, Falkenberg and Nijssen worked jointly on the design procedure and moved to the University of Queensland, where the method was enhanced further. It was there that Terry Halpin

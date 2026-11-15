The following report extract indicates electrical energy consumption (in kilowatt hours) by consumers on a quarterly basis. Some consumers (e.g., recent ones) might not yet appear in the report. Although consumption can be derived from other data not shown here, assume that it is simply stored for this exercise.

| Consumer | Year | QtrNr | Consumption (kW.h) |
|---|---|---|---|
| 3001 | 2006 | 4 | 1622 |
| | 2007 | 1 | 1500 |
| | 2007 | 2 | 2001 |
| ... | ... | ... | ... |
| 5678 | 2007 | 2 | 2001 |
| ... | ... | ... | ... |

+   (a) Specify a UML schema for this UoD, including constraints and derivation rules.
+   (b) Suppose that in the model, Fault is an association class to objectify the association Consumer reported FaultType at Instant. Suggest a new identification scheme for Fault to improve the usability of the model.

2. Model the academic schema in Exercise 8.5, Question 2 in UML.

# 9.9 Summary

UML has been adopted by the OMG as a method for object-oriented analysis and design. Although UML is mainly focused on the design of object-oriented programming code, it can be used for modeling database applications by supplementing its predefined notations with user-defined constraints.

UML has 13 main diagram types: six for structure (class, object, component, deployment, package, and composite structure), and seven for behavior (use case, state machine, activity, sequence, collaboration, interaction overview, and timing). Class diagrams are essentially an extended form of ER diagrams.

The basic correspondence between data structures and instances in UML and ORM is summarized in Table 9.5. Classes are basically entity types and are depicted as named rectangles, with compartments for attributes and operations, etc. In UML, facts are stored either in attributes of classes or in associations among two or more classes.

Binary associations are depicted as lines. Ternary and longer associations include a diamond. Role names may be placed at association ends, and an association may be given a name.

An association may be objectified as an association class, corresponding to nesting in ORM. Associations may be qualified to provide a weak form of co-reference.

Attributes and association ends may be annotated with multiplicity constraints to indicate both optionality and cardinality (e.g., 0..1 = at most one, 1 = exactly one, * = zero or more, 1..* = one or more). Attributes have a default multiplicity of 1, and association ends
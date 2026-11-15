
A solid half-line denotes a mandatory role, and a dotted half-line indicates an optional role. For cardinality, a crow’s foot intuitively indicates “many” by its many “toes”. The absence of a crow’s foot intuitively indicates “one”. The crow’s foot notation was invented by Dr. Gordon Everest, an ORM advocate, who originally used the term “inverted arrow” (Everest, 1976) but now calls it a “fork”. Fig. 8.5 shows the basic correspondence with the ORM notation for simple mandatory and uniqueness constraints.

![](img/1344db3eba3d550e6edb009556fcd95c_337_0.png)

To enable the optionality and cardinality settings to be verbalized, Barker (1990a, pp. 3–5) recommends the following _naming discipline for relationships_. Let _A R B_ denote an infix relationship _R_ from entity type _A_ to entity type _B_. Name _R_ in such a way that each of the following four patterns results in an English sentence:

> **Each A (must | may) be R (one and only one B | one or more _B-plural-form_)**

Use “must” or “may” when the first role is mandatory or optional, respectively. Use “one and only one” or “one or more” when the cardinality on the second role is one or many, respectively. For example, the optionality/cardinality settings in Fig. 8.5(a) verbalize as **Each Employee must be an occupier of one and only one Room; Each Room may be occupied by one or more Employees.**

The constraints on the left-hand role in the ORM model in Fig. 8.5(b) verbalize as **Each Employee occupies some Room; Each Employee occupies at most one Room.** These constraints combined verbalize as **Each Employee occupies exactly one Room.** The lack of a uniqueness constraint on the right-hand role is verbalized as **It is possible that the same Room is occupied by more than one Employee**, or (if no inverse reading exists) as **It is possible that more than one Employee occupies the same Room.**

Regarding the lack of an explicit mandatory role constraint on the right-hand role, we don’t want that verbalized explicitly because it may well be unstable. If Room plays no other fact roles, the role is mandatory by implication (Room is not declared independent), so verbalization may well confuse here. If Room does play another fact role, and we decide that some rooms may be unoccupied, we could declare this explicitly either as **It is possible that some Room is occupied by no Employee** or as **It is not necessary that each Room is occupied by some Employee.** If no inverse reading is available, it may be verbalized thus: **It is possible that no Employee occupies some Room.**

To its credit, the Barker verbalization convention is good for basic mandatory and uniqueness constraints on infix binaries. But it is far less general than ORM’s approach, which applies to instances as well as types, for predicates of any arity, infix or mixfix, and covers many more kinds of constraint, with no need for pluralization. As a trivial example, the fact instance “Employee ‘101’ an occupier of Room 23” is not proper English, but “Employee ‘101’ occupies Room 23” is good English.

If each role in a binary association is assigned one of optional/mandatory and one of many/one, there are 16 patterns. The equivalent Barker ER and ORM diagrams for these cases are shown in Fig. 8.6. The last case where both roles of a many:many relationship are mandatory is considered illegal in Barker ER.

| Constraint | Barker ER | ORM |
| :--- | :--- | :--- |
| n:1 both roles optional | A -> .... -> B | A - - - B |
| 1:n both roles optional | A .... <- B | A - - - B |
| 1:1 both roles optional | A .... B | A = = B |
| m:n both roles optional | A -> .... <- B | A = = B |
| n:1 first role mandatory | A -> .... -> B | A . - - - B |
| 1:n first role mandatory | A --- -> B | A . - - - B |
| 1:1 first role mandatory | A .... B | A . = = B |
| m:n first role mandatory | A -> .... <- B | A . = = B |
| n:1 second role mandatory | A -> .... -> B | A - - - . B |
| 1:n second role mandatory | A .... -> B | A - - - . B |
| 1:1 second role mandatory | A .... B | A = = . B |
| m:n second role mandatory | A -> .... <- B | A = = . B |
| n:1 both roles mandatory | A -> --- -> B | A . - - - . B |
| 1:n both roles mandatory | A --- -> B | A . - - - . B |
| 1:1 both roles mandatory | A --- B | A . = = . B |
| m:n both roles mandatory | A -> --- <- B | A . = = . B |

FIG. 8.6 Equivalent constraint patterns.

Ring associations considered illegal by Barker are shown in Fig. 8.7(a). Although rare, they sometimes occur in reality, so should be allowed at the conceptual level, as permitted in ORM.

As an exercise, you may wish to invent satisfying populations for the ORM associations in Fig. 8.7(b). Although considered illegal by Barker, at least some of these patterns are allowed in Oracle's CASE tools.

![](img/1344db3eba3d550e6edb009556fcd95c_339_0.png)

In the Barker notation, a bar "|" across one end of a relationship indicates that the relationship is a component of the primary identifier for the entity type at that end. For example, in Fig. 8.8, Employee and Building have simple identifiers, but Room is compositely identified by combining its room number and building.

![](img/1344db3eba3d550e6edb009556fcd95c_339_1.png)

The use of identification bars provides some of the functionality afforded by external uniqueness constraints in ORM. For example, the schemas in Fig. 8.9 are equivalent. Any other attributes of Room and Building would be modeled in ORM as relationships. ORM's external uniqueness notation seems to us to convey more intuitively the idea that each RoomNr, Building combination is unique (i.e., refers to at most one room). But maybe we're biased. At any rate, this constraint (as well as any other graphic constraint) can be automatically verbalized in natural language.

![](img/1344db3eba3d550e6edb009556fcd95c_339_2.png)

![](img/1344db3eba3d550e6edb009556fcd95c_340_0.png)

FIG. 8.10 A room schedule model in Barker notation.

Some people misread the bar notation for composite identification as a “1” because this is what the symbol means in many other ER notations. But the main problem with the bar and “#” notations is that they cannot be used to declare uniqueness constraints (see later). A second problem, arising from the practice of modeling some fact types as attributes and others as relationships, is that two very different notations are used for the same fundamental concept (uniqueness).

Section 1.2 used a room scheduling example to illustrate several fundamental differences between ORM and modeling approaches such as ER and UML. You may recall that the schema shown in Fig. 8.10 was used to model the example in the Barker notation. If you skipped Section 1.2, you may wish to read it now because it discussed this example in a lot of detail. The use of attributes and the binary-only relationship restriction in this model make it hard to verbalize and populate the schema for validation purposes. Moreover, there is at least one constraint missing.

A populated ORM schema for this example is reproduced in Fig. 8.11 (minus the counterexample rows discussed in Section 1.2). Here, the facts are naturally verbalized as a ternary and a binary, and the constraints are easily checked using verbalization and sample data. With the ER model, there is no way of specifying the right-hand uniqueness constraints on either fact type because the Barker notation doesn’t capture uniqueness constraints on attributes or relationships unless they are used for primary identification.

![](img/1344db3eba3d550e6edb009556fcd95c_340_1.png)

| 20 | Mon 9 a.m. | ORC |
|---|---|---|
| 20 | Tue 2 p.m. | ORC |
| 33 | Mon 9 a.m. | XQC |
| 33 | Fri 5 p.m. | STP |

| ORC | ORM class |
|---|---|
| STM | Staff Meeting |
| STP | Staff Party |
| XQC | XQuery class |

FIG. 8.11 A populated ORM model for room scheduling.

![](img/1344db3eba3d550e6edb009556fcd95c_341_0.png)

In case it looks like we’re just bashing attribute-based approaches such as ER, let us reiterate that we find attribute-based models useful for compact overviews and for getting closer to the implementation model. However, we generate these by mapping from ORM, which we use exclusively for the initial conceptual analysis. This makes it easier to get the model right in the first place and to modify it as the underlying domain evolves.

Unlike ER (and UML for that matter), ORM was built from a linguistic basis, and its graphic notation was carefully chosen to exploit the potential of sample populations. To reap the benefits of verbalization and population for communication with and validation by domain experts, it’s better to use a language that was designed with this in mind.

An added benefit of ORM is that its graphic notation can capture many more business rules than popular ER notations. Although not as rich as ORM, the Barker notation is more expressive than many ER notations. The rest of this section discusses its support for advanced constraints and subtyping.

In Barker notation, an exclusion constraint over two or more roles is shown as an “exclusive arc” connected to the roles with a small dot or circle. For example, Fig. 8.12(a) includes the constraint that no employee may be allocated both a bus pass and a parking bay. In ORM, this constraint is depicted by connecting “⊗” to the relevant roles by a dotted line, as shown in Fig. 8.12(b).

To declare that two or more roles are mutually exclusive and disjunctively mandatory, the Barker notation uses the exclusive arc, but each role is shown as mandatory (solid line). For example, in Fig. 8.13(a) each account is owned by a person or a company, but not both.

![](img/1344db3eba3d550e6edb009556fcd95c_341_1.png)

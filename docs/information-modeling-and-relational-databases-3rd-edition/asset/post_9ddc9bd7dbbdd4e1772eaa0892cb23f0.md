
![](img/1344db3eba3d550e6edb009556fcd95c_383_0.png)

### FIG. 9.10 Binary associations in (a) UML and (b) ORM.

![](img/1344db3eba3d550e6edb009556fcd95c_383_1.png)

### FIG. 9.11 A ternary association in (a) UML and (b) ORM.

Ternary and higher arity associations in UML are depicted as a diamond connected by lines to the classes, as shown in Fig. 9.11(a). Because many lines are used with no reading direction indicator, directional verbalization is ruled out, so the diagram can’t be used to communicate in terms of sentences. This nonlinear layout also often makes it impractical to conveniently populate associations with multiple instances, unless we use role names for column names. Add to this the impracticality of displaying multiple populations of attributes, and it is clear that class diagrams are of little use for population checks.

UML does provide object diagrams for instantiation, but these are convenient only for populating associations with a single instance. Adding multiple instances leads to a mess (e.g., Blaha and Premerlani, 1998, p. 31). Hence, as noted in the UML Notation Guide, “the use of object diagrams is fairly limited”.

The previous section discussed how UML depicts multiplicity constraints on attributes. A similar notation is used for associations, where the relevant multiplicities are written next to the relevant roles. Fig. 9.12(a) adds the relevant multiplicity constraints to Fig. 9.10(a). A “*” abbreviates “0..*”, meaning “zero or more”, “1” abbreviates “1..1”, meaning “exactly one”, and “0..1” means “at most one”. If no multiplicity is supplied for an association role, “*” is assumed by default (unlike attributes, where 1 is the default multiplicity).

![](img/1344db3eba3d550e6edb009556fcd95c_384_0.png)

### FIG. 9.12 UML multiplicity constraints (a) and equivalent ORM constraints (b).

UML places each multiplicity constraint on the “far role”, in the direction in which the association is read. Hence, the constraints in this example mean that each company employs zero or more employees, each employee is employed by exactly one company, each company acquired zero or more companies, and each company was acquired by at most one company.

The corresponding ORM constraints are depicted in Fig. 9.12(b). Recall that multiplicity covers both cardinality (frequency) and optionality. Here, the mandatory role constraint indicates that each employee works for at least one company, and the uniqueness constraints indicate that each employee works for at most one company, and each company was acquired by at most one company.

For comparison purposes, Fig. 9.13 depicts the n:1 association Moon orbits Planet in various notations. The instance diagram in Fig. 9.13(a) includes a sample population of moons (p = Phobos, d = Deimos, c = Callisto) and planets (v = Venus, m = Mars, j = Jupiter). For illustration purposes, the ORM diagram in Fig. 9.13(e) also includes sample object and fact types. The population is significant with respect to multiplicity constraints. Each planet orbits exactly one moon, and the same planet may be orbited by zero or more moons.

The UML (Fig. 9.13(b)) and information engineering (Fig. 9.13(c)) approaches are similar because both express the constraints in terms of multiplicities/cardinalities. In contrast, Barker ER (Fig. 9.13(d)) and ORM (Fig. 9.13(e)) capture some constraints in terms of mandatory/optional roles and other constraints in terms of cardinality/uniqueness constraints. As shown later, the failure of UML to separate out these two kinds of constraint prevents it from graphically capturing various cases it might otherwise have handled.

For binary associations, there are four possible uniqueness constraint patterns (n:1; 1:n; 1:1; m:n) and four possible mandatory role patterns (only the left role mandatory, only the right role mandatory, both roles mandatory, both roles optional). Hence, if we restrict ourselves to a maximum frequency of one, there are 16 possible multiplicity combinations for binary associations. The 16 cases are shown in Fig. 9.14, in both UML and ORM.

![](img/1344db3eba3d550e6edb009556fcd95c_385_0.png)

UML allows multiplicity constraints with whole numbers other than zero or one, and also supports multiplicity lists or ranges (e.g., “1..7, 10”). For such cases, ORM uses frequency constraints instead of uniqueness constraints. ORM is more expressive in this regard because it can apply such constraints to arbitrary collections of roles, not just single roles.

For an elementary n-ary association, each internal uniqueness constraint in ORM must span at least n – 1 roles. In UML, a multiplicity constraint on a role of an n-ary association effectively constrains the population of the other roles combined. For example, Fig. 9.15(a) is a UML diagram for a ternary association in which both Room–HourSlot and HourSlot–Activity pairs are unique. For simplicity, reference schemes are omitted.

An ORM depiction of the same association is shown in Fig. 9.15(b). The left-hand uniqueness constraint indicates that Room–HourSlot is unique (i.e., for any given room and hour slot, at most one activity is booked). The right-hand uniqueness constraint indicates that HourSlot–Activity is unique (i.e., for any given hour slot and activity, at most one room is booked). An extended version of this example was discussed in Section 1.2, where the ORM diagram better facilitated constraint checking by verbalization and population.

As it covers some n-ary cases like this, UML’s multiplicity constraint notation is richer than the optionality/cardinality notation of typical ER. However, there are many cases with n-ary associations where the multiplicity notation of UML can’t capture even a simple mandatory role constraint, or a minimum frequency constraint above 1. In contrast, the mandatory, uniqueness, and frequency constraint notations of ORM can capture any possible constraint of this nature, on roles or role sequences, on predicates of any arity. So ORM is far richer in this regard.

For example, suppose we modify our room booking example to indicate that all activities have a room-hourslot booking and also have unique names as well as their identifying codes. The modified example, including reference schemes, is shown in Fig. 9.16 in both UML and ORM. Because UML bundles both mandatory and uniqueness into a single notion of multiplicity, it cannot capture the constraint that each activity has a booking graphically. The best we can do is add a note, as shown in Fig. 9.16(a). This constraint may be expressed graphically in ORM using a mandatory role constraint, as shown in Fig. 9.16(b).

### FIG. 9.14 Equivalent constraint patterns in UML and ORM.

| Condition | UML | ORM |
| :--- | :--- | :--- |
| n:1 both roles optional | A *---0..1 B | A --- B |
| 1:n both roles optional | A 0..1---* B | A --- B |
| 1:1 both roles optional | A 0..1---0..1 B | A --- B |
| m:n both roles optional | A *---* B | A --- B |
| n:1 first role mandatory | A *---1 B | A .-- B |
| 1:n first role mandatory | A 0..1---1..* B | A .-- B |
| 1:1 first role mandatory | A 0..1---1 B | A .-- B |
| m:n first role mandatory | A *---1..* B | A .-- B |
| n:1 second role mandatory | A 1..*---0..1 B | A ---.-- B |
| 1:n second role mandatory | A 1---* B | A ---.-- B |
| 1:1 second role mandatory | A 1---0..1 B | A ---.-- B |
| m:n second role mandatory | A 1..*---* B | A ---.-- B |
| n:1 both roles mandatory | A 1..*---1 B | A .--.-- B |
| 1:n both roles mandatory | A 1---1..* B | A .--.-- B |
| 1:1 both roles mandatory | A 1---1 B | A .--.-- B |
| m:n both roles mandatory | A 1..*---1..* B | A .--.-- B |

![](img/1344db3eba3d550e6edb009556fcd95c_387_0.png)

### FIG. 9.15 Constraints on a ternary in (a) UML and (b) ORM.

![](img/1344db3eba3d550e6edb009556fcd95c_387_1.png)

### FIG. 9.16 (a) UML resorts to a note to capture (b) a mandatory constraint in ORM.

This deficiency in UML is a direct consequence of choosing to attach minimum multiplicity to a role other than the immediate role. For the same reason, UML multiplicity constraints are also unable to capture various ORM frequency constraints. In general, given any n-ary (n > 2) association, if an ORM mandatory or frequency constraint applies to at least 1 and at most n − 2 roles, this cannot be captured by a UML multiplicity constraint. Some examples of such cases are shown in Fig. 9.17. Further discussion on such cases may be found in Halpin (2001).

Unlike many ER versions, both UML and ORM allow associations to be objectified as first class object types, called association classes in UML and objectified associations or nested object types in ORM. UML requires the same name to be used for the original association and the association class, impeding natural verbalization of at least one of these constructs. In contrast, ORM nesting is based on linguistic nominalization (a verb phrase is objectified by a noun phrase), thus allowing both to be verbalized naturally, with different readings for each.

Although UML identifies an association class with its underlying association, it displays them separately, connected by a dashed line (see Fig. 9.18a). Each person may write many papers, and each paper is written by at least one person. Because authorship is m:n, the association class Writing has a primary reference scheme based on the combination of person and paper (e.g., the writing by person “Norma Jones” of paper 33). The optional period attribute stores how long that person took to write that paper.

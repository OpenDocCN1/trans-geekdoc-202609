
UML assumes that each object is identified by an internal surrogate. If desired, we could add a measurement number identifier for WeightMeasurement for Barker ER and UML. If the combination of date and patient still provides a secondary identifier for WeightMeasurement, the Barker ER identifier notation used in Fig. 10.22(a) to capture this constraint can no longer be used because it applies only to primary identifiers; so, this constraint should be noted elsewhere.

![](img/1344db3eba3d550e6edb009556fcd95c_447_0.png)

FIG. 10.22 Fig. 10.21 (c) remodeled in (a) Barker ER and (b) UML.

The UML schema in Fig. 10.22(c) adds a measurement number identifier for WeightMeasurement. The {id} marker for the WeightMeasurement.nr attribute prevents the use of the two {id} markers used in Fig. 10.22(b) to capture the composite uniqueness constraint, so this constraint is now captured textually in a note.

To maintain a history of patient temperatures, we might choose a different temporal granularity. For example, if our granularity is 1 h, we could use the fact type Patient at Hour had Temperature.

While the above approaches allow full history (at the desired granularity), they do not demand full history. For example, we are not constrained to record a patient’s weight on a daily basis or a patient’s temperature on an hourly basis.

For comparison purposes, we sometimes require a well-defined *partial history* (e.g., current and previous values only). The basics for such a situation can be modeled easily by using multiple fact types, as shown for patient weights in Fig. 10.23. A complete approach requires additional textual rules to assign the old current weight to the new previous weight on update.

![](img/1344db3eba3d550e6edb009556fcd95c_447_1.png)

FIG. 10.23 Modeling consecutive weights in (a) ORM, (b) UML, and (c) Barker ER.

Maintaining a history of nonfunctional fact types is a little more complicated because they may be changeable both collectively and individually. Consider, for example, the report extract of country visits shown in Table 10.2.

Table 10.2 Extract from a record of visits to countries by employees.

| EmpNr | CountryCode | startdate | enddate |
| :--- | :--- | :--- | :--- |
| 1001 | US | 2022-01-01 | 2022-01-15 |
| 1001 | NL | 2023-07-11 | ? |
| 1002 | NL | 2022-01-30 | 2022-02-13 |
| 1002 | NL | 2023-06-05 | 2023-06-05 |
| 1002 | BE | 2023-06-20 | ? |

In this UoD, an employee may visit many countries, and a country may be visited by many employees. An employee may visit more than one country on the same date (e.g., The Netherlands and Belgium), but no employee may visit the same country more than once on the same date. For each visit, the start date is known but the end date might be unknown (e.g., the visit might still be in progress).

Fig. 10.24 shows some poor attempts to model such visits. Fig. 10.24(a) models Visit as an objectified association in ORM, and Fig. 10.24(b) takes a similar approach in UML, modeling Visit as an association class. Fig. 10.24(c) models Visit as an entity type in the Barker ER notation. All these schemas have problems. You might like to identify the main problem before reading on.

In Fig. 10.24(a), the fact type Employee visited Country is nonfunctional (in this case m:n) and repeatable. For example, the fact instance Employee “1002” visited Country “NL” is repeated, appearing on two rows. But the uniqueness constraint spanning the roles of the fact type Employee visited Country requires that such a fact instance appears at most once in any population of the fact type.

![](img/1344db3eba3d550e6edb009556fcd95c_448_0.png)

In other words, the schema in Fig. 10.24(a) has no way to record multiple visits to the same country by the same employee. The same is true of all the other variations in Fig. 10.24—they assume that a visit may be identified simply by combining the visitor with the country visited. The schemas also lose the constraint that if a visit’s end date is known, it must be on or after the start date. How do we record a full history of country visits? Try answering this before reading on.

There are at least three ways to resolve this problem. One approach is to include a distinguishing temporal role as part of the identifier. Given that each employee starts to visit any given country at most once on any given date, we may identify a visit by combining the visitor, the country visited, and the start date of the visit.

Fig. 10.25(a) and (b) shows two ORM schemas using this approach. Visit is an independent entity type, as its only role outside its preferred reference scheme is optional. The external uniqueness constraint involving the end date role indicates that when an end date exists, each combination of visitor, country visited, and end date applies to at most one visit. The value-comparison constraint ensures that if a visit’s end date is known, it is on or after the start date.

UML and Barker ER versions of this approach are shown in Fig. 10.25(c) and (d). Neither has a graphic notation for the value comparison constraint nor for the external uniqueness constraint involving end date, but UML captures these constraints in a note.

![](img/1344db3eba3d550e6edb009556fcd95c_449_0.png)

![](img/1344db3eba3d550e6edb009556fcd95c_449_1.png)

![](img/1344db3eba3d550e6edb009556fcd95c_449_2.png)

![](img/1344db3eba3d550e6edb009556fcd95c_449_3.png)

FIG. 10.25 Schemas including start date as part of the identifier for Visit.

A second approach is to introduce a simple, visible identifier for Visit, as shown in Fig. 10.26. Of course, both the former external uniqueness constraints still apply, but neither provides the preferred identifier.

In UML, hidden surrogate identifiers are assumed. However, we use id here as a visible identifier used by humans in the business domain to communicate about visits. This requires the addition of an id attribute to the UML diagram, as shown in Fig. 10.26(b).

In the Barker ER solution in Fig. 10.26(c), a visit-id attribute is added, with “#” marking it as the primary identifier, and the stroke is removed from the association lines. Barker ER has no notation for alternate identifiers, so now both external uniqueness constraints are lost.

![](img/1344db3eba3d550e6edb009556fcd95c_450_0.png)

FIG. 10.26 Introducing a simple identifier in (a) ORM, (b) UML, and (c) ER.

A third approach is to introduce an ordinal number as part of the identifier. Here, the number is used to count the number of times the same employee visited the same country. For example, your first visit to The Netherlands is distinguished from your second visit to The Netherlands simply by including “first” and “second” in the definite descriptions. This visit number is included in the models in Fig. 10.27. For example, the first and second visits of employee 1002 to The Netherlands map to the tuples (“1002”, “NL”, 1) and (“1002”, “NL”, 2), respectively.

A fourth approach in UML is to tag the association ends in Fig. 10.24(b) with {nonunique}, so the population of the association is a bag of (employee, country) pairs. A surrogate id then provides a visit identifier. While allowed, this approach is subconceptual because the visit identifiers are no longer part of human communication.

![](img/1344db3eba3d550e6edb009556fcd95c_451_0.png)

FIG. 10.27 Adding ordinals to help identify visits in (a) ORM, (b) UML, and (c) ER.

While we have now covered the most common temporal data model patterns, in practice other complexities can arise that require further analysis. So far, our constraints have been *static*—they apply to each state of the information system that models the business domain and may be checked by examining each state individually (e.g., each person was born on at most one date).

*Dynamic constraints* reference at least two states, which may be successive (e.g., no employee may be demoted in rank) or separated by a period (e.g., invoices ought to be paid within 30 days of issue).

UML supports dynamic constraints via both diagrams (e.g., state machines and activity diagrams, as discussed in later chapters) and textual (e.g., state of dynamic rules in OCL. Apart from the nontransferable setting in Barker ER, industrial ER provides no support for dynamic constraints. ORM allows dynamic rules to be added as textual notes, for which a formal semantics may be provided. Various dynamic rule extensions to both ER and ORM have been proposed, but so far these have not made their way into popular modeling tools.

We now briefly sketch some ways to add dynamic rule support to ORM, focusing initially on updates to the population of a functional fact type. The fact type in Fig. 10.28 is used to store the *current* salary of each employee.

![](img/1344db3eba3d550e6edb009556fcd95c_451_1.png)

FIG. 10.28 An ORM model with a functional fact type.

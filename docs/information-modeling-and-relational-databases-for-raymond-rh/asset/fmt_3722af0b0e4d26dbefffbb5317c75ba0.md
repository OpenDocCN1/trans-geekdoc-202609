
An initial conceptual schema is depicted in [Fig. 14.71](#Ch014_681-771_B9780443237904000189.xhtml#f0360)(a). If this is the global schema, the mandatory role constraints are implied by the pair-subset constraint. More importantly, the uniqueness constraint on the binary when combined with the pair-subset constraint has other implications. Can you spot these?

![Fig. 14.71 Is the ternary fact type elementary?](images/B9780443237904000189/f14-71-9780443237904.jpg)

[Fig. 14.71](#Ch014_681-771_B9780443237904000189.xhtml#B-f0360) Is the ternary fact type elementary?

The pair-subset constraint indicates that lecturers may teach only their assigned courses, but the uniqueness constraint on the binary indicates that each lecturer is assigned at most one course. Hence, lecturers may teach at most one course. So, there is an FD from the first role of the ternary to the second role, as shown in [Fig. 14.71](#Ch014_681-771_B9780443237904000189.xhtml#f0360)(b). Because the ternary has an implied, spanning UC, the implied FD implies the UC across the first and third roles. Moreover, because there is a third role in the ternary, the fact type now cannot be elementary. This is an example of the general rule set out in [Fig. 14.72](#Ch014_681-771_B9780443237904000189.xhtml#f0365). Two corollaries are included, one of which we will make use of in our example. You may wish to prove these corollaries as an exercise.

![Fig. 14.72 A basic splittability check.](images/B9780443237904000189/f14-72-9780443237904.jpg)

[Fig. 14.72](#Ch014_681-771_B9780443237904000189.xhtml#B-f0365) A basic splittability check.

If a fact type is elementary, all its FDs are the result of its UCs. If another FD exists, then semantically underlying this FD is another fact type, which is the target of a pair-subset constraint from the original fact type. If this is expressed at the conceptual level, we know the original fact type is not elementary, and we should remove the relevant role (as in [Fig. 14.72](#Ch014_681-771_B9780443237904000189.xhtml#f0365)).

The ternary in [Fig. 14.72](#Ch014_681-771_B9780443237904000189.xhtml#f0365) matches this pattern, but has an additional UC across its last two roles (for each course, a student has only one lecturer). To preserve this constraint after removing the role, an external UC must be added between the course and student roles in the new schema (see [Fig. 14.73](#Ch014_681-771_B9780443237904000189.xhtml#f0370)).

![Fig. 14.73 The corrected conceptual schema and its relational map.](images/B9780443237904000189/f14-73-9780443237904.jpg)

[Fig. 14.73](#Ch014_681-771_B9780443237904000189.xhtml#B-f0370) The corrected conceptual schema and its relational map.

The general requirement for this extra move is specified as the first corollary in [Fig. 14.72](#Ch014_681-771_B9780443237904000189.xhtml#f0365). When the corrected conceptual schema is Rmapped, we obtain two table schemes with two intertable constraints ([Fig. 14.73](#Ch014_681-771_B9780443237904000189.xhtml#f0370)).

Suppose that instead of dealing with [Table 14.8](#Ch014_681-771_B9780443237904000189.xhtml#t0045) conceptually, we develop a relational schema for it using the normal form theory discussed earlier. We might begin with a single ternary: `Teaches(lecturer, course, [student])`. Suppose that someone now tells us all the constraints or cleverly constructs a significant population from which the constraints can be deduced. We note that there are two composite uniqueness constraints over (lecturer, student) and (course, student). Because student is an optional attribute, neither of these can be used as a primary key, so we know something is wrong. Indeed, we know the table is not in BCNF because we have the FD `lecturer → course`, and lecturer is not a key.

At this stage we split the table into two: `Assigned(lecturer, course)`; `Instructs(lecturer, student)`. These are the same two tables we arrived at by deconceptualization in [Fig. 14.73](#Ch014_681-771_B9780443237904000189.xhtml#f0370). However, the normal form theory discussed in this section tells us nothing about the two intertable constraints. We have to figure these out for ourselves.

The final normal form we discuss is **sixth normal form** (**6NF**), which was proposed by Chris Date and others in the late 1990s mainly to simplify the implementation of temporal databases. A relation scheme is in 6NF if and only if it satisfies no nontrivial join dependencies. A 6NF table scheme is automatically in 5NF and DKNF.

Intuitively, a 6NF table scheme contains the primary key and at most one other attribute. So, each row of a 6NF table contains just one atomic fact. Recall that an atomic fact is either an elementary fact or an existential fact.

For example, the 5NF table scheme `Person(name, gender, height, weight, maritalStatus)` may be decomposed into the following 6NF table schemes: `Person(name, gender)`; `Person(name, height)`; `Person(name, weight)`; `Person(name, maritalStatus)`. This makes it easier to store temporal information such as the period during which a person has a specific height, a specific weight, or a specific maritalStatus.

As a trivial example, the table scheme `Person(name)` is also in 6NF because each of its rows holds just one existential fact (e.g., there is a person named “Joseph Robinette Biden Jr.”).

Further normal forms could be invented to cater for further constraints, but surely it is better to focus on cleaning up design faults at the conceptual level where humans can utilize their semantic understanding of the UoD more easily.

As discussed in the next section, it is sometimes necessary to denormalize a relational schema to achieve acceptable performance. This is a possible option for the current example. Note that the intertable constraints are expensive to enforce, unlike key constraints. For example, enforcing the external uniqueness constraint effectively requires a table join each time a row is inserted into either table. Moreover, queries to list who teaches what to whom need a table join.

Another design is obtained by mapping the original ORM schema in [Fig. 14.71](#Ch014_681-771_B9780443237904000189.xhtml#f0360)(a) to give the relational schema shown in [Fig. 14.74](#Ch014_681-771_B9780443237904000189.xhtml#f0375)(a). The pair-subset constraint implies the ternary’s other key constraint on (lecturer, student), which may thus be omitted. Although the ternary is denormalized, it is safe because its problematic FD is enforced by the pair-subset constraint and the key constraint in the binary. We may now list who teaches what to whom, without a table join. If this is a focused query for the application, this design might be preferred.

![Fig. 14.74 Some denormalization options.](images/B9780443237904000189/f14-74-9780443237904.jpg)

[Fig. 14.74](#Ch014_681-771_B9780443237904000189.xhtml#B-f0375) Some denormalization options.

To modify the example somewhat, suppose lecturers must teach the course assigned to them (so the null in [Table 14.8](#Ch014_681-771_B9780443237904000189.xhtml#t0045) cannot occur). [Fig. 14.71](#Ch014_681-771_B9780443237904000189.xhtml#f0360)(a) is changed to make both roles of Lecturer mandatory, with the subset constraint becoming an equality constraint, and [Fig. 14.73](#Ch014_681-771_B9780443237904000189.xhtml#f0370) is changed to make both roles of Lecturer mandatory, and the relational subset constraint becomes an equality constraint.

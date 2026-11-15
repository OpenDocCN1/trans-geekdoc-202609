
![](img/1344db3eba3d550e6edb009556fcd95c_526_0.png)

FIG. 11.20 Composite secondary identifier and functional fact type.

Now consider the conceptual schema of Fig. 11.21. Here, each laboratory session is identified primarily by a session number and is used for a particular course. Once these course bookings have been made, sessions are assigned for use by students. The external uniqueness constraint says that each student is assigned at most one session for each course (e.g., laboratory resources might be scarce). Because this constraint involves fact types rather than reference types, it can be mapped.

An unusual feature of this example is the application of the external uniqueness constraint to a set of roles that includes a role in an m:n fact type (LabSession is assigned to Student). Because the m:n fact type must map to a table by itself, the external uniqueness constraint spans two relational tables. This is equivalent to an internal uniqueness constraint spanning courseCode and studentNr in the natural join of the two tables.

![](img/1344db3eba3d550e6edb009556fcd95c_526_1.png)

FIG. 11.21 External uniqueness constraint involving an m:n fact type.

## Mapping Objectified Associations

Let's now discuss some cases involving objectification (also known as nesting). In Fig. 11.22, the association Employee worked on Project is objectified as Work. This objectified type plays one mandatory and one optional role, both of which are functional. As with other object types, we initially treat the objectified association as a “black box”, mentally erasing its identification scheme.

From this viewpoint, the conceptual schema appears to have just two fact types, both having functional roles attached to the object type Work. Fact types are now grouped in the usual way. So, these two fact types are grouped into the same table. Visualizing the nested object type Work as a black box “ ■ ” results in the table Work( ■, startdate, [enddate] ). Finally, we unpack ■ into its component attributes (empNr and projectName), giving Work( empNr, projectName, startdate, [enddate] ).

![](img/1344db3eba3d550e6edb009556fcd95c_527_0.png)

FIG. 11.22 An active, objectified association with functional roles.

The value constraint in Fig. 11.22 verbalizes as **For each Work, existing** enddate >= startdate. Value constraints are violated if and only if they evaluate to false (just like SQL check clauses). The footnote annotation on the relational schema here corresponds to the SQL check clause **check** (enddate >= startdate).

Now consider the ORM schema of Fig. 11.23. Here, employees might be assigned to projects before their actual starting date is known. So, some instances of the objectified Assignment association might be recorded that (in some database state) do not play either of the attached roles. In this example, because even the disjunction of the attached roles is optional, the nested object type is _independent_—this is noted by the exclamation mark in “Assignment !”. Contrast this with the previous example (Fig. 11.22), where the nested object type Work is active and the startdate column in the relational schema is not optional.

![](img/1344db3eba3d550e6edb009556fcd95c_527_1.png)

FIG. 11.23 Mapping an independent, objectified association with functional roles.

Independent object types, whether nested or not, require special treatment in mapping, as follows.

- Map each independent object type and the fact types (if any) in which it plays functional roles to a separate table, with the object type’s identifier as the primary key and all other attributes optional. Add a subset constraint to this primary key from each column sequence mapped from nonfunctional roles (if any) of the independent object type.

If we wish to record just the fact that an employee is assigned to a particular project, we enter values just for empNr and projectName. Details about start and end dates for work on the project can be added later when they are known. Because both start date and end date are optional, the value constraint now verbalizes as **For each Assignment, existing enddate >= existing startdate.**

Fig. 11.24 shows another way to model this UoD. The independent object type has no functional roles attached, and maps to a table all by itself. The m:n fact type maps to another table. A subset constraint captures its optionality. If instead we tried to map everything to one table, this would violate entity integrity (why?).

The constraint that if an assignment’s start and end dates are known, the end date must come after or on the start date is now harder to formulate, both at the conceptual level and at the relational level. Moreover, the approach of Fig. 11.24 spreads the information over more tables and demands an intertable constraint. This is usually undesirable because it often slows down the execution of queries and updates. For such reasons, the approach of Fig. 11.23 is normally preferred to that of Fig. 11.24.

The schemas in Figs. 11.23 and 11.24 allow us to record an end date without a start date. In practical applications, we sometimes allow things like this because our information may be incomplete. For example, we might want to record the date somebody ended a project, but not know when that person started.

![](img/1344db3eba3d550e6edb009556fcd95c_528_0.png)

FIG. 11.24 Mapping an independent, objectified association with no functional roles.

In such cases, conceptual schemas sometimes have fewer mandatory roles than the ideal world suggests, and in consequence relational schemas may have more optional columns than complete knowledge would allow.

Suppose however, that if we know an end date then we do know the starting date. To enforce this constraint in Fig. 11.23, add a subset constraint on the ORM schema from the first role of the “ended on” predicate to the first role of the “started on” predicate.

This constraint may be declared in the relational schema by using *nested option brackets*. Here, we enclose the option brackets for enddate *inside* the option brackets for startdate, giving Assignment( empNr, projectName, [ startdate, [enddate] ] ). This indicates that a (nonnull) value is recorded for enddate only if a value is recorded for startdate.

To add this constraint to Fig. 11.24 is not as easy. A textual constraint is required at both conceptual and relational levels to declare that for each employee, project pair, phase “end” is recorded only if phase “start” is.

Chapter 14 examines in detail the notion of “equivalent” conceptual schemas and provides guidelines for transforming a conceptual schema to improve the efficiency of the relational schema obtained from Rmap.

If the start and end dates for an employee’s work on a project are recorded, a derivation rule can be specified to compute the work period (by subtracting the start date from the end date, if known). Because each computer system has an internal clock, conceptually there is a unary fact type of the form Date is today. So, for someone still working on a project, we could also derive the time spent so far on the project by subtracting the start date from the current value for “today”.

By default, derived facts are not stored. So, *by default, derived columns are excluded from the base tables* (i.e., stored tables) of the relational schema. For example, the derivation rules could be implemented using views or stored procedures.

In some cases, efficiency considerations may lead us to *derive on update* rather than at query time and to store the derived information. In such cases, the derived fact type is marked “***” on the conceptual schema diagram. During the relational mapping, the fact type is mapped to a base table, and the derivation rule is mapped to a rule that is triggered by updates to the base table(s) referenced in the derivation rule.

For example, we could implement the derivation rule by declaring appropriate generated columns or table triggers (recall the earlier net pay example). As well as derivation rules, *all conceptual constraints should be mapped* (not just uniqueness and mandatory constraints).

## Mapping Subtypes

Let’s now consider the *mapping of subtype constraints*. Table 11.1 was seen earlier in Chapter 6. Although we have no rule to determine when a phone number is recorded, we know that prostate status may be recorded only for male patients and pregnancies are recorded for all female patients and only for female patients. The conceptual schema is reproduced in Fig. 11.25.

Table 11.1 Patient details.

| PatientNr | Name | Gender | Phone | Prostate status | Pregnancies |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 101 | Adams A | M | 2052061 | OK | – |
| 102 | Blossom F | F | 3652999 | – | 5 |
| 103 | Jones E | F | ? | – | 0 |
| 104 | King P | M | ? | Benign enlargement | – |
| 105 | Smith J | M | 2057654 | ? | – |

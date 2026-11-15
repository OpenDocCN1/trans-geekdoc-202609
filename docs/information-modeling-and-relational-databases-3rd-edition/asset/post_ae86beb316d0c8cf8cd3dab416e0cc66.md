
child's primary key) that references the parent. By definition, the child must be identifier dependent, as shown by the soft rectangle. The parent is identifier independent (as shown here) unless it is made dependent by some other relationship.

IDEF1X allows both forward and inverse predicate readings for relationships. These may be written together, as shown in Fig. 8.29(a), or on different sides of the relationship line, as shown later in Fig. 8.30(a).

**(a)**

**Room**

| bldgNr (FK) |
| --- |
| roomNr |
| size |
| phoneNr (O) |

**Building**

| bldgNr |
| --- |
| bldgName (AK1) |
| nrFloors |

![](img/1344db3eba3d550e6edb009556fcd95c_353_0.png)

FIG. 8.29 The IDEF1X schema (a) is equivalent to the ORM schema (b).

The forward reading of a specific connection relationship is always toward the child, and hence toward the dot “•”. This forward or “parent-perspective” reading must be supplied. The inverse or “child-perspective” reading, if supplied, is toward the parent (away from the dot). If both readings are supplied, a slash “/” is appended to the forward reading. In Fig. 8.29(a), the forward reading is Building contains Room and the inverse reading is Room is in Building. The child is on the left, so the forward reading is right to left. For nonspecific (m:n) relationships, the forward reading is always read from left to right (or top to bottom if the relationship line is vertical). Recall that m:n relationships exist only at the ER view level.

The equivalent ORM diagram in Fig. 8.29(b) makes it clear that the association Room is in Building is part of the composite reference scheme for Room. In the IDEF1X diagram, this association is actually depicted by including bldgNr as part of the key for Room, and the connection “relationship” shows the foreign key reference. We can partially lift the IDEF1X discussion to a conceptual level by talking of the parent’s primary key migrating to the child (see Fig. 8.30).

Although not a legal IDEF1X diagram, Fig. 8.30(a) helps portray Room as being partly identified by its room number and partly by its relationship to Building. Compare this with the Barker notation depiction in Fig. 8.9. At this level, the association Room is in Building is conceptual.

Now, imagine a copy of Building's primary key migrating to complete the primary key of Room, as in Fig. 8.30(b). At this stage, we have dropped to the logical level. The conceptual relationship between Room and Building is now depicted by Room's bldgNr attribute. We still need to indicate that any value for this attribute must also occur as a primary key value of Building, and this foreign key reference is what the connection line now represents. We removed the “relationship” name to stress this point. You can now think of the connection line as a foreign key arrow.

For identifying relationships, each child (instance) is associated with exactly one parent (instance), as shown by a solid line with no adornments. By default, a parent is associated with zero or more children, as shown by an unadorned dot “•” at the line end. If familiar with UML, think of this as equivalent to “*”. You can override this default child cardinality by adorning the dot with a cardinality constraint mark. The main cases are shown in Fig. 8.31 along with their ORM counterpart. Here, “P” indicates a positive number (at least 1), and “Z” indicates zero or 1 (at most 1). A single number (e.g., 3) indicates exactly that number. You can also indicate ranges. For example, “2–5” indicates at least 2 and at most 5.

![](img/1344db3eba3d550e6edb009556fcd95c_354_0.png)

FIG. 8.30 Building's primary key “migrates” to become a foreign key in Room.

| nrChildren | IDEF1X | ORM |
| :--- | :--- | :--- |
| 0 or more | Child •— Parent | Child —— Parent |
| 1 or more | Child •— P — Parent | Child •——— Parent |
| 0 or 1 | Child •— Z — Parent | Child —— Parent |
| Exactly n | Child •— n — Parent | Child — n — Parent |

FIG. 8.31 Main child cardinality cases for identifying relationships.

To make sense of these cardinality constraints, think of them as applying to the conceptual relationship that existed before the key was migrated to the child (cardinality constraints on a foreign key reference are rather pointless). The “Z” mark is unintuitive for “at most 1”, and in IDEF1X, an alternative notation for this constraint is to use a hollow dot “◦”.

A nonidentifying relationship is shown as a named, dashed line. Child and parent are independent unless made dependent by some other relationship. If the dashed line is unadorned, each child (instance) is associated with exactly one parent (instance), as in Fig. 8.32(a). If a diamond is added at the parent end, each child is associated with at most one parent, as in Fig. 8.32(b). The corresponding ORM diagrams are also shown.

In a nonidentifying relationship, the child nonkey attributes (those not in the primary key) include a foreign key that references the parent’s primary key. If the foreign key is mandatory (each component is nonnull), then each child instance is associated with exactly one parent instance. This is referred to as a mandatory relationship, but actually means that the child role of the conceptual relationship that (before migration) gave rise to the foreign key reference is mandatory.

![](img/1344db3eba3d550e6edb009556fcd95c_355_0.png)

![](img/1344db3eba3d550e6edb009556fcd95c_355_1.png)

Fig. 8.33(a) depicts this situation in more detail. Here, a and b are simple or composite attributes. If the foreign key is optional (its components may all be null), then each child instance is associated with at most one parent instance. Fig. 8.33(b) depicts this situation. In IDEF1X, this is referred to as an optional relationship.

In both mandatory and optional cases, each instance of the child’s foreign key that has no null components must occur as an instance of the parent’s primary key. This is the default meaning of a foreign key constraint in structured query language (SQL). For the mandatory case, of course, there can be no null components.

An example of a mandatory, nonidentifying connection relationship is shown in Fig. 8.34(a). Here, each employee is identified by an employee number, must have a name, and must work for a department. Each department is identified by its code and must have a unique name.

![](img/1344db3eba3d550e6edb009556fcd95c_356_0.png)

FIG. 8.34 Same example in (a) IDEF1X, (b) IE, (c) Relational, and (d) ORM.

The fact (conceptual relationship) that a given employee works for a given department is stored by instantiating the empNr and deptCode attributes of Employee (e.g., empNr = 101, deptCode = “HR”). The connection “relationship” is simply a foreign key reference indicating that each department code of an employee must be a department code of a department.

The same example is shown in IE notation in Fig. 8.34(b) and in ORM notation in Fig. 8.34(d). Here, the association Employee works for Department is depicted conceptually, rather than by including an attribute of Employee. This would also be the case for the Barker notation. Fig. 8.34(c) depicts the situation in a relational notation. Here, facts about who works for what department are stored in the Employee table, which includes a deptCode attribute referencing the Department table. If you compare this with the IDEF1X notation in Fig. 8.34(a), it should be clear that they are just two notational variations of the same structure. In key-based and fully attributed views, the IDEF1X notation is essentially a logical notation rather than a conceptual one.

As another example of nonidentifying relationships, the room scheduling example considered in Sections 1.2 and 8.2 is modeled in IDEF1X in Fig. 8.35(a). The ORM model for this situation is reproduced in Fig. 8.35(b), without the fact populations. The primary key and alternate key constraints in the IDEF1X model correspond to the uniqueness constraints in the ORM model. Although the IDEF1X schema does capture all the constraints, it is a logical rather than a conceptual representation, and unlike ORM it does not facilitate validation by verbalization and population.

Fig. 8.36 shows a more complex IDEF1X example involving a compound foreign key relationship corresponding to a pair-subset constraint in the ORM schema.

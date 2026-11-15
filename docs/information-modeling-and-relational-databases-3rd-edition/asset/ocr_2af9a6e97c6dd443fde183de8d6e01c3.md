Now, imagine a copy of Building's primary key migrating to complete the primary key of Room, as in Fig. 8.30(b). At this stage, we have dropped to the logical level. The conceptual relationship between Room and Building is now depicted by Room's bldgNr attribute. We still need to indicate that any value for this attribute must also occur as a primary key value of Building, and this foreign key reference is what the connection line now represents. We removed the “relationship” name to stress this point. You can now think of the connection line as a foreign key arrow.

For identifying relationships, each child (instance) is associated with exactly one parent (instance), as shown by a solid line with no adornments. By default, a parent is associated with zero or more children, as shown by an unadorned dot “•” at the line end. If familiar with UML, think of this as equivalent to “*”. You can override this default child cardinality by adorning the dot with a cardinality constraint mark. The main cases are shown in Fig. 8.31 along with their ORM counterpart. Here, “P” indicates a positive number (at least 1), and “Z” indicates zero or 1 (at most 1). A single number (e.g., 3) indicates exactly that number. You can also indicate ranges. For example, “2–5” indicates at least 2 and at most 5.

![](bbox=[0.13, 0.432, 0.836, 0.558])

FIG. 8.30 Building's primary key “migrates” to become a foreign key in Room.

| nrChildren | IDEF1X | ORM |
| :--- | :--- | :--- |
| 0 or more | Child •— Parent | Child —— Parent |
| 1 or more | Child •— P — Parent | Child •——— Parent |
| 0 or 1 | Child •— Z — Parent | Child —— Parent |
| Exactly n | Child •— n — Parent | Child — n — Parent |

FIG. 8.31 Main child cardinality cases for identifying relationships.
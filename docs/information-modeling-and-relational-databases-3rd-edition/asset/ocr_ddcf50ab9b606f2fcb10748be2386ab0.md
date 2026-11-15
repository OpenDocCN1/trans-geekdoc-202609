# Table 4.3 Uniqueness constraints added to original table.

| Student Nr | Name | Class |
|---|---|---|
| 001 | Adams J | 11A |
| 002 | Brown C | 12B |
| 003 | Brown C | 11A |

If another student named “Brown C” joined one of these classes, at least one of the names would need to be modified to keep them distinct within that class. For instance, we could add extra initials or numbers (e.g., “Brown CT”, “Brown C2”).

Each row of the report splits into two elementary facts, one for the name and one for the class. To specify the name-class UC on the schema, we need two fact types. The role boxes to which the UC applies are joined by dotted lines to a circled uniqueness bar, as shown in Fig. 4.36.

Because this UC involves roles from different predicates, it is an example of an external constraint or interpredicate constraint. A constraint on a single predicate is an internal or intra-predicate constraint. So, there are two kinds of UCs: internal uniqueness and external uniqueness.

![](bbox=[0.3, 0.45, 0.72, 0.6])

# FIG. 4.36 An external uniqueness constraint has been added.

In this example, the external UC indicates that for each student, the *combination* of student name and class is unique. The constraint verbalizes as “Given any StudentName and Class, at most one Student has that StudentName and is in that Class”. For instance, given “Adams J” and “11A” there is only one StudentNr sharing rows with both (“001”). Given “Adams J” and “12B” there is no StudentNr paired with both.

An easy way to understand this constraint is to say that if we perform the conceptual (inner) *join* operation on the two fact tables, then the resulting table has a UC across the (name, class) column pair. Note that when we join the two fact tables, we obtain the table in the original report (Table 4.3).

The external UC is equivalent to an internal UC on the first and last roles of the derived, ternary fact type formed from the join path: StudentName is of Student *who* is in Class. See Fig. 4.37. The object type Student is personal, so we prefer the personal pronoun “who” instead of “that”.
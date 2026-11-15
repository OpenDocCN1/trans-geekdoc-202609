+   (h) The external uniqueness constraint that each RGB intensity combination applies to at most one Color cannot be specified as a unique clause in most DBMSs, but can be coded using a trigger. Write appropriate trigger code to enforce this constraint.
+   
+   (i) Now write SQL code to perform the data migration needed to populate the CarSale2 schema.
+   
+   (j) Using your new CarSale2 schema, reformulate the queries in (c), (d), and (e).

# 14.10 Summary

Conceptual schemas are equivalent iff they model the same UoD. Various schema transformations may be performed to reshape a conceptual schema into one that is either equivalent, or an acceptable alternative.

Predicate specialization fragments a predicate into two or more special cases, typically by absorbing an enumerated object type into it. For example, the association Person is of Gender {‘M’,‘F’} may be specialized into Person is male and Person is female by absorbing Gender.

The inverse transformation, predicate generalization, typically involves extracting an enumerated object type from a predicate. Predicate specialization/generalization (PSG) may also be performed by considering the n cases of a role with a frequency constraint of n or ≤n. For example, the association Person is a parent of Person with a frequency constraint of 2 on its second role may be specialized into Person is parent1 of Person and Person is parent2 of Person.

Nested object types may be interchanged with coreferenced object types, using the Nest/Coreference transformation (N/CR). Either representation may be replaced by flattening into one or more fact types. For example, consider the nesting Enrollment(Student enrolled in Subject) results in Rating. If results are mandatory, this may be flattened into the ternary Student for Subject scored Rating. If results are optional, the flattened approach requires an extra binary (Student enrolled in Subject) targeted by a pair-subset constraint from the ternary.

The overlap algorithm indicates how nesting may be performed for compatible subpredicates, depending on the constraint between them (subset, equality, exclusion, etc.). See Fig. 14.35. Other schema transformations exist. A transformation might convert a graphical constraint to a textual constraint (or vice versa).

Although nested and coreferenced approaches have the same relational map, many other cases of equivalent conceptual schemas result in different relational schemas when subjected to the standard Rmap procedure. The process of transforming a conceptual schema into another that results in a more efficient relational map is called conceptual schema optimization.

Many optimization moves aim to reduce the number of relational tables, typically by specializing nonfunctional predicates into functional ones that can be grouped into the same table as another functional fact type or by using nesting (or coreferencing) to unify compatible composite keys. This is particularly useful in reducing the number of table joins required
other than primary keys). For example, your metaschema should be able to store the following schema:

```
Employee ( empNr, empName, salary, [taxPaid] )
     ^
     |
Drives ( empNr, carRegNr )
```

+   2. Map your answer to Question 1 to a relational metaschema.

+   3. A sample UML class diagram is shown.

![](bbox=[0.185, 0.29, 0.79, 0.535])

Specify a metaschema in ORM notation for simplified UML class diagrams that are restricted to the following features. Classes have attributes only (e.g., no operations). Attributes have visibility (+=public, #=protected, -=private, ~=package) and multiplicity (*=0 or more, 0.0.1=0 or 1, 1..*=1 or more, 1=exactly 1). Associations may be binary or n-ary. No association classes or qualified associations are allowed. Association ends have multiplicity (*=0 or more, 0..1=0 or 1, 1..*=1 or more, 1=exactly 1). Role names are mandatory (whether or not they are displayed). The only constraints that may be added to a subclassing scheme are disjoint and complete. No derived attributes or derived associations are allowed. No notes are allowed. No aggregation is allowed.

No other graphic constraints (e.g., {ordered}, {xor}, {subset}) or textual constraints are allowed. Ignore our extensions (e.g., {P}, {U1}). Ignore data types. Ignore instance populations and presentation aspects (e.g., layout, or whether the display of a feature is suppressed). Your metaschema should be able to store a single class diagram like the one shown.

+   4. Specify a metaschema in ORM notation for Barker ER (as discussed in Section 8.2). Your metaschema should be able to store a single Barker ER diagram like the one shown.
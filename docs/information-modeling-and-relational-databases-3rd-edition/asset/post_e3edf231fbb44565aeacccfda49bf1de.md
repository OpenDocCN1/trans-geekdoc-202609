
Consider the conceptual schema in Fig. 11.9. The many:many fact type maps to a separate table (using rule 1). The unary fact type is functional because it has an implied uniqueness constraint. The functional fact types map to a table keyed on the identifier of Employee (using rule 2).

The primary keys are underlined, and the optionality of mobileNr is shown by the square brackets. Under closed world assumption (CWA) semantics, the unary fact type Employee is tenured maps to a mandatory Boolean column. Currently, NORMA instead maps all unaries to an optional Boolean; however, there are future plans for NORMA to distinguish between CWA, open world assumption (OWA), and open world with negation (OWN) semantics. The dotted arrow depicts the subset constraint that each employee referenced in the Drives table is also referenced in the primary key of the Employee table (referential integrity).

![](img/1344db3eba3d550e6edb009556fcd95c_518_0.png)

Now consider the ORM schema in Fig. 11.10. Notice the equality constraint, shown as an arrow-tipped dotted line between the empNr fields of both tables. This is needed because both roles played by Academic are mandatory, and each maps to a different table. An equality constraint is equivalent to two subset constraints going in opposite directions. This causes a referential cycle because each table refers to the other.

The subset constraint from Qualification.empNr to Academic.empNr is a simple foreign key constraint because it references a primary key. But the subset constraint from Academic.empNr to Qualification.empNr is not a foreign key constraint because it targets only part of a primary key.

![](img/1344db3eba3d550e6edb009556fcd95c_518_1.png)

This latter subset constraint may be enforced in various ways (e.g., by assertions, triggers, or stored procedures). Referential cycles typically result from a mandatory role that has no simple uniqueness constraint. Because referential cycles require special care to implement, this conceptual constraint pattern should be avoided if possible. In our example, however, the business rule that each academic holds at least one degree does seem reasonable, so in this case we leave it as is.

Before leaving this example, a few more comments about naming are worth making. The table name "Qualification" is one of many possible choices to convey the notion of academics being qualified by their degrees. Two other choices are to use the association name ("Holds") or to concatenate the object type names ("AcademicDegree"). The department column is named "deptCode" because we expect other departmental facts (not shown here) to be recorded in a department table, and we want to avoid using "department" to name both a column and a table. Similarly, the degree column is named "degreeCode" rather than "degree" because we might want to record other facts about degrees (e.g., their titles). In general, if the object type underlying a column will also underlie the primary key of another table, it is advisable to include the reference scheme in the column name.

Now consider Fig. 11.11. Here, each horse has its gender and weight recorded. Each race has at most one winner (we do not allow ties). There are no composite keys for rule 1 to work on. The gender and weight fact types have functional roles attached to Horse. By rule 2, these two associations must be grouped into the same table keyed on the identifier for Horse. Similarly, the time and win fact types are functions of race and are grouped into the Race table. We chose the column name "raceTime" instead of "time" mainly because "time" is a reserved word in SQL. It's best to avoid using reserved words for names because they require double quotes. We later provide links to online lists of SQL reserved words. The column name "winner" is used instead of "horseName" to convey the semantics better.

![](img/1344db3eba3d550e6edb009556fcd95c_519_0.png)

## Mapping 1:1 Associations

Let's now consider some examples involving 1:1 fact types. In the conceptual schema of Fig. 11.12, both Bankcard and Client share a 1:1 association. If we are certain that no other functional roles will be played by Bankcard, it is usually best to group the 1:1 fact type together with the other functional fact types into the same table, as shown.

![](img/1344db3eba3d550e6edb009556fcd95c_520_0.png)

```
Client ( clientNr, gender, birthdate, [bankcard] )
```

### FIG. 11.12 The mapping choice if Bankcard plays no other functional roles.

The bankcard column is optional, but the disadvantage of nulls here is usually outweighed by the advantage of having all the data in one table. The underlining of bankcard indicates a uniqueness constraint for its nonnull values. Because it may contain more than one null, the bankcard column cannot be used to identify rows, and hence cannot be the primary key. With two uniqueness constraints, we doubly underline clientNr to highlight it as the primary key.

If Bankcard does play other functional roles, however, the bankcard ownership association should be grouped into a Bankcard table, as shown in Fig. 11.13. Notice that the owned role played by Bankcard is now explicitly mandatory; in the previous example, it was only implicitly mandatory (because it was the only role played by Bankcard). Notice that only one role of this 1:1 association is mandatory. In asymmetric cases like this, it is usually better to group on the mandatory role side as shown.

![](img/1344db3eba3d550e6edb009556fcd95c_520_1.png)

```
Client ( clientNr, genderCode, birthdate )
Bankcard ( bankCardNr, clientNr, expirydate )
```

### FIG. 11.13 The mapping choice if Bankcard plays another functional role.

To illustrate this idea further, consider the conceptual schema in Fig. 11.14. Each employee is identified primarily by his/her employee number, but also has a unique name (unusual, but some departments work that way by refining formerly duplicate names). Each department has one head, who heads only one department. Because not all employees are department heads, the role of heading is optional.

![](img/1344db3eba3d550e6edb009556fcd95c_521_0.png)

### FIG. 11.14 The heads fact type is grouped on the mandatory role side.

Hence, the 1:1 association between Employee and Department is optional for Employee but mandatory for Department. Because it is usually better to group on the mandatory role side, here this means including the headEmployeeNr column in the Department table, as shown.

The NORMA tool allows you to edit the column names generated in the relational schema simply by editing their name property. For example, we may shorten "employeeNr", "employeeName", and "departmentCode" to "empNr", "empName", and "deptCode", respectively.

Suppose we grouped the 1:1 association on the optional side instead, by adding a deptHeaded column to the Employee table. This leads to the following relational schema:

Employee ( empNr, [deptHeaded], empName, salary )
Department ( deptCode, budget )

This alternative has two disadvantages. First, the optional deptHeaded column permits nulls (unlike the mandatory headEmpNr column). All other things being equal, nulls should be avoided if possible. In addition to consuming storage, they are often awkward for people to work with. The second disadvantage is that we now have an equality constraint between the tables, rather than just a subset constraint.

In principle, we might group into one table all the functional predicates of both object types involved in a 1:1 association. With our example, this gives the schema EmployeeDept( empNr, empName, salary, [deptHeaded, deptBudget] ). Here, enclosing the last two columns in the same square brackets declares that one is null if and only if the other is.

However, apart from requiring two optional columns and a special constraint that requires them to be null together, this grouping is unnatural. For example, the primary key suggests that the whole table deals with employees rather than their departments. For such reasons, this single-table approach should normally be avoided.

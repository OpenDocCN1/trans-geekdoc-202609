
Now consider Fig. 11.15(a). Here, each employee has the use of exactly one company car, and each company car is allocated to exactly one employee. Employees and cars are identified by their employee number and by their registration number, respectively. The names of employees and the car models (e.g., Mazda CX5) are also recorded, but might not be unique. Here, both roles of the 1:1 association are mandatory, and each is attached to an entity type with another functional role. Should the 1:1 fact type be grouped into an Employee table or into a Car table?

Unlike the previous example, we now have a symmetrical situation with respect to mandatory roles. An arbitrary decision could be made here. We could group to the left, as in Fig. 11.15(a) and (b), or to the right as in Fig. 11.15(c). Either of these approaches is reasonable.

![](img/1344db3eba3d550e6edb009556fcd95c_522_0.png)

**(b)** Employee( empNr, empName, carRegNr )
Car( carRegNr, carModel )

**(c)** Employee( empNr, empName )
Car( carRegNr, carModel, empNr )

FIG. 11.15 The ORM schema (a) may map to relational schema (b) or to schema (c).

We might also try mapping to a single table: EmployeeCar( empNr, empName, carRegNr, carModel ). Although possible, this is unnatural, requiring an arbitrary choice of primary key. This becomes more awkward if other facts about employees (e.g., gender) and cars (e.g., purchase date) are recorded in the table. Also, consider the additional update overhead to change the car used by an employee compared with the two-table approach.

Now what about the case of a 1:1 fact type with both roles optional? For example, consider a UoD identical to that just discussed except that only some employees are given company cars and only some company cars are used by employees (e.g., some may be reserved for important visitors). The two table approach is recommended.

Because of the symmetry with respect to mandatory roles, we could map the 1:1 association into the Employee table to give the schema Employee( empNr, empName, [carRegNr] ); Car( carRegNr, carModel ); Employee.carRegNr references Car.

Alternatively, we could map the 1:1 association to the Car table yielding the schema Employee( empNr, empName ); Car( carRegNr, carModel, [empNr] ); Car.empNr references Employee. The percentage of nulls is likely to differ in these two designs. In this case, the design with fewer nulls is usually preferable.

Yet another option is a three-table approach, in which the 1:1 association has a table to itself. This option becomes more attractive if the two-table approach yields high percentages of nulls. For example, if only 1% of employees and 1% of cars are likely to be involved in Employee drives Car, we might map this fact type into a table by itself, giving three tables overall.

A fourth option for 1:1 cases is to use two tables, but include the 1:1 association in both with a special equality constraint to control the redundancy. More detailed discussions of mapping 1:1 fact types are referenced in the chapter notes. Our default procedure is summarized in Fig. 11.16; here, “functional role” means a functional role in an elementary fact type (not a reference type).

In Fig. 11.16, the arrow “$\leftarrow\rightarrow$” indicates that the 1:1 fact type should be grouped into the functional table of the left-hand object type. In case (a), the right-hand object type may play nonfunctional roles not shown here, and any role in the 1:1 fact type may be optional or mandatory. The third case (no other functional roles) is rare and requires a choice of primary key in the separate table. The final line refers to symmetric cases where the roles of the 1:1 predicate are both mandatory or both optional, and both object types play another functional role—here, we have a grouping choice.

![](img/1344db3eba3d550e6edb009556fcd95c_523_0.png)

```
Each 1:1 fact type maps to only one table:

if   (a) only one object type in the 1:1 predicate has another functional role
         then group on its side
else if (b) both object types have other functional roles
         and only one role in the 1:1 is explicitly mandatory
         then group on its side
else if no object type has another functional role
         then map the 1:1 to a separate table
else   the grouping choice is up to you
```

FIG. 11.16 Default procedure for mapping 1:1 fact types.

To understand some further cases, it will help to recall the fundamental bridge between conceptual and logical levels. This is summarized in Fig. 11.17. In the populated ORM schema in Fig. 11.17(a), the mandatory role pattern anticipates other roles being added later to Employee but not Gender.

![](img/1344db3eba3d550e6edb009556fcd95c_524_0.png)

FIG. 11.17 The conceptual/logical bridge.

Fig. 11.17(a) abbreviates the preferred reference schemes shown explicitly in Fig. 11.17(b), which uses icons to directly depict a female employee and the female gender. The shaded, derived association abbreviates the conceptual path from EmployeeNr through Employee and Gender to GenderCode. This unpacks the semantics underlying the relational schema in Fig. 11.17(c).

Recall that uniqueness constraints on reference predicates are the responsibility of humans to enforce. The information system can’t stop us from giving the same employee number to two different employees, or from giving the same employee two employee numbers. Hence, *uniqueness constraints on primary reference schemes are not mapped*. Instead, we must enforce them in the real world.

However, assuming we have enforced the primary reference constraints, the system can enforce constraints on the fact types. For example, it enforces the uniqueness constraint in *Employee( empNr, genderCode )* by ensuring that each employee number occurs only once in that column and hence is paired with at most one gender code. Assuming that the reference types really are 1:1, this uniqueness constraint on empNr corresponds to the uniqueness constraint on the conceptual fact type (i.e., **Each Employee is of at most one Gender**). It does not capture any uniqueness constraint from the reference types.

## Mapping External Uniqueness Constraints

Let's now consider mapping of schemas that include *external uniqueness constraints*. Recall that such constraints appear as a circled bar, and if they are used for preferred reference they have a double bar. In the ORM schema of Fig. 11.18, employees are identified by combining their family name and initials. Because the external uniqueness constraint in this example underlies the preferred reference scheme, it is not mapped. In the resulting table scheme Employee( familyName, initials, genderCode ), the uniqueness constraint corresponds to the uniqueness constraint on the conceptual fact type Employee is of Gender.

![](img/1344db3eba3d550e6edb009556fcd95c_524_1.png)

FIG. 11.18 Composite primary identifier and functional fact type.

A good way to visualize the mapping is as follows:

- Mentally erase the identification scheme of each object type.
- Group facts into tables, using simple surrogates for the roles of real-world objects.
- Replace each surrogate by the attribute(s) used in the table to identify the objects.

For example, the conceptual schemas of Figs. 11.17 and 11.18 each map initially to Employee( e , g ) with the meaning Employee e is of Gender g. In both cases, g is then replaced by “genderCode”. With Fig. 11.17, e is replaced by empNr, but with Fig. 11.18, e is unpacked into (familyName, initials) because the identification scheme is composite. Because the uniqueness constraint spans e, it must also span the attribute combination that replaces it.

Now consider the conceptual schema of Fig. 11.19. The structural difference here is that the fact type has a composite uniqueness constraint. We may initially think of it mapping to the table Drives( e , c ), where e and c are surrogates for the employee and car roles. Replacing the surrogates by the real identifiers results in the table scheme Drives( familyName, initials, carRegNr ). Because e was just part of a longer key, so is the composite identifier for employee that replaces it.

![](img/1344db3eba3d550e6edb009556fcd95c_525_0.png)

Drives( e , c )      Drives( familyName, initials, carRegNr )

FIG. 11.19 Composite primary identifier and nonfunctional fact type.

Now consider the conceptual schema of Fig. 11.20. This is like that of Fig. 11.18 except that Employee now has empNr as its primary identifier. The external uniqueness constraint now applies to two fact types rather than reference types, and hence can be mapped and enforced by the information system.

As shown, this maps to a uniqueness constraint spanning surname and initials in the relational table (ensuring each familyName, initials combination is paired with only one employee number). The uniqueness constraint on the table’s primary key, empNr, captures the three simple uniqueness constraints on the three conceptual fact types (i.e., because each empNr is unique, it is paired with only one family name, only one sequence of initials, and only one gender code).

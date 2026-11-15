For example, suppose we allowed FemaleStudent(StudentNr) and PostGradStudent (StudentNr) as direct subtypes of Person(.nr). Mapping personNr down into tables for both subtypes would create redundancy of the facts that associate personNr and studentNr for the intersection of the subtypes. So this pattern is not allowed. Instead we insert the intermediate supertype Student(.nr) as a subtype of Person(.nr) and a supertype of FemaleStudent and PostGradStudent, which now inherit their identification scheme from Student (which is used for establishing the correspondence between personNr and studentNr).

We confine our discussion here to the subtype separation option (separate tables are created for functional roles specific to each subtype) and assume that all reference schemes are simple (not composite). For each subtype with a preferred reference mode different from the root's, we define its “total table” (if any) as set out in the following total table procedure.

# Total Table Procedure:

```
if the object type has a mandatory disjunction of one or more functional roles
all of which map to the same table
then the table to which its functional roles map is its total table
else if it has a mandatory nonfunctional role
then select one of these roles arbitrarily;
the table to which this role maps is its total table
else { all roles are optional }
if the object type is independent or is a subtype with separation mapping option
then its table is the total table
else if the object type plays only functional roles or only one role
all of which map to the same table
then the table for this is its total table
else the object type has no total table.
```

The basic idea is that the total table of an object type contains its total population (i.e., it includes all instances in the population of the object type). If an object type does have a total table, this procedure will find it. In what follows, where total tables exist we basically ignore other tables of the object type (the other tables are linked by foreign keys to the primary ones in the normal way).

The root supertype table(s) is/are computed in the normal way. Copy the preferred reference of the root supertype as an extra attribute in the total table of each subtype, which “introduces” a different preferred reference scheme to the graph; if the introducing subtype has no total table, create a reference table for it (to store just the fact connecting the two identifiers for the object type’s population).

In specifying, at the relational level, subtype links between object types with different primary reference schemes, use the root reference scheme; if the object types have the same reference scheme, use this common reference scheme.
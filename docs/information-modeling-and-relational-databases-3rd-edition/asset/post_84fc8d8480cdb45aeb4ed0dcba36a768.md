
The general case is summarized in Fig. 4.39, where A, B, and C are any object types, and R and S are predicates. External UCs may apply to roles from reference types, not just fact types. This is the basis for composite reference schemes, as discussed in a later chapter.

As a more complex case, suppose persons enroll in subjects but are given subject positions (1st, 2nd, 3rd, etc.) rather than subject ratings. Each person achieves at most one position in any given subject. Moreover, no ties may occur (i.e., for each position in a subject there is only one student).

![](img/1344db3eba3d550e6edb009556fcd95c_159_0.png)

Table 4.4 Student ranking within subjects (no ties allowed).

| Person | Subject | Position |
|---|---|---|
| Adams J | CS114 | 3 |
| Adams J | CS100 | 10 |
| Adams J | PD102 | 3 |
| Brown C | CS114 | 10 |
| Brown C | PD102 | 5 |

Table 4.4 shows a sample report for this UoD. Performing step 1 on the first row, we may express the information as the ternary: Person (name) “Adams J” is placed in Subject (.Code) “CS114” at Position (.Nr) 3. This leads to the schema of Fig. 4.40. Notice the overlapping UCs.

We could instead express the information on row 1 thus: Person (name) “Adams J” enrolled in Subject (.Code) “CS114”; this Enrollment achieved Position (.Nr) 3. This leads to the nested version in Fig. 4.40(b). For this to be equivalent to the ternary, the role played by the objectified association must be mandatory.

The simple UC on the achievement predicate captures the UC spanning the first two roles in the flat version of Fig. 4.40(a). The external UC corresponds to the constraint spanning the last two roles in the flat version–each (Subject, Position) combination is unique.

![](img/1344db3eba3d550e6edb009556fcd95c_159_1.png)

So, if we _flatten_ the nested version into a ternary, then any (Subject, Position) pair occurs on at most one row of the ternary table. To help understand this, we suggest that you add the fact tables to the diagram. The fact table for the outer predicate matches the output report.

The external UC in Fig. 4.41 is a _unique-where-true constraint_, where the uniqueness applies only to those politicians who are government heads. This verbalizes as **For each Country, at most one Politician is a government head and serves on the government of that Country.**

![](img/1344db3eba3d550e6edb009556fcd95c_160_0.png)

FIG. 4.41 A unique-where-true external uniqueness constraint.

Table 4.5 Students are assigned both ratings and positions.

| Person | Subject | Rating | Position |
| :--- | :--- | :--- | :--- |
| Adams J | CS114 | 7 | 3 |
| Adams J | CS100 | 6 | 10 |
| Adams J | PD102 | 7 | 3 |
| Brown C | CS114 | 6 | 10 |
| Brown C | PD102 | 7 | 5 |

External UCs sometimes connect more than two roles. For example, a point in three-dimensional space might be associated with a unique combination of x, y, and z coordinates.

As you may gather from these examples, nesting tends to produce a more complex constraint picture. For this example, the flattened version is preferred. However, if the Position information is optional (e.g., to be added later), then the nested approach is preferred. Such modeling choices are covered in more detail later.

Another reason for nesting is to avoid embedding the same association within more than one fact type. Suppose we have to record both a rating and a unique subject position for each student taking any given subject. A sample report for this situation is shown in Table 4.5.

We might describe this UoD using two ternaries, as in Fig. 4.42. Note, however, that all (Person, Subject) combinations appearing in one fact table must also appear in the other. A later chapter shows how such a constraint may be added.

Alternatively, we may objectify the enrollment association between Person and Subject, and attach rating and position predicates to this (see Fig. 4.43). The nested approach corresponds to reading the information on row 1 of the table as Person “Adams J” enrolled in Subject “CS114”; this Enrollment scored Rating 7; this Enrollment achieved Position 3. To indicate that rating and position must be recorded, additional constraints are needed (see next chapter).

If a role has a simple, internal UC, it should not be included in an external UC. Even if a join path exists to enable an external UC to be declared, the external constraint would be implied by the stronger, simple UC; it is generally preferable to omit implied constraints.

![](img/1344db3eba3d550e6edb009556fcd95c_161_1.png)

FIG. 4.43 Another schema for Table 4.5 (nested version).

As an exercise to illustrate this point, you may wish to modify Fig. 4.36 so that student names are unique, and then show that the external constraint is implied. Before you start the section exercise, there’s one point you should be clear about. When you examine an information sample, you are seeing it at the external level. There are often many aspects of the presentation that may not be relevant to your application. In a tabular report, for example, the order of the columns or rows is not normally something that you need to model. If the information is presented in nontabular ways (e.g., diagrammatic) there are always topological and metric aspects, and possibly other aspects (e.g., color), that are represented along with basic data. Whether these additional aspects of the presentation need to be modeled is something that only the domain expert can decide. To fully appreciate this point, make sure that you attempt at least Question 2 from the following exercise.

## Exercise 4.4

1. Add the UCs to the conceptual schema diagrams for:
   (a) Exercise 3.4 Question 6   (b) Exercise 3.5 Question 4

2. Many manufactured products contain parts that may themselves be products of even smaller parts. The structure of one such product is shown:

![](img/1344db3eba3d550e6edb009556fcd95c_162_0.png)

   (a) List at least three different kinds of facts that are captured in this diagram.

   (b) Assume that we are interested in modeling only containment facts. These facts may also be displayed as a labeled tree (hierarchy) as shown. Draw a conceptual schema diagram for this UoD, including UCs, but make no use of nesting.

![](img/1344db3eba3d550e6edb009556fcd95c_162_1.png)

   (c) Draw an equivalent conceptual schema diagram that does make use of nesting.

3. A car dealer maintains a database on all the cars in stock. Each car is identified by the vehicle identification number displayed on a plate attached to the car (e.g., on its dashboard). For each car, the dealer records the model (e.g., Saturn SW2), the year of manufacture (e.g., 2006), the retail price (e.g., $18,000), and the color (e.g., dark green). Because of space limitations the dealer will never have in stock more than one car of the same model, year, and color at the same time. The dealer also keeps figures on the number of cars of a particular model and color that are sold in any given year. For example, in 2007, five dark green Saturn SW2s were sold. Draw the conceptual schema diagram, including all UCs.

## 4.5 Arity Checks

In step 1 of the CSDP, we try to express information examples in terms of elementary facts. At that stage we rely on familiarity with the UoD to determine whether a fact type is simple or compound (splitable). Once UCs are added, a formal check can be conducted. This section discusses a check based on UCs, and the next section discusses the notions of projection and join, which may sometimes be used to perform a projection-join check.

Until we are experienced at conceptual schema design, we might include some fact types that are too long or too short. “Too long” means that the arity of the fact type is higher than it should be—the predicate has too many roles. In this case, we must split the compound fact type up into two or more simple fact types. For example, the fact type Scientist was born in Country during Year should be split into two fact types: Scientist was born in Country; Scientist was born during Year.

“Too short” means the arity of some fact types is too small, resulting in a loss of information—a fact type has been split even though it was elementary. In this case, the fact types resulting from the split need to be recombined into a fact type of higher arity.

![](img/1344db3eba3d550e6edb009556fcd95c_163_0.png)

FIG. 4.44 A fact type has one or more keys.

For example, suppose that scientists may lecture in many countries in the same year. It would then be wrong to split the fact type Scientist lectured in Country during Year into the fact types Scientist lectured in Country; Scientist lectured during Year. This kind of error is rare, but serious nevertheless.

For a given fact type, a minimal combination of roles spanned by a UC is called a “key” for that fact type. “Minimal” means the UC has no smaller UC inside it; if it did, it is implied by the smaller (but stronger) constraint and hence should not be shown. Role combinations for such longer, implied UCs are called “proper superkeys”. However, as proper superkeys are not minimal, we do not count them as keys in our discussion.

Each role is associated with a column of the fact table for the fact type. Unless the fact type is unary, it is possible for it to have more than one key. Consider the cases shown in Fig. 4.44. Here, the binary has two one-role keys, the middle ternary has two two-role keys, and the other ternary has one three-role key.

The first two predicates also have implied UCs across their whole length, but these are not counted as keys for these predicates. The length of a role sequence is the number of roles it contains. A key of length 1 is a simple key. All other keys are composite.

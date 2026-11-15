
![](img/1344db3eba3d550e6edb009556fcd95c_747_0.png)

FIG. 14.44 This suboptimal schema maps to six tables.

- **Colecturing** ( topiccode, colecturer )
- **PGtopic** ( topiccode, topicTitle, headLecturer, period )
- **ActualPrerequisite** ( topiccode, actualPrereq )
- **PrefPrerequisite** ( topiccode, preferredPrereq )
- **TopicChoice** ( studentNr, subjectCode, topicCode )
- **Enrollment** ( studentNr, subjectCode )

FIG. 14.45 The relational schema mapped from Fig. 14.44.

PGtopic.topicCode (i.e., PGtopic.topicCode is the disjoint union of ActualPrerequisite.topicCode and PrefPrerequisite.topicCode). The ordinary “x” indicates that the topic-lecturer pairs in Colecturing and PGtopic are exclusive. The other constraints are straightforward.

Suppose a focused query for this domain is the following: list all topics (code and title) together with their main lecturers, co-lecturers, actual prerequisites, and preferred prerequisites. Let another focused query be the following: list students, the subjects in which they are enrolled, and the topics chosen by them (if any) for those subjects. With the relational schema of Fig. 14.45, the first query involves a join of four tables, and the second query involves a composite outer join of two tables. So, these queries will be slow to run.

![](img/1344db3eba3d550e6edb009556fcd95c_748_0.png)

FIG. 14.46 The conceptual schema obtained by optimizing Fig. 14.44.

Applying optimization steps 1 and 2 to the conceptual schema of Fig. 14.44 results in three main changes, as shown in Fig. 14.46.

Step 1.2 generalizes the two prerequisite binaries to a ternary by extracting the object type PrereqKind {"actual", "preferred"}. Step 1.3 uses the overlap algorithm to nest the enrollment and topic fact types. Step 2.1 specializes the colecturer predicate into two exclusive binaries simply keyed on Topic. If we also demand that a topic has colecturer2 it must have a colecturer1, then this may be added as a subset constraint. As an exercise, Remap the schema in Fig. 14.46, then check your solution with that shown in Fig. 14.47.

```
PGtopic ( topicCode, topicTitle, period, headLecturer, [colecturer1], [colecturer2] )
{ sem1, sem2, yr }
Prerequisite ( topicCode, subjectCode, prereqKind )
{actual, preferred}
Enrollment ( studentNr, subjectCode, [topicCode] )
```

FIG. 14.47 The relational schema mapped from Fig. 14.46.

The optimized relational schema has just three tables: one for the ternary, one for the nesting, and one for the five functional binaries of Topic. The "≠" symbol means that on the same row, any nonnull values for headLecturer, colecturer1, and colecturer2 must differ. This relational schema leads to much faster execution of the focused queries as well as simpler constraint enforcement on updates.

We now consider the final steps (3, 4, 5) in the optimization procedure. Unlike the previous steps, these do not reduce the number of tables. Step 3 is set out in Fig. 14.48. This aims to reduce self-joins and is called the table width guideline (TWG) because it indicates when a wider table (more columns) may be preferable.

The schema equivalence illustrated was considered earlier. If the object type A plays a functional role, the transformation to binaries would have already occurred in the last phase of step 2.1. Even if A has no functional role, the specialization into binaries may still be worthwhile if it avoids self-joins in focused queries.

![](img/1344db3eba3d550e6edb009556fcd95c_749_0.png)

Each S<sub>i</sub> corresponds to R where B = b<sub>i</sub>,

- 3 For the ternary pattern above, if focused queries on R require comparisons between different tuples, and the values b<sub>1</sub>,..., b<sub>n</sub> are few and fairly stable, then absorb B, specializing R into n functional binaries.

FIG. 14.48 Optimization step 3: the table width guideline.

As an example of step 3, suppose we wish to see how full-time university fees varied for various degrees over the triennium 2021–2023. Let’s model this with the ternary Degree in Year had FulltimeFee with a uniqueness constraint spanning the first two roles, a frequency constraint of 3 on the first role, and a value constraint of {2021...2023} on Year’s role, as shown in Fig. 14.49. Suppose we map this to the relational schema FulltimeFee ( degree, feeYear, Fee ), with the frequency and value constraint enforced at the relational level.

A fragment of a sample population for this table is shown in Fig. 14.49. Let a sample focused query be, How much did the BS full-time fee increase over the triennium? Answer this query yourself by inspecting the table.

| degree | feeYear | fee |
|---|---|---|
| BS | 2021 | 5000 |
| BS | 2022 | 5000 |
| BS | 2023 | 5500 |
| MBA | 2021 | 7000 |
| MBA | 2022 | 7300 |
| MBA | 2023 | 7700 |

![](img/1344db3eba3d550e6edb009556fcd95c_749_1.png)

How much did the BS degree fulltime fee increase over the 3 years?

```
SQL code for query: select New.fee - Old.fee
from FullTimeFee as Old cross join FullTimeFee as New
where Old.feeYear = 2021 and Old.degree = 'BS' and
New.feeYear = 2023 and New.degree = 'BS'
```

FIG. 14.49 This query requires a self-join because it compares different rows.

Such joins can be avoided by first transforming the schema via TWG. Applying a variant of PSG1 where the value constraint applies to a role instead of an object type, the ternary specializes to the three conceptual binaries: Degree had 2021- FulltimeFee; Degree had 2022- FulltimeFee; Degree had 2023- FulltimeFee.

Here, the roles of Degree are functional and linked by an equality constraint. If, in the global schema, fee information is mandatory for Degree, these roles are mandatory (which implies the equality constraint). If Degree has no other functional roles, these three conceptual binaries map to a single table: FulltimeFee ( degree, fee2021, fee2022, fee2023 )

If Degree had other functional roles, the optimization would have been performed at step 2.1, with the extra functional fact types mapping to the same table.

Fig. 14.50 shows the conceptual schema, and also illustrates how the wider table enables the query to be performed simply by comparing values on the same row, which is much easier than the previous query.

![](img/1344db3eba3d550e6edb009556fcd95c_750_0.png)

| degree | fee2021 | fee2022 | fee2023 |
|---|---|---|---|
| BS | 5000 | 5000 | 5500 |
| MBA | 7000 | 7300 | 7700 |

How much did the BS degree fulltime fee increase over the 3 years?

```
SQL code for query: select fee2023 - fee2021
from FullTimeFee
where degree = 'BS'
```

FIG. 14.50 The transformed schema leads to a more efficient query.

This example was trivial and clear-cut, but life is not always so simple. If the fee year range is large, the number of extra columns generated by the transformation may be too high. For example, suppose that we must record fees for the period 1984...2023. Specializing the ternary would generate 50 binaries and lead to a relational table with 51 columns: FulltimeFee( degree, fee1984, ..., fee2023 ).

Such a large number of binaries would clutter the conceptual schema (although a flexible CASE tool could be set to display the ternary with the optimization hidden in the mapping). The very wide relational table would also be awkward to view (lots of horizontal scrolling) and to print. For these reasons, once the cardinality of the value constraint exceeds a reasonable number (e.g., 5), the ternary fact type might well be preferred.

The stability of the value constraint is also important. In many cases, such a constraint is known to be stable (e.g., {"m", "f"} for gendercode). Sometimes, however, the value constraint changes with time. For example, suppose fees are to be recorded for all years from 2001 to the current year, or for just the most recent triennium. The binary approach

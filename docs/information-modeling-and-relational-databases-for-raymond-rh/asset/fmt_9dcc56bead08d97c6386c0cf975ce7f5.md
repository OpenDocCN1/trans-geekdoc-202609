
## Denormalization and Low-Level Optimization

If the normalized, two-table design has poor performance, we might denormalize the design to a single table that is their natural join, as shown in [Fig. 14.74](#Ch014_681-771_B9780443237904000189.xhtml#f0375)(b). With the subset constraint of [Fig. 14.71](#Ch014_681-771_B9780443237904000189.xhtml#f0360)(a) replaced by an equality constraint, assignment facts can be retrieved by projecting on the first two roles of the ternary, but the uniqueness constraint on the assignment binary still needs to be catered for. In the denormalized ternary, this constraint cannot be enforced as a uniqueness constraint, so a separate constraint is required to enforce the FD `lecturer → course`. As long as this additional constraint is enforced (e.g., as a user-defined constraint in SQL), the single-table design is safe. As before, the alternate key constraint is implied and hence omitted.

Advances in relational languages are making it easier to specify constraints such as FDs that are not key based. However, the overhead of enforcing such constraints needs to be factored in when choosing the final relational design. In general, we should first try a fully normalized design, using conceptual optimization where relevant to improve it. If performance is still unacceptable, controlled denormalization is an option.

## Exercise 14.6

1. The conceptual schema for a given UoD is as shown. Some table schemes designed by novices for parts of this UoD are listed here. Indicate briefly, in terms of normalization theory, why each of these table schemes is not fully normalized.

    1. (a) `Parenthood` ( `parentName`, `gender`, `Child`( `childName`, `gender` ))

    2. (b) `Teaches` ( `person`, `subjectTutored`, [`subjectLectured`] )

    3. (c) `ParentOf` ( `parent`, `child`, `genderOfParent`, `genderOfChild` )

    4. (d) `Tutor` ( `tutorName`, `subject`, [`child`] )

    5. (e) Use Rmap to generate a correct relational schema.

    ![](images/B9780443237904000189/u14-11-9780443237904.jpg)

2. 
    1. (a) The conceptual schema of Question 1 is incomplete with respect to real-world constraints. For example, parents of the same child must differ in gender, but this constraint is not captured. Replace the parent predicate with mother and father predicates to develop a more complete schema that includes this constraint (Hint: include subtyping).

    2. (b) Rmap your solution to (a).

3. Suppose that while developing a conceptual schema, you specify the following fact type: Manager supervises Trainee on Project. Assume that no manager is a trainee, and that all objects are simply identified by name. The following constraint applies: no manager may supervise the same trainee on more than one project.

    1. (a) Draw this as a ternary fact type, including the constraint.

    2. (b) You now check whether there are any other functional fact types of interest between these object types, and discover that each manager supervises at most one project. Add this fact type to your schema and then add any set-comparison constraint that applies.

    3. (c) Is the ternary elementary? If not, explain why not, and correct the schema.

    4. (d) Rmap your answer to (d).

    5. (e) Because of poor performance, this relational schema is regarded as unsatisfactory. Using controlled denormalization, suggest an alternative relational schema.

    * The following business rule is now added: each trainee on a given project has only one supervisor for that project. Add this constraint to your schema.

## 14.7 Denormalization and Low-Level Optimization

Applying the conceptual optimization procedure followed by the Rmap procedure ensures a redundancy-free relational schema that should be reasonably efficient. To test the performance of this logical schema, it should be implemented as an internal schema on the target DBMS, using a realistic population. At this stage, `indexes` should normally be created for all primary and foreign keys as well as any other columns that play a significant role in focused queries.

For large tables, indexes can dramatically improve performance because they can normally be loaded, in part or whole, into main memory and their entries are sorted into structures that permit fast retrieval (e.g., binary trees). At times, indexes may slow down updates because they must be updated when relevant changes are made to the base tables, but even with updates, indexes can speed up many kinds of constraint checking (e.g., ensuring that keys are unique). There are many kinds of indexes (e.g., clustered, nonclustered), and indexing schemes often differ among vendors.

To speed up or facilitate certain complex queries, `working tables` (either predeclared or ad hoc) may be used (e.g., to hold intermediate results, perhaps obtained by joining several tables, which might be reused several times before the base values are updated). Predeclared working tables are populated at the start of a session to hold intermediate results that may be treated as stable for the session; these temporary tables are dropped at the end of the session. Ad hoc working tables are similar, but are created during a session and may be dropped before the end of the session as soon as they are no longer needed.

Another popular option is to use `materialized views`—these are views that are populated automatically with data according to their definition, and updated automatically as needed when their base tables are updated. Support for materialized views varies with the DBMS; in SQL Server, they are called indexed views.

Different DBMSs offer other means of tuning the internal schema (e.g., clustering the storage of related data). In addition, because no query optimizer is perfect, the form of the actual query itself can impact (sometimes seriously) on the performance. With some older optimizers, merely changing the order in which tables are listed in a join condition can cause significant changes in the response time. In most cases, you can use the performance tuning assistance provided by the DBMS to compare execution plans and select the best alternative.

If the data has been prechecked for integrity, consider deactivating constraint checking when performing bulk updates (e.g., loading a data warehouse from operational databases). You might also delay expensive constraint checking until after performing a bulk update. Although most database applications can be developed completely in 4GLs, consider writing some modules in a 3GL (e.g., C#) to speed up critical aspects or to achieve better control (e.g., checking acyclic constraints is usually faster in a 3GL than using recursive union in SQL).

For a few specific applications, a relational DBMS system might not be able to give the desired performance, and a different kind of DBMS might be needed (e.g., an object database).

Because realistic applications typically require data updates by users to be performed via an external interface (e.g., screen forms) rather than directly on the base tables, it needs to be decided how much constraint checking will be done at the table level and how much at the form level. With client-server networks, we need to decide how much work is done at the client end and how much at the server end. Constraints are often implemented both at the user interface and at the DBMS.

Implementing constraints on screen forms can detect data entry errors as early as possible. Implementing constraints on the DBMS ensures that they are checked regardless of the user interface. With noncentralized database systems, great care is needed in deciding how to replicate data to reduce communication overheads. A proper discussion of these issues is beyond the scope of this book.

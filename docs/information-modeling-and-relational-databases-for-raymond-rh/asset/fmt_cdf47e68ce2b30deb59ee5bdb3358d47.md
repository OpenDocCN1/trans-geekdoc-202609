
# Reengineering Process Overview

Much of the reengineering process can be automated, especially if a very detailed database schema is provided at stage 1. However, human interaction is also required to ensure a complete and elegant result. While our discussion is limited to the logical and conceptual levels, reengineering an application involves work at the external level (e.g., revising the user interface) and physical level (e.g., retuning) as well.

## Worked Example: Four Reengineering Stages

The four basic reengineering stages are now illustrated with a worked example. As the main input to the process, [Fig. 14.78](#Ch014_681-771_B9780443237904000189.xhtml#f0395) shows a relational schema as well as two rows of data for each table (shown as tuples on the right to save space).

![Fig. 14.78 The original database schema and some sample data.](images/B9780443237904000189/f14-78-9780443237904.jpg)

[Fig. 14.78](#Ch014_681-771_B9780443237904000189.xhtml#B-f0395) The original database schema and some sample data.

Suppose this design is used to record details about a 1-day computer conference, but its performance is poor mainly because of the number of table joins required for common queries.

Moreover, application developers find parts of the schema awkward or even unsafe. For example, the `budget` column in the `Committee` table applies to the committee as a whole, not to a particular chairperson of that committee (each committee has at most two chairpersons). It is suspected that this is not the only unnormalized feature of the tables.

Because of your expertise in conceptual modeling, you are hired to provide a conceptual model of the application so that a clear and complete picture of the business domain is available. Moreover, you are asked to provide a new relational design that is both normalized and efficient, if this is possible.

In practice, reengineering usually requires dialog with the domain expert to clarify the UoD, especially to identify missing constraints. To help you try the reverse engineering phase yourself, uniqueness, value, exclusion, and frequency constraints are depicted. However, other constraints are omitted (e.g., subset constraints, and nonimplied FDs due to denormalization). Some missing constraints are "obvious" and others may be identified from the brief description that follows.

Also, the sample rows of data enable you to apply CSDP step 1. These rows do not provide a significant, or even a legal, population (e.g., if the database were composed of only these data, subset constraints between the tables would be violated).

Abbreviated codes have the following meanings: `Prog` = Programming; `Org` = Organizing; `undec` = undecided; `tbl` = table; `fig` = figure; `lec` = lecture; `lab` = laboratory. Authors submit papers that are then sent to referees to be rated. The method for determining which papers are accepted is not modeled here.

Various statistics (number of pages, tables, and figures) may be kept about accepted papers, partly to help with publication of the conference proceedings. If statistics are kept for a paper, all three numbers must be recorded.

An accepted paper may be presented by one or more of its authors at the conference. Which authors present the paper might be unknown until after the paper is accepted. The conference program includes slots to which accepted papers are eventually allocated. Each slot is of 1 hour duration. Time is measured in military hours (e.g., `14` = 2 p.m.). To allow more papers on the same day, two streams (A and B) may be run in parallel (so two paper slots may have the same time).

A room directory is used to help assign slots to rooms; room area is in square meters. Only lecture rooms or laboratories may be used for paper presentations. The number of seats is recorded just for lecture rooms, and the number of PCs is recorded just for laboratories. Before peeking at the solution, try to provide a conceptual schema for this application. Include all constraints (including those missing from the original relational schema). In doing this, it will become apparent that some of the tables have redundancy problems. Which tables are these?

Compare your solution with the one provided in [Fig. 14.79](#Ch014_681-771_B9780443237904000189.xhtml#f0400). Give yourself a pat on the back if you got all the constraints.

![Fig. 14.79 The conceptual schema resulting from reverse engineering.](images/B9780443237904000189/f14-79-9780443237904.jpg)

[Fig. 14.79](#Ch014_681-771_B9780443237904000189.xhtml#B-f0400) The conceptual schema resulting from reverse engineering.

The table grouping differs from what Rmap would generate, for example, the two Committee fact types are wrongly grouped into the same table, even though one of them is nonfunctional. As a result, the original `Committee` table is open to redundancy problems with facts of the type Committee has budget of MoneyAmt. Similarly, the `Authored` table exhibits redundancy by including facts of the type Paper has PaperTitle. So, the original design denormalizes the relational schema in an uncontrolled way.

Although the ORM schema looks complicated, the conceptualization clarified the UoD, for example, the semantics of the `PaperSlot` table are easier to understand on the ORM schema. Now that the detailed semantics are displayed graphically, we are in a better position to explore optimization possibilities in a controlled manner.

## Conceptual Optimization Phase

As the second phase of reengineering, use the conceptual optimization procedure to transform the conceptual schema into one that Rmaps to a more efficient relational schema. Compare your solution with [Fig. 14.80](#Ch014_681-771_B9780443237904000189.xhtml#f0405). The specialization of the chairperson and diagram predicates into functional binaries is straightforward.

![Fig. 14.80 The optimized conceptual schema.](images/B9780443237904000189/f14-80-9780443237904.jpg)

[Fig. 14.80](#Ch014_681-771_B9780443237904000189.xhtml#B-f0405) The optimized conceptual schema.

In nesting the referee and author predicates, we could instead have united these exclusive but compatible predicates. Although this alternative move would lead to one less table, nesting these exclusive predicates would detract from the readability and lead to awkward constraint patterns.

Even the nesting in [Fig. 14.80](#Ch014_681-771_B9780443237904000189.xhtml#f0405) leads to awkward verbalization. The original flattening into four predicates seems more natural than the two nestings. Ideally, a CASE tool would allow the modeler to choose the flattened display for clarity, with the option of nesting in a hidden, preprocessing stage to the standard mapping.

## Relational Mapping Phase

The next stage is to map the optimized conceptual schema to a new relational schema. As an exercise, try this yourself before looking at the solution in [Fig. 14.81](#Ch014_681-771_B9780443237904000189.xhtml#f0410). Notice that the final relational schema contains just seven tables (compared with the 12 original tables), is fully normalized, and captures all the original constraints as well as those that were missing from the original.

![Fig. 14.81 The final relational schema.](images/B9780443237904000189/f14-81-9780443237904.jpg)

[Fig. 14.81](#Ch014_681-771_B9780443237904000189.xhtml#B-f0410) The final relational schema.

## Data Migration Phase

Finally, the data migration is performed. The main aspect of this conversion involves defining the new relation types in terms of the original ones. Once this is done, the data migration can be performed automatically. [Fig. 14.81](#Ch014_681-771_B9780443237904000189.xhtml#f0410) displays one row of converted data for each of the new tables.

# Exercise 14.8

1. The following relational schema was designed to record details about academics and subjects, but its performance is poor, mainly because many joins are needed for common queries. Also, developers find the `Academic` table and its qualified constraint to be awkward to think about. This constraint says that on each row of the `Academic` table, there is exactly one nonnull value in the last three columns.

schematize with a single ternary fact type. Evaluate this approach, and draw a correct conceptual schema.

| Executive | Work phone | Home phone |
| :--- | :--- | :--- |
| Adams A | 4235402 | 5837900 |
| Adams A | 4235444 | |
| Adams S | 4235444 | 5837900 |
| Brown T | 4235300 | 7578051 |

4. The following table contains data about some moons in our solar system.

| Moon | Planet | Orbital period (days) |
| :--- | :--- | :--- |
| Callisto | Jupiter | 16.7 |
| Deimos | Mars | 30.0 |
| Phobos | Mars | 0.3 |

+   (a) Schematize this as a ternary. Is this okay?
+   (b) Schematize this using nesting. Is this okay?
+   (c) Schematize this using only simple binaries. Is this okay?

5. The following table contains information about movie exports. Suppose we model this with the quaternary Movie exported from Country to Country achieved SalesLevel. Draw the schema for this approach. Is this acceptable? If not, explain why.

| Movie | Origin | Country | Sales level |
| :--- | :--- | :--- | :--- |
| Backdraft | US | AU | High |
| | | NZ | Low |
| | | GB | Medium |
| Crocodile Dundee | AU | NZ | Low |
| | | US | High |
| Terminator 2 | US | ? | ? |

# ## 4.6 Projections and Joins

The previous section showed that a sufficient condition for splitting an unnested fact type is that it has a UC spanning fewer than n – 1 roles. Because this is not a necessary condition for splitting, in some cases further analysis is required to make a definite decision. At the heart of such an analysis is the question, Can the fact type be rephrased as a conjunction of smaller fact types?

With a bit of experience behind us, we can usually answer this question fairly quickly. This section discusses a formal procedure for addressing this question in a systematic way. The procedure makes use of two operations known as “projection” and “join”, which are important in relational database work. The join operation has already been discussed, and involves combining tables by matching values referencing the same object to form a new table (review Section 4.4).
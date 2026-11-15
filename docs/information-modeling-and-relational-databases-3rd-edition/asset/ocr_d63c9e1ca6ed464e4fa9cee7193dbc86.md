![](bbox=[0.168, 0.102, 0.856, 0.195])

FIG. 9.23 All constraints are now shown explicitly in (a) UML and (b) ORM.

![](bbox=[0.256, 0.276, 0.76, 0.344])

FIG. 9.24 The relational schema mapped from Fig. 9.23.

Some ORM tools can detect the misleading nature of constraint patterns like that of Fig. 9.22(b) and ask you to resolve the problem. Human interaction is the best policy here because there is more than one possible mistake (e.g., is the subset constraint correct leading to Fig. 9.23, or is the optional role correct resulting in Fig. 9.21?).

If a schema in Fig. 9.23 is mapped to a relational database, it generates a referential cycle because the mandatory fact types for Committee map to different tables (so each committee must appear in both tables). The relational schema is shown in Fig. 9.24 (arrows show the foreign key references, one simple and one composite, which correspond to the subset constraints).

Referential cycles are sometimes unavoidable, but are awkward to implement. In this case, the cycle arose because of the pair-subset constraint combined with the mandatory role constraint on is-chaired-by. Given the pair-subset constraint, the cycle would also apply if Committee is independent or plays another mandatory, functional role. Relational mapping is covered in detail in Chapter 11.

Because UML does not allow unary relationships, subset constraints between ORM unaries need to be captured textually, using a note to specify an equivalent constraint between Boolean attributes. For example, the ORM subset constraint in Fig. 9.25(b), which verbalizes as **Each Patient who smokes is cancer prone**, may be captured textually in UML by the note in Fig. 9.25(a).

UML 2 introduced a *subsets property* modifier to indicate that for each instance that is the context for a property (an attribute or association role), the population (extension) of that property for that instance must be a subset of the population of another compatible property for that instance. For example, adorning the citizen role in Fig. 9.26(a) with {subset resident} means that each citizen of a country is a resident of the same country. Fig. 9.26(b) shows the equivalent ORM schema.
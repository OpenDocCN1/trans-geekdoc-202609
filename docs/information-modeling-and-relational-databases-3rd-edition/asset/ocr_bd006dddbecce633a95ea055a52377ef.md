The pair-exclusion constraint in Fig. 9.33(b) can be expressed in UML by a note connected by dotted lines to the two associations, as shown in Fig. 9.33(c). Alternatively, one could attach a textual constraint to the Person class (e.g., “bookAuthored and bookReviewed are disjoint sets”) or the Book class (e.g., “author and reviewer are disjoint sets”), but the choice of class is arbitrary.

UML has no graphical notation for exclusion between attributes, or between attributes and association roles. An exclusion constraint in such cases may often be captured as a textual constraint. For example, in Fig. 9.34(a), the exclusion constraint that each employee is either tenured or is contracted until some date may be captured by the textual constraint shown.

![](bbox=[0.2, 0.31, 0.82, 0.51])

FIG. 9.34 An exclusion constraint modeled in (a) UML and (b) ORM.

Here, the constraint is specified in OCL. The expressions “->isEmpty()” and “->notEmpty()” are equivalent to “is null” and “is not null” in SQL. Fig. 9.34(b) depicts the exclusion constraint graphically in ORM. There are other ways to model this case in UML (e.g., using subtypes) that offer more chances to capture the constraints graphically.

# 9.6 Subtyping

Both UML and ORM support subtyping using “is-a” semantics, where each instance of a subtype is also an instance of its supertype(s). For example, declaring Woman to be a subtype of Person entails that each woman is a person, and hence Woman inherits all the properties of Person. Given two object types, A and B, A is a subtype of B if, for each database state, the population of A is included in the population of B. For data modeling, the only subtypes of interest are proper subtypes. We say that A is a proper subtype of B if and only if A is a subtype of B, and there is a possible state where the population of B includes an instance not in A. From now on, we’ll use “subtype” as shorthand for “proper subtype”.

In both UML and ORM, specialization is the process of introducing subtypes, and generalization is the inverse procedure of introducing a supertype. Both UML and ORM allow
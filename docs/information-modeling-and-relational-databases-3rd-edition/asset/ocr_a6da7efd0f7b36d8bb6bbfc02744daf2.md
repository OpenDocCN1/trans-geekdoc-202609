![](bbox=[0.135, 0.095, 0.835, 0.205])

FIG. 14.41 A functional, coreferenced case; (a) is generally preferable to (b).

Fig. 14.41(a) is generally preferable to Fig. 14.41(b) for two reasons. First, it facilitates schema changes that add other facts about rooms (e.g., Room has Size(m²:)). Second, it is natural to think in terms of rooms, and the composite identification scheme is clearly displayed. In general, don’t eliminate an entity type unless you feel that no further details will be recorded for it and that no clarity is lost by its removal.

If you do decide to eliminate a compositely identified entity type, ensure that it is the target of only functional predicates. For example, Fig. 14.41(a) includes the fact type Employee works in Room. Suppose we now make this association m:n to cater for some unusual case where an employee may have more than one office. For example, if an employee has to move his/her office from one building to another, he/she may be assigned an office in each building to facilitate working efficiently in both places until the move is completed. It would now be wrong to eliminate Room as in Fig. 14.41(b) because the two associations are now m:n, losing the information about which room number goes with which building.

That covers the main conceptual schema transformations of practical relevance in information modeling. Other transformations exist, but we have no space to discuss them here. Some transformations that deal with compound (nonelementary) fact types are discussed later in the context of denormalization and nonrelational mappings.

# Exercise 14.4

+   1. (a) Each employee uses one or two phone numbers, and each phone number is used by an employee. Each phone number is classified as a work phone or home phone. No employee can have two phone numbers with the same classification. Schematize this using the following entity types: Employee, PhoneNr, and PhoneType.
+   (b) Provide an alternative schema by absorbing PhoneType.
+   (c) Now suppose that some phones might not be used by any employee. Modify your answer to (a) accordingly.
+   (d) Provide an alternative schema by specializing the uses fact type.

+   2. (a) Consider the fact types Person is of Gender {‘m’, ‘f’}; Person is a parent of Person. Each person’s gender is recorded. Parents of the same child must differ in gender. Some people might not be recorded as a parent or child. Schematize this.
+   (b) Set out an alternative schema by specializing the parenthood fact type.
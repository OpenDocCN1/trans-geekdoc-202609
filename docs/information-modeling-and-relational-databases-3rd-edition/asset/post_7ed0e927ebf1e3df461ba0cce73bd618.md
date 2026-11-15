
![](img/1344db3eba3d550e6edb009556fcd95c_270_0.png)

### FIG. 6.38 An incomplete conceptual schema for Table 6.4.

Notice the optional roles. Although correct as far as it goes, this schema fails to express the constraints that prostate status is recorded only for male patients, and the number of pregnancies is recorded just for the females. The phrase “just for” means “for and only for” (i.e., “for all and only”). To capture these constraints, we introduce subtypes and attach their specific roles, as shown in Fig. 6.39.

The subtypes MalePatient and FemalePatient are marked with an asterisk “*” to indicate that they are derived subtypes (i.e., they are derived by applying a derivation rule to their supertype(s)).

The derivation rules appear as formal subtype definitions beneath the diagram. By default, subtypes inherit the identification scheme of their supertype, so there is no need to repeat it here.

Recall that a role is played only by instances of the object type to which the role is attached. Hence, the subtyping reveals that prostate status is known (to the information system) only if the patient is male, and pregnancy count is known only if the patient is female. The role attached to MalePatient is optional. Not all men need to have their prostate status recorded.

However, the role attached to FemalePatient is mandatory. So, pregnancy count is recorded if the patient is female. The combination of the subtype constraint and the mandatory role on FemalePatient means that a pregnancy count is recorded if and only if the patient is female.

![](img/1344db3eba3d550e6edb009556fcd95c_270_1.png)

- Each MalePatient is defined as a Patient who is of Gender ‘M’.
- Each FemalePatient is defined as a Patient who is of Gender ‘F’.

### FIG. 6.39 Subtyping completes the conceptual schema for Table 6.4.

In this case, the MalePatient subtype plays only one role, and this is optional. Unlike primitive entity types, there is no default assumption of mandatory if only one role is attached to a subtype. With subtypes, any mandatory role constraints must be explicitly shown (including disjunctive cases).

A subtype with no specific roles attached is said to be an *inactive subtype*. For example, MalePatient and FemalePatient subtypes might be introduced merely for taxonomy purposes as a way to display that patients can be classified in this way. In ORM, we rarely use inactive subtypes, as it is usually better to simply display such a classification scheme as a binary fact type with a value constraint (e.g., Fig. 6.39 uses Patient is of Gender {"M", "F"}) or as unaries (e.g., isMan and isWoman may be attached to Patient as exclusive, disjunctively mandatory unaries). The binary form is much neater when the classification scheme involves several subtypes.

While specific fact types are attached to the relevant subtype, common fact types are attached to the supertype. In this example, name, gender, and phone details may be recorded for any patient, so are attached directly to Patient. In general, each subtype inherits all the roles of its supertype(s). Although drawn outside its supertype, the subtype is totally contained inside the supertype. In Fig. 6.39, all instances of MalePatient or FemalePatient have their name, gender, and possibly phone number recorded. Attaching a common fact type to the supertype avoids duplicating it on all the subtypes.

To determine membership of derived subtypes, each derived subtype must be defined in terms of at least one role played by its supertype(s). With the present example, the gender fact type is used to determine membership in MalePatient and FemalePatient. The subtype definitions are formal—they are not just comments.

The operator “is a” or “is an” is used for “is defined as”, and “who” or “that” is used after the supertype name. For persons, “who” sounds more natural than “that”. The quantifier “Each” normally precedes the name of the subtype being defined, as shown in Fig. 6.39. Here, each MalePatient is a Patient but because derived subtypes must be well defined, this “is a” connection must be qualified in some way. For example, Each MalePatient is a Patient who is of Gender ‘M’. Subtyping provides a means of qualifying an optional role, a simple set-comparison constraint.

Subtyping may also be used instead of unqualified, simple set-comparison constraints, especially if the subtype plays many specific roles. Consider a UoD where each employee drives cars or catches buses but not both. Cars or buses are recorded for all employees, bus allowance is recorded just for the bus catchers, and driver’s license numbers are recorded only for the drivers. This can be modeled without subtypes, using exclusion, equality, and subset constraints. As an exercise, draw the schema for this and then try a subtyping solution.

Different subtyping approaches are possible. One solution is to specify the fact type Employee drives Car and then introduce the subtypes Driver (Employee who drives some Car) with the license predicate attached and NonDriver (Employee who drives no Car) with both bus caught and bus allowance predicates attached. The more subtype-specific information required (e.g., total distance traveled by bus, driving violations), the tidier the subtyping portrayal becomes in comparison to the no-subtyping alternative. Note, however, that subtyping cannot replace composite set-comparison constraints (between sequences of two or more roles).

Be careful to avoid circular definitions—don’t try to define a subtype in terms of itself. For example, suppose we defined BusCatcher as Employee who catches some Bus and then attached the bus predicate to this subtype (i.e., BusCatcher catches Bus). This specifies that the role of catching a bus is played only by those who play the role of catching a bus. Such circular reasoning is not very informative! In very rare cases, a role used to define a subtype may be a reference role. For example, we might record some property only for people whose surname begins with “Z”.

For the schema of Fig. 6.39, the subtypes MalePatient and FemalePatient are mutually exclusive and collectively exhaustive. When these two conditions are met, the subtypes are said to form a partition of their supertype. We may display this situation on a hypothetical Euler diagram, as shown in Fig. 6.40(a). This is analogous to the process of partitioning or slicing a pie or pizza into pieces, as shown in Fig. 6.40(b). The pieces don’t overlap (mutual exclusion), and all the pieces together make up the whole pizza (collective exhaustion).

Our understanding of the subtype names “MalePatient” and “FemalePatient” helps us to “see” a partition. But such names are only character strings to the computer system, so how is the partition formally captured in the model?

Look back at Fig. 6.39. The mutual exclusion between MalePatient and FemalePatient is implied by their definitions, together with the uniqueness constraint on the gender predicate (Each Patient is of at most one Gender). The constraint that MalePatient and FemalePatient exhaust Patient is implied by the subtype definitions, the {“M”, “F”} constraint, and the mandatory role on the gender predicate (Each Patient is of at least one Gender). Because ORM demands that derived subtypes be well defined and all relevant constraints on defining predicates be declared (graphically or textually), any exclusion or exhaustion constraints on derived subtypes are always implied.

As humans, we can use our understanding of meaningful subtype names to “see” whether subtypes are exclusive or exhaustive. This shortcut depends on a judicious choice of subtype names. For example, if we unwisely chose the subtype names “Man” and “Woman” to partition the Patient type, the exhaustion constraint would not apply in a UoD that includes child patients or adult people who are not patients.

For clarity, it is usually best to display subtype exclusion and exhaustion constraints explicitly, even if these are implied. With complex subtype graphs, the explicit display of such implied constraints can make the diagram cluttered. Ideally, a computer-aided software engineering (CASE) tool should enable the display of such constraints to be toggled on or off.

![](img/1344db3eba3d550e6edb009556fcd95c_272_0.png)

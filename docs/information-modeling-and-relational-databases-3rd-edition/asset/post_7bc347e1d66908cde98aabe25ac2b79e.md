
After the first event pop(Country) changes from { } to {US, JP}, and pop(CountryCode) changes from { } to {"US", "JP"}. Assuming the universe of discourse (UoD) is just about the Olympics, the entity type Country is the set of all countries that might possibly compete in the Olympic Games.

A predicate occurs within an elementary fact type or reference type (a.k.a. existential fact type). Reference types are usually abbreviated as a parenthesized reference mode. Roles in a reference type are called referential roles. Roles in an elementary fact type are called “fact roles”. Each entity type in a completed conceptual schema plays at least one referential role and, unless it is declared independent (see Section 6.3), at least one fact role. In general, the population of an entity type equals the union of the population of its roles. Unless the entity type is independent, its population is the union of the populations of its fact roles.

For example, the populated schema in Fig. 5.3 indicates the size (in square kilometers) and carbon dioxide emissions (as a percentage of worldwide emissions) of some countries as measured in 2020. The Country entity type might include many countries (e.g., from Afghanistan to Zimbabwe), but this state of the database lists only four countries. Each instance in the database population of Country plays the role r1, r2, or both. So, the current population of Country is the set of all the instances referenced in either the r1 column or the r2 column.

```
We could set this out as:
pop(Country) = pop(r1) ∪ pop(r2)
= {AU, FR, US} ∪ {AU, CN, US}
= {AU, CN, FR, US}
```

Here, “∪” is the operator for set union. The union of two sets is the set of all the elements in either or both. For instance, {1,2} ∪ {2, 3, 4} = {1, 2, 3, 4}. In the case just given, Australia and the United States occur in both role populations while China and France occur in only one.

![](img/1344db3eba3d550e6edb009556fcd95c_185_0.png)

## 5.2 Mandatory and Optional Roles

Consider the output report of Table 5.1. Patients are identified by a patient number. The question mark “?” denotes a null, indicating that an actual value is not recorded. For instance, patient 002 may have a phone but it is not recorded, or he/she may simply have no phone. Different patients may have the same name and even the same phone number, so the table population is not significant.

We must record each patient’s name, but it is optional to record a phone number. Fig. 5.4 shows a preliminary conceptual model for this situation. Conceptual facts are elementary, so they cannot contain nulls. The null in Table 5.1 is catered for by omitting a fact for patient 002 in the fact type Patient has PhoneNr.

In step 5 of the design procedure, each role is classified as mandatory or optional. A **role is mandatory** if and only if, for all states of the database, the role must be played by every member of the population of its object type; otherwise, the role is **optional**. A mandatory role is also called a *total role* because it is played by the total population of its object type.

### Table 5.1 Details about hospital patients.

| Patient Nr | Patient Name | Phone |
|---|---|---|
| 001 | Adams C | 2057642 |
| 002 | Brown S | ? |
| 003 | Collins T | 8853020 |

![](img/1344db3eba3d550e6edb009556fcd95c_186_0.png)

### FIG. 5.4 A populated schema for Table 5.1.

Which of the four roles in Fig. 5.4 are mandatory and which are optional? If the diagram includes all the fact types for the universe of discourse (UoD), and its sample population is significant, we can easily determine which roles are mandatory.

In practice, however, we mostly work with subschemas rather than the complete, or global schema; and sample populations are rarely significant. In such cases, we should check with the domain expert as to whether the relevant information must be recorded for all instances of the object type (e.g., must we record the name of each patient?).

Consider the two fact roles played by Patient. For the database state shown, the populations of these roles are {001,003} and {001,002,003}. If these are the only fact roles of Patient, then pop(Patient) = {001, 002, 003}. The role of having a name is played by all recorded patients, and the role of having a phone number is played by only some.

![](img/1344db3eba3d550e6edb009556fcd95c_187_0.png)

### FIG. 5.5 Mandatory role constraint shown as a dot at either end of the role line.

- Mandatory: Each Patient has some PatientName.
- Unique: Each Patient has at most one PatientName.
- Each Patient has at most one PhoneNr.

Assuming the population is significant in this regard, the name role is mandatory and the phone number role is optional.

To indicate explicitly that a role is mandatory, we add a **mandatory role dot** to the line that connects the role to its object type. This dot may be placed at either end of the role line. In Fig. 5.5(a), the dot is placed at the object type end. This reinforces the _global_ nature of the constraint in applying to the object type’s population. If we add a patient instance to the population of a mandatory Patient role, we must also include this instance in the population of each other role declared mandatory for Patient.

In this sense, a mandatory role constraint can have an impact beyond its predicate. In contrast, a uniqueness constraint is _local_ in nature, constraining just the population of its role(s), with no impact on other predicates.

In Fig. 5.5(b), the mandatory dot is placed at the role end. This is best when an object type’s role lines are so close together that if we added a dot at the object type end it would be unclear which role is intended. This situation can arise when an object type plays a large number of roles displayed on the same schema page.

In Fig. 5.5, the first role of the top predicate is mandatory and unique. The mandatory role constraint verbalizes as **Each Patient has at least one PatientName**, or as **Each Patient has some** PatientName. The uniqueness constraint verbalizes as **Each Patient has at most one** PatientName. In combination, these constraints verbalize as **Each Patient has exactly one** PatientName (i.e., each recorded patient has one and only one name recorded). In general, _at least one_ + _at most one_ = _exactly one_.

In a schema, if two or more fact roles are played by the same object type, then individually these roles are optional unless marked mandatory. For example, in Fig. 5.5 the first role of Patient has PhoneNr is optional. So, we may add a patient to the database population without adding a phone number for that patient.

What about the roles played by PatientName and PhoneNr? If these are the only roles played by these object types in the global schema, then these roles are mandatory. Unless declared independent (see Section 6.3), each primitive object must play some role, and each primitive entity must play some fact role. Hence _by default, if a primitive object type plays only one role, or a primitive entity type plays only one fact role_ (in the global schema), this role is mandatory. In such cases, the implied mandatory role dot is usually

![](img/1344db3eba3d550e6edb009556fcd95c_188_0.png)

omitted. In Fig. 5.5, if no other roles are played by PatientName and PhoneNr, their roles are mandatory by implication. In this case, although not recommended, these implied constraints could be marked explicitly, as shown in on the rightmost schema in Fig. 5.6.

Explicit depiction of implied mandatory role constraints has several disadvantages. First, it complicates schema evolution. For example, suppose that tomorrow we decide to add the fact types Patient had previously—PatientName; Patient is secondary—PhoneNr. With the implicit approach, this is simply an addition to the current schema. But with the explicit approach, we need to delete the formerly implied mandatory role constraints and replace them with weaker constraints (e.g., Each PatientName is of, or was of, at least one Patient; Each PhoneNr is used by, or is a secondary number for, at least one Patient—such inclusive-or constraints are discussed shortly).

Another problem with marking implied mandatory constraints is that this de-emphasizes the important mandatory role constraints (the ones we need to enforce (e.g., we must record a name for each patient)). Implied mandatory constraints are enforced automatically, so they have no implementation impact.

If we demanded the explicit approach for simple mandatory constraints, we should do the same for disjunctive mandatory (inclusive-or) constraints. But if the roles involved in the disjunction occur on separate schema pages, there is no convenient way to mark the constraint between them.

Another problem with the explicit approach is that it complicates theorem specification. Later on, we consider some schema equivalence theorems. In this context, the implicit approach allows us to discuss schema fragments independently of other roles played in the global schema, but the explicit approach would forbid this, leading to extra complexity.

For such reasons, avoid the explicit specification unless we have some special reason to draw the attention of a human to the implied constraints. As discussed in the next chapter, the rule for implicit mandatory roles does not apply to subtypes; if they play just one fact role, this is optional unless marked mandatory.

The population of a mandatory role equals the total population of its attached object type. Fig. 5.7 depicts the general case for an object type A and an attached role r. The role r may occur in any position in a predicate of any arity, and A may participate in other predicates. Mandatory role constraints are enforced on populations rather than types. If the only fact stored is that patient 001 is named “Adams C”, the name role played by Patient is still mandatory even if more instances of the Patient type are yet to be added to the population.

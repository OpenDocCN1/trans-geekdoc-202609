
Fig. 9.18(b) shows an ORM schema for this domain. The objectified association Writing is marked independent (by the “!”) to indicate that a writing object may exist, independently of whether we record its period. ORM displays Period as an object type, not an attribute, and includes its unit.

![](img/1344db3eba3d550e6edb009556fcd95c_388_0.png)

FIG. 9.17 Some ORM constraints that can't be captured by UML multiplicities.

![](img/1344db3eba3d550e6edb009556fcd95c_388_1.png)

FIG. 9.18 Writing depicted as an objectified association in (a) UML and (b) ORM.

![](img/1344db3eba3d550e6edb009556fcd95c_388_2.png)

FIG. 9.19 Objectification of an n:1 association in (a) UML and (b) ORM.

UML allows any association (binary and above) to be objectified into a class, regardless of its multiplicity constraints. In particular, UML allows objectification of n:1 associations, as shown in Fig. 9.19(a). While this is allowed in ORM 2 (see Fig. 9.19(b)), it is often a case of poor modeling. For example, given that a moon orbits only one planet, an orbital period may be related directly to the moon. Unless there are other things to record about Orbit (e.g., eccentricity), we could instead model the orbital period in UML as an attribute of Moon, or in ORM as an association between Moon and Period (as in Fig. 9.19c). Chapter 10 provides heuristic guidelines for applying objectification in modeling.

UML has no graphic notation to capture ORM external uniqueness constraints across roles that are all modeled as attributes in UML. However, ORM external uniqueness constraints used for coreferencing can be modeled in UML. Fig. 9.20(a) shows an ORM model where the Account object type is coreferenced by combining its bank with its (local) account number.

One way to model this in UML is to use a qualified association. Here, instead of depicting the relevant ORM roles or object types as attributes, UML uses a class, adjacent to a qualifier, through which connection is made to the relevant association role. A qualifier in UML is a set of one or more attributes whose values can be used to partition the class, and is depicted as a rectangular box enclosing its attributes.

Fig. 9.20(b) is based on an example from the official UML specification. Here, each bank account is used by at most one client, and each client may use many accounts. The attribute accountNr is a qualifier on the association, effectively partitioning each bank into different accounts.

![](img/1344db3eba3d550e6edb009556fcd95c_389_0.png)

FIG. 9.20 (a) Qualified association in UML and (b) coreferenced type in ORM.

The qualified association approach in Fig. 9.20(b) is less adaptable. For example, if we now want to record something about the account (e.g., its balance) we need to introduce an Account class, and the connection to accountNr is unclear. For a similar example, see Fowler (1997, p. 92), where product is used with Order to qualify an order line association; again, this is unfortunate because we would normally introduce a Product class to record data about products, and relevant connections are then lost.

Fig. 9.20(c) shows a better way to capture coreferencing in UML. Here, both the accountNr attribute and the association end hosted by Bank are marked with “{id}”, indicating that these two in combination provide an identifier for Account.

ORM’s concept of an external uniqueness constraint that may be applied to a set of roles in one or more predicates provides a simple, uniform way to capture all of UML’s qualified associations and unique attribute combinations as well as other cases not expressible in UML graphical notation (e.g., cases with m:n predicates or long join paths). As always, the ORM notation has the further advantage of facilitating validation through verbalization and multiple instantiation.

## 9.5 Set-Comparison Constraints

Set-comparison constraints declare a subset, equality, or exclusion relationship between the populations of role sequences. This section compares support for these constraints in UML and ORM. A detailed discussion of these constraints in ORM can be found in Section 6.4.

As an extension mechanism, UML allows subset constraints to be specified between *whole associations* by attaching the constraint label “{subset}” next to a dashed arrow between the associations. For example, the subset constraint in Fig. 9.21(a) indicates that any person who chairs a committee must be a member of that committee. Fig. 9.21(b) shows the same example in ORM.

![](img/1344db3eba3d550e6edb009556fcd95c_390_0.png)

ORM has a mature formalization, including a rigorous theory of schema consistency, equivalence, and implication. Because formal guidelines for working with UML are somewhat immature, care is needed to avoid logical problems. For example, consider the modified version of our committee example shown in Fig. 9.22(a), which comes from an earlier version of the UML specification, with reference schemes added. Do you spot anything confusing about the constraints?

You probably noticed the problem. The multiplicity constraint of 1 on the chair association indicates that each committee must have at least one chair. The subset constraint tells us that a chair of a committee must also be a member of that committee. Taken together, these constraints imply that each committee must have a member. Hence, we would expect to see a multiplicity constraint of “1..*” (one or more) on the Person end of the membership association. However, we see a constraint of “*” (zero or more) instead, which at best is misleading. An equivalent, misleading ORM schema is shown in Fig. 9.22(b), where the upper role played by Committee appears optional when in fact it is mandatory.

One might argue that it’s okay to leave these schemas unchanged, as the constraint that each committee includes at least one person is implied by other constraints. However, while display options for implied constraints may sometimes be a matter of taste, practical experience has shown that in cases like this, it is better to show implied constraints explicitly, as in Fig. 9.23, rather than expect modelers or domain experts to figure them out for themselves.

![](img/1344db3eba3d550e6edb009556fcd95c_390_1.png)

![](img/1344db3eba3d550e6edb009556fcd95c_391_0.png)

FIG. 9.23 All constraints are now shown explicitly in (a) UML and (b) ORM.

![](img/1344db3eba3d550e6edb009556fcd95c_391_1.png)

FIG. 9.24 The relational schema mapped from Fig. 9.23.

Some ORM tools can detect the misleading nature of constraint patterns like that of Fig. 9.22(b) and ask you to resolve the problem. Human interaction is the best policy here because there is more than one possible mistake (e.g., is the subset constraint correct leading to Fig. 9.23, or is the optional role correct resulting in Fig. 9.21?).

If a schema in Fig. 9.23 is mapped to a relational database, it generates a referential cycle because the mandatory fact types for Committee map to different tables (so each committee must appear in both tables). The relational schema is shown in Fig. 9.24 (arrows show the foreign key references, one simple and one composite, which correspond to the subset constraints).

Referential cycles are sometimes unavoidable, but are awkward to implement. In this case, the cycle arose because of the pair-subset constraint combined with the mandatory role constraint on is-chaired-by. Given the pair-subset constraint, the cycle would also apply if Committee is independent or plays another mandatory, functional role. Relational mapping is covered in detail in Chapter 11.

Because UML does not allow unary relationships, subset constraints between ORM unaries need to be captured textually, using a note to specify an equivalent constraint between Boolean attributes. For example, the ORM subset constraint in Fig. 9.25(b), which verbalizes as **Each Patient who smokes is cancer prone**, may be captured textually in UML by the note in Fig. 9.25(a).

UML 2 introduced a *subsets property* modifier to indicate that for each instance that is the context for a property (an attribute or association role), the population (extension) of that property for that instance must be a subset of the population of another compatible property for that instance. For example, adorning the citizen role in Fig. 9.26(a) with {subset resident} means that each citizen of a country is a resident of the same country. Fig. 9.26(b) shows the equivalent ORM schema.

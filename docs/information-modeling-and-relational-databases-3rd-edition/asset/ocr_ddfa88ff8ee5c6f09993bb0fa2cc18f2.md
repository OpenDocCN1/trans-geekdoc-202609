The fourth row (C4, Mechanics, ?) is rejected because in the presence of row 3, it violates the constraint that courses with no department must have different titles. To determine constraint satisfaction, the nulls on rows 3 and 4 are treated like ordinary values, and thus are equated. This effectively applies *outer join semantics*.

Outer join semantics may apply even if the disjunctive reference scheme is the only means of identifying courses, as in Fig. 10.2(c).

External constraints with inner join semantics may be used for the preferred reference scheme of an entity type only if the coroles hosted by that entity type in the constrained relationships are mandatory, as in Fig. 10.2(a).

In the previous examples, the join path underlying the external uniqueness constraint involves only one join. But in practice, the *join path* may involve many inner or outer joins. Fig. 10.3 summarizes the problem of *join path ambiguity*. To find the join path underlying the external uniqueness constraint, we need to find a path connecting roles r2 and r9, moving right from r2 and left from r9.

![](bbox=[0.22, 0.39, 0.75, 0.5])

FIG. 10.3 Join paths may require explicit declaration of the join roles.

Our choice is shaded, but there are three possible paths between B and C. We could traverse the top predicate, performing the joins r2 = r3 and r4 = r9. We could traverse the middle predicate that implicitly underlies the subtype connection, performing the joins r2 = r5 and r6 = r9, or we could traverse the bottom predicate, performing the joins r2 = r7 and r8 = r9.

ORM does not graphically highlight the relevant joins (as done here by shading). In general, shading is not adequate because a path may traverse the same predicate more than once. A general graphical solution may be provided by numbering the roles used to perform the joins, but this can lead to messy diagrams. A tool could prompt the user to select the list of join roles and then toggle the display of the joins on/off under user control. An alternative is to use a textual language to formulate constraints with multiple, candidate join paths. Formal support for join paths is provided in the professional version of NORMA.

For non-ORM approaches, basic support for external uniqueness is required, and then the join paths may be disambiguated graphically as for ORM or textually if the method includes a sufficiently powerful formal query language. UML could use the object constraint language (OCL) for such specifications, although OCL expressions often appear cryptic to nontechnical domain experts.
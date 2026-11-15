This Date example illustrates the following generalization of the rule mentioned earlier for single mandatory roles: by default, the disjunction of roles played by a primitive object type is mandatory. If the object type is an *entity type*, the disjunction of its fact-roles is also mandatory by default (this default can be overridden by declaring the object type independent; see next chapter).

Apart from highlighting the important cases where disjunctive mandatory roles need to be enforced (e.g., the coach-player disjunction) and simplifying schema evolution, this rule facilitates the drawing of schemas. For example, object types such as *Date* and *MoneyAmount* often have several roles that are disjunctively mandatory, and to display this constraint explicitly would be messy (or even impossible if the object type occurs on separate schema pages).

To avoid confusion, a mandatory role constraint (simple or disjunctive) should be shown explicitly if the object type it constrains is a subtype (see *Chapter 6*).

In the case of implied (possibly disjunctive) mandatory role constraints, it is okay to *mark the constraint explicitly* if it will still apply if *more roles are added to the object type* (where these extra roles are excluded from the constraint). For object types such as *Date*, this would almost never happen.

An *inclusive-or* (disjunctive mandatory role) constraint indicates that each instance in the population of the object type must play at least one of the constrained roles (and possibly all of them).

*Fig. 5.11* indicates in general how to specify explicitly that a disjunction of roles *r1*, *r2*, ..., *rn* is mandatory by linking the *n* roles to a circled dot. The roles may occur at any position in a predicate, and the predicates need not be distinct.

![](bbox=[0.13, 0.56, 0.42, 0.66])

**Inclusive-or (Disjunctive mandatory role) constraint**
The inclusive disjunction of roles r1 .. rn is mandatory for A
i.e., each member of pop(A) plays r1 or ... rn (or all)
i.e., each member of pop(A) plays at least one of r1, ..., rn

# FIG. 5.11 Inclusive-or constraint (the role disjunction is mandatory).

The inclusive “or” is used in the *verbalization* of the constraint. For example, the inclusive-or constraint in Fig. 5.10 is formally verbalized as **Each Member coaches some Team or plays for some team**. As in logic and computing, “or” is always interpreted in the inclusive sense unless we say otherwise.

Inclusive-or constraints sometimes apply to roles in the same predicate. Fig. 5.12 relates to a small UoD where people are identified by their first name. A sample population is shown for the ring binary; here each person plays one (or both) of the two roles. For instance, Terry is a child of Alice and Bernie, and a parent of Selena. Because Person plays another role in the schema, the disjunctive mandatory role constraint must be depicted explicitly, either by connecting the circled dot to (a) the junction of the two roles, or to (b) both of the roles.
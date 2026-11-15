may then be burdened with the responsibility of distinguishing default from actual values. Also, bag functions that ignore nulls will not ignore nils.

The final refinement to step 0 of the mapping procedure (step 0.7) deals with cases where an objectified predicate is not spanned by a uniqueness constraint. Some versions of ORM forbid this because it violates elementarity. As discussed in Section 10.5, we also prefer to avoid such cases.

However, if it is allowed, then some preprocessing is needed before executing the grouping part of the procedure.

In nested 1:1 cases, a decision should be made to favor one of the roles in grouping. For example, suppose the schema in Fig. 11.49 is used to model current marriages in a monogamous society. This schema violates elementarity. It can be split into two fact types: one about the marriage and one about the marriage year. If no other functional roles are played by Person, we might map this to either of the tables schemes shown in Fig. 11.49. For such 1:1 cases, a choice must be made (e.g., by choosing one of the uniqueness constraints as primary).

If only one role in the objectified predicate is functional, it is automatically chosen for the primary key. For example, in a polyandrous society where a man may be married to at most one woman but not vice versa, the husband column would be chosen as the primary key (and wife would no longer be a key).

Despite the provisions of step 0.7, objectified associations without a spanning uniqueness constraint should normally be avoided by remodeling without nesting. Recall Fig. 10.52, which showed two ways to do this for the marriage case under discussion. Figs. 10.54 and 10.55 illustrated how to remodel some other cases without using objectification.

![](bbox=[0.107, 0.585, 0.823, 0.721])

Once the columns and constraints are determined in a relational mapping, you may wish to consider changing the *order of columns* within a table. Although the relational model treats column order as irrelevant, in practice, column order can have an impact on both readability and performance. A CASE tool will choose an ordering for you, but you can override this.

Usually, it is best to include primary key columns first, and to group columns together if they are components of a compositely identified object type or have a strong semantic affinity. In such cases, a top-down order is usually preferable (e.g., buildingNr, roomNr
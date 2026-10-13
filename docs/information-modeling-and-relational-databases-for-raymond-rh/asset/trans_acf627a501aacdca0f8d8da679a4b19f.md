
## Figure 14.6 illustrates the most common case

[Figure 14.6](#Ch014_681-771_B9780443237904000189.xhtml#f0035) illustrates the most common case, where *R* is a ternary predicate with a UC spanning *B* and one other role. However, the result applies to longer predicates as well. The game example of [Figure 14.4](#Ch014_681-771_B9780443237904000189.xhtml#f0025) is an instance of the equivalence in [Figure 14.6](#Ch014_681-771_B9780443237904000189.xhtml#f0035) where *B* = MedalKind, *n* = 3, and the role of *B* is contained in a composite UC.

![Figure 14.6 The UC on the left is equivalent to the UC on the right.](images/B9780443237904000189/f14-06-9780443237904.jpg)

[Figure 14.6](#Ch014_681-771_B9780443237904000189.xhtml#B-f0035) The UC on the left is equivalent to the UC on the right.

### What if the role of B is not in a UC?

But what happens if the role of *B* in the generic predicate *R* is not in a UC? Because *R* is elementary, its other role must be spanned by a UC; that UC is converted to an **exclusion** constraint spanning the specialized predicates.

Mutually exclusive unary predicates provide the simplest case of this. For example, suppose workers in a company hold at most one position (Manager, Clerk, or Secretary). As shown in [Figure 14.7](#Ch014_681-771_B9780443237904000189.xhtml#f0040), assuming appropriate verbalizations between the predicates, this may be rephrased with mutually exclusive unary predicates. For implementation, the binary version is usually preferred (e.g., its relational schema simplifies updates to a worker's position and allows schema updates to the list of positions). The more unary predicates there are, the worse the unary solution gets (why?).

![Figure 14.7 The UC on the left is equivalent to the exclusion constraint on the right.](images/B9780443237904000189/f14-07-9780443237904.jpg)

[Figure 14.7](#Ch014_681-771_B9780443237904000189.xhtml#B-f0040) The UC on the left is equivalent to the exclusion constraint on the right.

### Mutually exclusive binary predicate example

Another example, this time with mutually exclusive binary predicates, is shown in [Figure 14.8](#Ch014_681-771_B9780443237904000189.xhtml#f0045). Reference schemes are omitted for simplicity. Here, the task codes "A" and "R" stand for Authoring and Reviewing. Note the two alternative ways of stating that a person may not be both an Author and a Reviewer of the same book.

![Figure 14.8 The UC on the left is equivalent to the exclusion constraint on the right.](images/B9780443237904000189/f14-08-9780443237904.jpg)

[Figure 14.8](#Ch014_681-771_B9780443237904000189.xhtml#B-f0045) The UC on the left is equivalent to the exclusion constraint on the right.

These two examples illustrate the unary (*m*=1) and binary (*m*=2) cases of the following second corollary of Theorem PSG1. The result applies to longer predicates as well (see [Figure 14.9](#Ch014_681-771_B9780443237904000189.xhtml#f0050)). Here, the exclusion constraint means that no value row may appear in more than one of the $S_i$ fact tables.

*   If a UC spans all roles of *R* except the role of *B*, then $S_1 \dots S_n$ are mutually exclusive; and conversely.

![Figure 14.9 The UC on the left is equivalent to the exclusion constraint on the right.](images/B9780443237904000189/f14-09-9780443237904.jpg)

[Figure 14.9](#Ch014_681-771_B9780443237904000189.xhtml#B-f0050) The UC on the left is equivalent to the exclusion constraint on the right.

### Textual vs. graphic constraints

In the rare case of a schema transformation where a graphic constraint in one schema has no graphic counterpart in the other, the constraint should be represented as a **textual constraint** in the other version.

For example, consider the two schemas in [Figure 14.10](#Ch014_681-771_B9780443237904000189.xhtml#f0055). The codes "A" and "S" stand for Assistant and Supervisor. Reference schemes are omitted for simplicity. A person may supervise one project and be an assistant on another.

![Figure 14.10 The textual constraint in schema (a) appears as a graphic constraint in (b).](images/B9780443237904000189/f14-10-9780443237904.jpg)

[Figure 14.10](#Ch014_681-771_B9780443237904000189.xhtml#B-f0055) The textual constraint in schema (a) appears as a graphic constraint in (b).

Assuming appropriate verbalizations between the predicates, the UC in schema (a) converts to the exclusion constraint in (b), and the top UC in (b) is implied.

The bottom UC in (b) states that each project has at most one supervisor. This cannot be expressed as a graphic constraint on the ternary predicate because it is a **ring constraint** (see [Section 7.4](#Ch007_273-308_B978044323790400013X.xhtml#s0035)). To ensure equivalence, it is added as a textual constraint to the left schema: **Each** Project uses **at most one** Employee in Position 'S'.

If Project plays other functional roles, the binary approach on the right is usually preferred because its relational version simplifies enforcement of that supervisor constraint. If Project plays no other functional roles, the ternary approach may be preferred because it maps to a single table.

Because schema transformation theorems are usually applied to subschemas in a global schema, care must be taken to preserve any **mandatory role constraints** (implicit or explicit).

### Mapping mandatory role constraints

For example, in [Figure 14.4](#Ch014_681-771_B9780443237904000189.xhtml#f0025), if Country plays no other role, its role in schema (a) and the disjunction of its roles in (b) are implicitly mandatory. If Country plays another role in the global schema and it is required to record at least one medal result for it, these simple and disjunctive mandatory role (inclusive-or) constraints must be shown explicitly (see [Figure 14.11](#Ch014_681-771_B9780443237904000189.xhtml#f0060)).

![Figure 14.11 The mandatory constraints in (a) map to the inclusive-or constraint in (b).](images/B9780443237904000189/f14-11-9780443237904.jpg)

[Figure 14.11](#Ch014_681-771_B9780443237904000189.xhtml#B-f0060) The mandatory constraints in (a) map to the inclusive-or constraint in (b).

This illustrates the third corollary of Theorem PSG1:

*   If the role (or role disjunction) of $A_i$ in *R* is mandatory, then the disjunction of its specialized roles is mandatory, and conversely ($1 \le i \le m$).

The inclusion of "(or role disjunction)" covers the rare case where $A_i$ plays multiple roles in *R* ($A_1 \dots A_m$ need not be distinct). Note also how our convention for implicit mandatory role constraints enables theorems like PSG1 to be stated without making any assumptions about other roles played in the global schema.

### Frequency constraints map to equality constraints

Now consider [Figure 14.12](#Ch014_681-771_B9780443237904000189.xhtml#f0065)(a). Here, Country's medal-winning role is optional (implying Country plays another role in a unary or longer fact type, but it has a **frequency constraint** of 3). Thus, if any medal result is recorded for a country, all three medal results (Gold, Silver, and Bronze) are required. To express this in [Figure 14.12](#Ch014_681-771_B9780443237904000189.xhtml#f0065)(b), we add an **equality constraint** between the medal-winning roles played by Country. This is an instance of the fourth corollary of Theorem PSG:

![Figure 14.12 The frequency constraint in (a) maps to the equality constraint in (b).](images/B9780443237904000189/f14-12-9780443237904.jpg)

[Figure 14.12](#Ch014_681-771_B9780443237904000189.xhtml#B-f0065) The frequency constraint in (a) maps to the equality constraint in (b).

```
If R is a ternary predicate with a UC spanning only the role of B and one other role, adding a frequency constraint of n to that other role is equivalent to adding an equality constraint on the specialized versions of that role.
```


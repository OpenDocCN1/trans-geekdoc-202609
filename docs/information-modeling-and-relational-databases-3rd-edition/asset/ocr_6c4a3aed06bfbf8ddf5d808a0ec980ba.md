![](bbox=[0.375, 0.1, 0.65, 0.2])

FIG. 4.45 This ternary is a compound fact type, and hence splittable.

Let’s apply the _n_ − 1 rule. Here the key has length 1, which is 2 less than the length of the fact type. So, the fact type is not elementary and must be split. But _how do we split it_? Our verbalization of row 1 is a conjunction of two facts about the same country. Assuming our interpretation of the report is correct, we must split the fact type into two fact types as shown in Fig. 4.46. Because the common entity type is Country, the original ternary fact type is “split on Country”. If we captured the semantics of the report in step 1 correctly, it would be wrong to split this fact type in any other way.

![](bbox=[0.38, 0.4, 0.65, 0.5])

FIG. 4.46 The previous ternary splits into these two elementary fact types.

To see why the splittability rule works in this case, look back at Table 4.7. A UC on the Country column means that, given any state of the database, no country can be listed more than once in this column. Each country has at most one population and each country has at most one area. So, for any given country, if we are as separate pieces of information that country’s population and that country’s area, we can reconstruct that country’s row in the output report. Because the ternary fact type of the output report can be split and recombined without information loss, it is not elementary.

If a fact type violates the _n_ − 1 rule, it is a conjunction of smaller fact types even if its predicate has no conjunctive operator such as “and”. Suppose we verbalized the previous ternary as Country with Population has Area. This still means the same, so is really a conjunction in disguise. Similarly, the ternary Invoice issued to Customer on Date has a UC on its first rule and can be split into two fact types: Invoice was issued to Customer; Invoice was issued on Date. In general, if a fact type can be rephrased as a conjunction, it should be split because it is not elementary.

Before considering other examples, let’s review some terminology used in the normalization approach to database design. For a given fact table, let _X_ denote a single column or combinations of columns, and let _Y_ denote a single column. Then we say that _Y_ is _functionally dependent on X_ if and only if, for each value of _X_ there is at most one value of Y. In other words, _Y_ is a _function of X_. A function is just a many:1 relation (including 1:1 as
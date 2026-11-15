

“association” means “relationship type”. Section 10.5 refines the notion of objectification to distinguish two varieties, propositional and situational.

An objectified association is depicted by a named, soft-rectangle around the predicate being objectified (see Fig. 3.16). The name of the objectified association is placed in double quotes. An objectified association usually has two roles, but may have one or more.

Entries in fact columns for nested objects may be shown as bracketed pairs (triples, etc.) of values. For example, the enrollment of student 1001 in CS100 appears as “(1001, CS100)” in the fact table for the resulted in predicate. Note that nesting is not the same as splitting. Fig. 3.16 does not show two independent binaries. The resulted in predicate cannot be shown without the enrolled in predicate. The ternary in Fig. 3.15 is still elementary. Fig. 3.15 is said to be the flattened, or unnested, version.

Chapter 14 deals with schema equivalence in detail. The nested and flattened versions are not equivalent unless the role played by the objectified association is mandatory. With our current example, this means that a rating must be known for each enrollment. In this case, the flattened version is preferred because it is simpler to diagram and populate. As discussed later, nesting is often preferred if the objectified association has an optional role, or more than one role to play.

![](img/1344db3eba3d550e6edb009556fcd95c_114_0.png)

FIG. 3.16 Knowledge base for Table 3.9 (nested version).

| Politician | Country | Year |
|---|---|---|
| Clinton | Australia | 1994 |
| Clinton | Italy | 1994 |
| Clinton | Australia | 1995 |
| Keating | Italy | 1994 |

![](img/1344db3eba3d550e6edb009556fcd95c_114_1.png)

The Politician with surname 'Clinton' **visited** the Country named 'Australia' **in** the Year 1994 CE.

FIG. 3.17 One way of verbalizing the first row.

For example, suppose we widen the UoD to include enrollment dates. The flat solution needs another ternary: Student enrolled in Course on Date. With the nested solution, we simply add the binary: Enrollment occurred on Date. As shown later, the nested solution also simplifies constraint specification in this case, and hence is preferred.

Now consider the travel record example depicted in Fig. 3.17. Using the telephone heuristic, the modeler verbalizes the first row of data as an instance of the ternary fact type: Politician visited Country in Year. The sample data indicates that many politicians may visit many countries in many years, allowing many nesting options. We could objectify Politician visited Country as Visit, and add Visit occurred in Year. We might instead objectify Politician traveled in Year as Travel, and add Travel visited Country, or objectify Country was visited in Year as Visit, and add Visit was by Politician. With no strong reason for one nesting choice over the other, it is simpler to leave it as a ternary.

Although we usually display only one reading for ternary and longer fact types, there are many possible readings depending on the order in which we traverse the roles. An n-ary predicate has n! (factorial n, i.e., n × n−1 × ... × 1) reading orders. Hence, a ternary has six possible reading orders, a quaternary has 24, and so on.

For example, the ternary fact type given earlier could be specified by any of the following six readings: Politician visited Country in Year; Politician in Year visited Country; Country was visited by Politician in Year; Country in Year was visited by Politician; Year included visit by Politician to Country; Year included visit to Country by Politician. Some ORM tools also support alias readings for any given reading order.

In practice, one reading is usually enough. However, if we wish to query the schema directly, it is handy to be able to navigate from any given role. To cater for this, we would need to supply for each role a reading that starts at that role (the order of the later roles doesn’t matter). So, we never need any more than n readings for any n-ary fact type. This is a lot fewer than factorial n. Supplying predicate readings for more than one reading order of a fact type can also help with better verbalization of constraints and derivation rules. In practice, one often provides forward and inverse readings for binary fact types, but usually provides alternate readings for n-ary fact types only on an as-needed basis.

Now suppose we need to design a database for storing sales data that can be displayed graphically as shown in Fig. 3.18. This three-dimensional bar chart shows the sales figures for two computer-aided drafting products codenamed “ACAD” and “BCAD”. As an exercise in steps 1 and 2, try to verbalize the sales information and then schematize it (on a conceptual schema diagram) before reading on.

Consider the first Q1 bar. A person familiar with the domain might verbalize the fact as: “BCAD in the first quarter had sales of one million dollars”. This completes step 1a. As modelers, we complete step 1b by refining this into one or more elementary facts. In this case, we may verbalize it as a single ternary: “The Product with code ‘BCAD’ in the Quarter numbered 1 had sales of MoneyAmount 1000000 USD”.

We chose to identify quarters using numbers (e.g., 1) but you can use codes (e.g., “Q1”) if you like. We used the object type “MoneyAmount” instead of “Sales” to make the underlying domain explicit. This makes it clear that we can compare sales figures with other monetary figures (e.g., costs and profits).

![](img/1344db3eba3d550e6edb009556fcd95c_116_0.png)

FIG. 3.18 Can you verbalize this bar chart?

Assuming the chart applies to the United States, we chose USD (United States Dollar) for the monetary unit. This distinguishes it from other dollars (e.g., AUD for Australian Dollar). This is good practice, but if there is no danger of confusion you could simply show the unit as “$”.

Instead of directly using MoneyAmount as the object type, we could do this indirectly by using Sales with the expanded reference mode (USD: Money), which abbreviates to (USD:). Each other bar may be verbalized similarly. This completes step 1. In preparation for step 2, we could set the fact type out with reference modes in parentheses as follows: Product(Code) in Quarter(nr) had sales of MoneyAmount(USD:).

It is now a simple task to draw the conceptual schema diagram. As a check, we populate it with some simple fact instances. Fig. 3.19 shows both direct and indirect ways of typing sales to money amounts. As a display option, (USD:) may be expanded to (USD: Money).

![](img/1344db3eba3d550e6edb009556fcd95c_116_1.png)

FIG. 3.19 A conceptual schema for the sales data, with a sample population.

Another common way for presenting numeric data is the pie chart. A legend is often provided next to the chart to indicate the items denoted by each slice. Each slice of the pie indicates the portion of the whole taken up by that particular item. An example is given in Fig. 3.20. Try to schematize this yourself before reading on.

![](img/1344db3eba3d550e6edb009556fcd95c_117_0.png)

FIG. 3.20 Can you schematize this pie chart?

Applying step 1a to the defense slice of the first pie, we could verbalize the fact as “In 1965 defense consumed 43% of the budget”. To complete step 1, we refine this to “In Year 1965 CE the BudgetItem named ‘Defense’ consumed Portion 43% of the budget”. The other slices denote the same kind of fact, so we may generalize to the ternary fact type: in Year (CE): BudgetItem(Name) consumed Portion (%) of the budget. Here, the predicate “in .... consumed .... of the budget” has front text before the first placeholder and two placeholders adjacent to one another. Although fairly rare, this is a legal mixfix predicate.

This flexibility makes verbalization easier than it would have been otherwise. To complete step 2, the resulting schema and sample data are shown in Fig. 3.21.

To conclude this section, let’s review some terminology. Three terms for objects have now been introduced. Entities are the objects in the UoD that we reference by means of descriptions. Values (e.g., character strings or numbers) appear as entries in database tables and are often used to refer to entities. Finally, relationships between objects may be treated as objects themselves: these are objectified relationships (or nested objects).

![](img/1344db3eba3d550e6edb009556fcd95c_117_1.png)

FIG. 3.21 A conceptual schema for the budget data, with a sample population.


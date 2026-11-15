Another common way for presenting numeric data is the pie chart. A legend is often provided next to the chart to indicate the items denoted by each slice. Each slice of the pie indicates the portion of the whole taken up by that particular item. An example is given in Fig. 3.20. Try to schematize this yourself before reading on.

![](bbox=[0.21, 0.198, 0.8, 0.35])

FIG. 3.20 Can you schematize this pie chart?

Applying step 1a to the defense slice of the first pie, we could verbalize the fact as “In 1965 defense consumed 43% of the budget”. To complete step 1, we refine this to “In Year 1965 CE the BudgetItem named ‘Defense’ consumed Portion 43% of the budget”. The other slices denote the same kind of fact, so we may generalize to the ternary fact type: in Year (CE): BudgetItem(Name) consumed Portion (%) of the budget. Here, the predicate “in .... consumed .... of the budget” has front text before the first placeholder and two placeholders adjacent to one another. Although fairly rare, this is a legal mixfix predicate.

This flexibility makes verbalization easier than it would have been otherwise. To complete step 2, the resulting schema and sample data are shown in Fig. 3.21.

To conclude this section, let’s review some terminology. Three terms for objects have now been introduced. Entities are the objects in the UoD that we reference by means of descriptions. Values (e.g., characters strings or numbers) appear as entries in database tables and are often used to refer to entities. Finally, relationships between objects may be treated as objects themselves: these are objectified relationships (or nested objects).

![](bbox=[0.32, 0.74, 0.7, 0.9])

FIG. 3.21 A conceptual schema for the budget data, with a sample population.
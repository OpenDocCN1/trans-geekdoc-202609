The best we can do is to name each role and then use role names as headers to the fact table. However, the visual connection of the fact columns to the class diagram would be weak because of the nonlinear layout of the association roles, and the higher the arity of the association, the worse it gets.

In its favor, UML is far richer than ORM or ER in its ability to capture other aspects of application design (e.g., operations, activities, component packaging, and deployment). UML includes diagrams, such as state machine and activity diagrams, to capture business processes. Any full specification of a business domain needs to address these dynamic aspects. If the application is to be implemented in object-oriented code, UML enables more precise descriptions of the programming code structures to be specified (e.g., attribute visibility and association navigability).

If we restrict our attention to conceptual data modeling, however, the ORM notation is much richer than ER or UML in its capacity to express business constraints on the data as well as being far more orthogonal and less impacted by change. As a simple example, consider the output report of Table 1.4 (the reviewers and movie 3 are fictitious). You might like to try modeling this yourself before reading on.

# Table 1.4 Another sample output report about Movies.

| Movie | | Director | | Reviewers | |
|---|---|---|---|---|---|
| Nr | Title | Name | Born | Name | Born |
| 1 | Crater | Kyle Patrick Alvarez | US | Fred Bloggs Ann Green | US US |
| 2 | Crocodile Dundee | Peter Faiman | AU | Ann Green Ima Viewer Tom Sawme | US GB AU |
| 3 | Star Peace | Ann Green | US | ? ? | ? ? |
| ... | ... | ... | ... | ... | ... |

One way to model this report in UML is shown in Fig. 1.5. Although the population of the sample report suggests that movie titles are unique and that a person can direct only one movie, let's assume that the domain expert confirms that this is not the case. We should adapt our sample population to illustrate this (e.g., add a new movie 4 with the same title “Star Peace” directed by Peter Faiman).

![](bbox=[0.285, 0.78, 0.68, 0.87])

# FIG. 1.5 A UML class diagram for Table 1.4.
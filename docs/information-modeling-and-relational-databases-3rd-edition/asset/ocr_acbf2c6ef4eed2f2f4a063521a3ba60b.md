MovieTitle would still be a minor object type even if its role was functional; its role is still only implicitly mandatory).

There are some finer points to determining major object types, but this is enough to get the basic idea. Based on the previous reasoning, Fig. 18.8 has only two major object types: Movie and Person. Fig. 18.10 provides one overview of the application by displaying only the major fact types.

![](bbox=[0.35, 0.24, 0.62, 0.35])

FIG. 18.10 Only the major fact types are shown.

Instead of being hidden, minor fact types may, if desired, be viewed in terms of attributes of the major object types. Although this attribute viewpoint hides structural information (e.g., domains and certain constraints), the ER or UML diagram obtained provides a compact picture that is useful for quick overviews. Fig. 18.11 shows a UML class diagram for the current example. Unlike most ER notations, UML allows the attribute domains to be specified if desired, and the missing constraints (here disjunctive mandatory, subset, exclusion, external uniqueness, and asymmetric constraints) could be documented in notes, although at the price of losing compactness.

Notice that country information is displayed here in terms of attributes (single and multivalued) rather than as associations with a Country class. This is because Country is a minor object type in the original ORM schema. If instead, Country played an explicit mandatory role or a functional role not already absorbed, it would become major, and we would display it as a class. This is usually the case (e.g., we normally store both the code and name of countries).

![](bbox=[0.23, 0.71, 0.72, 0.88])

FIG. 18.11 A UML class diagram abstracted from Fig. 18.8.
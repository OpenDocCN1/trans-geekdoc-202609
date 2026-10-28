![](bbox=[0.141, 0.081, 0.839, 0.343])

Figure 12. Conceptual model for defining Linking Problem Types.

![](bbox=[0.141, 0.408, 0.839, 0.624])

Figure 13. An example of formalization of a LPTs in RDF.

provided by this language. This hierarchisation based on the `rdfs:subClassOf` property involving classes for each LPT (e.g., `LPT_1-1_1-2 rdfs:subClassOf LPT_1-1`) is not represented here for lack of space.

# 6. Conclusion

Data linking allows similar entities to be linked, so that semantic data spread over several heterogeneous datasets can be used more effectively. In this paper, we therefore propose a formalized classification of the different types of problems that can be encountered when linking RDF datasets. We hope that this classification will help the data linking community to better identify the problems that may arise when two RDF datasets with heterogeneous terminology, structure, and logic need to be linked. Establishing a precise profile, as close as possible to the RDF data to be processed, should allow a better choice of the algorithmic module(s) needed to solve a data linking task, in an attempt
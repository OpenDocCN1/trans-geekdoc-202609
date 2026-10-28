![](bbox=[0.219, 0.082, 0.809, 0.21])

**Figure 3.** Representation in FLINT of the rules for giving a fine. Purple circles are instances of *ComplexFact*. Nodes related to *Pay fine* are omitted.

# ## 6. Conclusion and discussion

We have presented the FLINT ontology and its publicly accessible RDF/OWL implementation. The main aim of the FLINT ontology is to support normative coordination. FLINT does this by describing a normative system using facts to describe a state space, and acts to describe permissible transitions between states. As in [14,15] we thus model legal relations, with a focus on legal powers (in the form of acts) and duties. We found that modeling institutional facts in more detail greatly benefits the clarity of the interpretations of norms. We have also illustrated the intended use of the ontology with a toy example.

There are several research directions connected to FLINT and its ontology in which developments are currently taking place. First, while the FLINT ontology describes interpretations of norms, we are also working towards computational implementations of these interpretations in order to automate normative reasoning. A norm engine based on the FLINT ontology is under development [22], which uses the ontology in combination with SHACL constraints and inference rules to reason about compliance in concrete scenarios.

Second, to support this automated normative reasoning, we are working on a formalization of FLINT as a variant of dynamic logic [23], in order to characterize the decidability and complexity of this logic.

Third, another area of research focuses on the automation of the conversion from legal texts into FLINT frames. This is done by making some components of FLINT (actions, actors, recipients, and objects) in the legal text through automated semantic role labeling [24,25,26]. The FLINT ontology can be used in this line of work to exchange information between different tools.

Finally, we are working on an extension of the ontology which distinguishes several stages in the transformation from a law in natural language to a FLINT model. This starts with creating annotations in the law text and ends with a full formal model that can be used in conjunction with the norm engine, making all connections between steps explicit so that the formal model is explainable and traceable [27]. With this, we aim to bridge the gap between the theoretical foundations of legal philosophy, and the practical need for normative coordination.
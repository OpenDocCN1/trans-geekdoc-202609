|  | Number of Statements | Virtuoso | Jena | GraphDB | Oxigraph |
|---|---:|---:|---:|---:|---:|
| Standard reification | 61,865,751 | 3.6 GB | 52 GB | 8.5 GB | 6.5 GB |
| Singleton properties | 45,335,637 | 3.6 GB | 48 GB | 257 GB | 5.7 GB |
| Named graphs | 37,071,104 | 3.2 GB | 51 GB | 6.4 GB | 9 GB |
| RDF-Star | 37,055,676 | 3.7 GB | 50 GB | 6.6 GB | 12 GB |

**Table 1.** Generated DB size of different reification models.

The implementations of RDF-star[^12] can follow three approaches: *PG (Property Graph), SA (Separate Assertion), or both*[^13]. In the SA mode, quoted triples are not necessarily asserted in the graph. In the PG mode, any quoted triple is automatically asserted. Jena supports both modes, Oxigraph and GraphDB both support only the SA mode for RDF-Star. And Virtuoso does not support RDF-star at all.

# 4.2. *Experimental setup*

Experiments were run on a virtual machine with 128GB of RAM, 2GHz with 32 cores, on a Debian GNU/Linux 11 (Bullseye). All tests were run using docker images of the triplestores[^14] [^15] [^16] [^17]. All triplestores were parameterized with a query timeout of 30 minutes and given access to 16 GB of RAM. Only Oxigraph was not parameterized as we did not find the way to do it. GraphDB was also parameterized to use a context index when dealing with the named graphs version of the graph. All four triplestores were evaluated with the four reification models except for Virtuoso that does not support RDF-star, and GraphDB does not support singleton properties in an efficient way. This is because GraphDB makes the assumption that there will be only a small number of properties in the graph. This issue is described on the website of GraphDB[^18]. Details on how exactly the experiments were run are given at the end of this section.

*Query templates.* Based on the series of queries A, B, and F used in [12], we define seven query templates that are presented as SPARQL-star queries for simplicity. The templates will be referred to as Q1 to Q7. All templates can be seen in Figure 6. Q1 and Q5 are grounded with instances of ERs while Q2, Q3, Q4, and Q6 are grounded with instances of concepts. Q7 is not grounded. In these queries, only the subjects are quoted. Q2, Q3, and Q4 are star-shaped queries.

+   1. Q1 is a property path query. It returns the list of concepts and the associated hierarchy of categories (with skos:broader*) for a given ER.
+   2. Q2 is a FILTER query that compares the annotations of a concept. Given a concept, it returns the associated ERs whose pageRank score is greater than the cosine similarity using the FILTER keyword.
+   3. Q3 is a join query. It returns the set of ERs associated to three given concepts.
+   4. Q4 is similar to Q3 but with a FILTER that specifies how the three pageRank scores must relate together.

[^12]: https://w3c.github.io/rdf-star/implementations.html
[^13]: https://w3c.github.io/rdf-star/cg-spec/editors_draft.html#sa-mode-and-pg-mode
[^14]: https://hub.docker.com/r/secorserach/fuseki
[^15]: https://hub.docker.com/r/tenforce/virtuoso
[^16]: https://hub.docker.com/r/oxigraph/oxigraph
[^17]: https://hub.docker.com/r/khaller/graphdb-free
[^18]: https://graphdb.ontotext.com/documentation/10.0/devhub/rdf-sparql-star.html
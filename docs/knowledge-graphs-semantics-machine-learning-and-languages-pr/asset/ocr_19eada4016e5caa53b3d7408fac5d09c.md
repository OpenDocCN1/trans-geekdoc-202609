# 5.1 Architecture

The TIB Terminology Service was designed following the Frontend-Backend pattern, which positions an ontology lookup service as the data-providing backend for a frontend application developed using the React library. The backend service is built upon the Ontology Lookup Service (OLS) developed by EBI. This architectural structure embodies a tightly integrated design with dedicated modules for ingesting and indexing terminologies. Additionally, it incorporates graph libraries that facilitate the visualization of these terminologies and also defines API methods that enable the presentation of data on the front-end. This architecture allowed us to take advantage of not only the pre-existing API but also the ontology ingestion process, which streamlined our development efforts. However, to ensure the architecture adequately served the unique requirements of the envisioned Terminology Service, we introduced new methods into the adopted system.

![](bbox=[0.13, 0.35, 0.88, 0.65])

Figure 1: Architecture Terminology Service

The React frontend application addresses the need for flexible, autonomous implementation of features in the user interface, decoupled from the original approach of the OLS-web app.

As the original OLS user interface is embedded into the OLS-web app which is tightly integrated into the OLS backend architecture, serving individual communities would require running multiple OLS backend instances. This is costly for individual projects and hard to maintain.

We, therefore, decided for the TIB Terminology to ingest and index all ontologies in one backend while assigning the ontologies to one or more collections as we have described earlier. These collections are served to the respective communities by the front-end addressing their individual needs and preferences. Usually, collections can be
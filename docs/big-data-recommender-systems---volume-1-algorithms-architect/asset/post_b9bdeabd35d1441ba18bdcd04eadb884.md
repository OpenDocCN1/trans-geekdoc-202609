
# 18 Big data recommender systems, volume 1

Despite being fairly new, GDBs provide opportunity to improve the performance of applications dealing with huge amount of interconnected data and recommendation systems are one such example.

## Introduction

A graph (data structure to hold connected data) is a collection of edges and vertices. These vertices, also known as nodes, are used to represent entities in a domain such as a person, an actor, or an item. The edges represent the relationship between two persons, or purchase relationship between an item and a customer [31]. The vertices and edges also have properties to show further details about them. In case of vertices, examples of such properties could be age of a person or price of an item whereas in case of edges, it could be purchase of an item by a customer [32].

GDBs, universally categorized as not only structured query language (NoSQL) databases, are aiming to resolve everything using graphs. They focus on vertices (nodes) and the relationships (edges) between them. A GDB stores data in which vertices (nodes) and edges (relationships) are the building blocks. GDB are optimized for highly connected data and can become an effective tool for modelling interconnected data. By diversification in structure, the GDB has been adapted to various domains such as social networks, geographic information systems [33], e-commerce [34,35,36], and recommendation systems [37,38,39].

Since GDBs are optimized for highly connected data, they give performance advantage over relational databases provide limited capability to capture the semantics. Today’s era of big data, where we have huge data to process and analyze, the handling of complex data of interactions becomes nearly impossible in conventional databases. In Schema-based databases, as relational databases, the schema itself puts a limitation on how the information could be stored, and change in the schema requires a manual process in order to adapt new data. This is quite infeasible when we are exploring new kind of data on daily basis [26]. Therefore, it has been considered that relational databases are not suitable for storing relationship-based data [24]. It is also important to mention that all traversals in GDBs are localized and not required to explore unrelated data, which is a problem with Structured Query Language (SQL) [40]. GDBs such as, Neo4j, InfoGrid, CosmosDB, and Infinite are popular in the market days.

In GDBs, we can model anything by defining entities and the relationship among these entities as edges. Different GDB support different types of structures that can be modelled, but most type supported by most of the GDBs is Property Graph which is a multi-graph consisting of attributed, labelled, and directed vertices. Here, attributed means that an entity or relationship may have different attributes associated with them as age and price. Labelling allows grouping similar entities together.

## Discussion

Broadly, we can divide recommendation systems into two basic parts: Pattern Discovery and Pattern Application. As the name suggests, in Pattern Discovery, the system discovers the potential patterns that can be helpful in recommendation for a user.

Such patterns can be discovered through an algorithmic approach in which a dataset is processed using machine learning algorithms to identify the patterns which were not identified earlier. This is the area which got primary focus in the last decade [41,42,43]. Another mechanism which can help identify the patterns in the data is visual analytics, in which domain experts identify the hidden patterns by graph visualization [44,45,46]. Another way to learn the patterns is through business experts who understand and know the business in detail, because of their experience in the domain [47].

Once a pattern has been found either by machine learning algorithms or through business experts, the next step is to implement these patterns in business applications to generate recommendations for users. The success of a recommendation is not only dependent on how effectively it can identify the patterns, but also dependent on the ability to identify patterns in the business application. We may have to apply these patterns offline when recommendations are not critical, in case of generating recommendations for an e-mail campaign or identifying potentials for a person. Such jobs can be performed in a batch mode, and extensive algorithms can be used, in which it may be required to perform iterations on the data.

However, there are applications in which recommendations needs to be generated between a web request and a response. Recommending another restaurant while a user is viewing any specific restaurant or recommending an item while user requests to view a specific item are examples of cases. For such cases, we need systems that can generate recommendations within milliseconds which may include exclusion of complex queries on a huge data in order to match patterns. GDBs are appropriate candidates for such cases, as they are optimized to deal with interrelated data, and hence finds patterns efficiently as other database models.

Content-based filtering and CF are natively supported by GDBs. We can calculate recommendation using a similarity graph in a similar fashion as we do recommendation systems. We can define a similarity function to compare set of nodes. This similarity function can be used to find most similar nodes which can be returned to a user as recommendations. Property Graph model allows us to store precalculated similarity on the edges. We can use numerous already available methods to calculate similarity between two nodes as cosine similarity, Pearson correlation, or any other method which calculates items' frequency [24,48].

The fundamental operation to retrieve information from the graph is traversal, which is walking along the elements of a graph [31]. In graph, traversal is a localized operation unlike relational databases. It means that in order to travel from one node to another, we do not need any global information and each node and edge act as mini-index in the graph. The absence of global indexes for traversal means that GDBs have no performance impact on the size of the graph, which is quite a contrast from the case of SQL [26].

Unfortunately, no standardization has been made for traversal-based languages which results in different frameworks for this purpose. The most common implementations are Cypher Query Language [49], GraphQL [50], Gremlin [51], and SPARQL [52] used for resource description framework (RDF)-based databases. GDBs such as, Neo4j, InfoGrid, CosmosDB, and Infinite are popular in the market days.

## Theoretical foundations for recommender systems 19

## Datasets for recommendations

This subsection describes some publicly available datasets to evaluate RS. Some of these datasets contain only user-item data and, therefore, are suitable for CF techniques, while others contain product catalogue which can be used for hybrid recommendations.

### MovieLens

MovieLens dataset [53] is one of the most popular datasets used for recommendations. This dataset is compiled and made available by GroupLens, a research laboratory in the Department of Computer Science and Engineering at the University of Minnesota. The data was gathered through the MovieLens website, where users specify their preferences for movies in the form of five-star ratings. The data is in a user-item rating format and contains 20,000 movies by 138,000 users. In this dataset, each user is represented by an ID and no demographic information of the user is available. However, the published dataset contains only those users who have rated at least 20 movies. For movies, in addition to IDs, their titles and genre are also available. This dataset is most suitable for the CF technique.

### Jester

Jester [54] is a research project of UC Berkeley laboratory for Automation, Science and Engineering, to study social information filtering. The data are collected from Jester online recommendation website [55] and contains continuous ratings of jokes by anonymous users on a scale of -10 to +10. Multiple datasets have been collected over different time spans and are available on Jester's website. The largest among them is the size of 4.1 million ratings of 100 jokes by 73,421 users. This dataset is well-suited for CF in scenarios where a large number of users have rated a small number of items.

### BookCrossing

BookCrossing dataset [56] has been gathered through a four-week crawl from BookCrossing website [57]. The dataset contains 1,157,112 ratings of 271,397 distinct ISBNs, rated by 278,858 members of BookCrossing. The ratings are implicit and explicit with explicit ratings expressed on a scale of 1–10 and implicit ratings represented by zero. The dataset also contains some demographic information of users in the form of their Age and Location. Moreover, some content-based information of books, including book title, author, year of publication, and publisher, is gathered from Amazon website and is incorporated into this dataset. This dataset can, therefore, be used for both content-based and CF techniques of recommendation.

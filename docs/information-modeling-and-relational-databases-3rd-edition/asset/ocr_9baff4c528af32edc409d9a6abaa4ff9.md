these. SQL has long been accepted as an international standard and is commonly used for the communication of queries between different database systems. For this reason, SQL is the main query language discussed in this book.

Although relational systems give adequate performance for most applications, they are inefficient for some applications involving complex data structures (e.g., VLSI design).

Recently the XML has also become widely used for communication between different systems, but this is currently focused on sharing data for purposes such as electronic commerce and web publication. Many SQL-based DBMSs now support storing of XML data as well as querying XML data directly using a query language such as XQuery.

Data architectures exist for object-oriented databases, deductive databases (such as datalog systems), and ontological databases in languages such as OWL (Web Ontology Language). Many relational systems are being enhanced with object-oriented features, leading to object relational database systems. NoSQL systems are gaining popularity for efficiently handling high volumes of less-structured data.

# 1.4 The Relevant Skills

Because relational database systems are still dominant, they are the main focus of our implementation discussion, with some attention also being given to XML and other systems. Although conceptual interfaces to databases are still in their infancy, developing models at this higher level is more productive and avoids wasting time acquiring knowledge and skills that will rapidly become obsolete. Consider the impact of the electronic calculator on school mathematics curricula (e.g., removal of the general square root algorithm).

Fundamentally, there are two skills that will always be relevant to interacting with an information system. Both these skills relate to communicating with the system about our particular application area. Recall that the application domain is technically known as the UoD. The two requirements are to:

+   • describe the UoD

+   • query the system about the UoD

The first skill entails describing the structure or design of the UoD and describing its content or population: the structural aspect is the only challenging part. The ability to clearly describe the application domain is critical if you wish to add a model to the system. Complex models should normally be prepared by expert modelers working with domain experts. The main aim of this text is to introduce the fundamentals of information modeling. If you master the methods discussed, you will be well on your way to becoming an expert in modeling information systems.

Issuing queries is often easy using a 4GL, but the formulation of complex queries can still be difficult. Occasionally, the ability to understand some answers given by the system requires knowledge about how the system works, especially its limitations. This book provides a conceptual basis for understanding relational structures and queries, explains the algebra behind relational query languages, and includes a solid introduction to SQL.
Many common problems can be expressed in terms of searches through data space, and there are well-known algorithms to perform this in an efficient way. These capabilities make graph databases a popular choice in application areas such as the following:

+   - Modeling and querying social network data and other interpersonal relationships.
+   - Creating recommendations for users of a system by analyzing their preferences and activities.
+   - Identifying patterns of fraudulent behavior by analyzing connections between entities.
+   - Building knowledge graphs that represent semantic relationships between entities.
+   - Analyzing connections between individuals, organizations, and events in criminal investigations.

# 17.6 Other Nonrelational Databases

A conceptual schema may be mapped to various logical data models. The Rmap procedure discussed in Chapter 11 assumes that the application platform is a centralized, relational DBMS. It is a fairly simple task to specify other procedures for mapping to other types of DBMSs, as we've seen earlier in this chapter.

Although relational DBMSs have long been dominant in the commercial marketplace, many alternatives exist. These include older systems based on the hierarchic or network data model as well as newer alternatives such as those discussed previously. While purely relational DBMSs suit most business applications, they may not be the ideal match for some specialized applications such as computer-aided software engineering (CASE) tools, computer-aided design tools (e.g., VLSI design, mechanical engineering, architecture), document processing, spatial databases, expert systems, scientific databases (e.g., genetic engineering), and communications management. Note that most of these applications involve complex objects and probably account for at most 10% of database applications.

Many reasons are cited for dissatisfaction with purely relational DBMSs for complex applications. They may be too slow—they don't perform well with complex objects mainly because they require too many table joins. They often model objects in an unnatural way (e.g., information about a single object such as a person may be spread over several tables—this gets worse with complex objects). They are dependent on value-based identifiers. They don't facilitate reuse (e.g., they have no direct support for subtyping). They require access to a procedural language for difficult tasks (e.g., special rules and behavior), which leads to an “impedance mismatch” with the declarative, set-based, relational query language. They might not support binary large objects (BLOBs) such as images (icons, pictures, maps etc.), sound tracks, video, and so on.

# Object Orientation

An object database (ODB), or object-oriented database (OODB), incorporates various object-oriented features. Historically, ODB research drew upon related developments in
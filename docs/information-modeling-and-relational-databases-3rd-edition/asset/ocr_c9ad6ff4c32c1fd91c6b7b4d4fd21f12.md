creative response to this need can lead to major enhancements in the quality and efficiency of the business and its supporting information systems. Here, we consider only the problem of reengineering a database system. This process may be divided into four stages, as shown in Fig. 14.77.

![](bbox=[0.28, 0.195, 0.74, 0.395])

FIG. 14.77 Four steps in reengineering a database.

The first stage, conceptualization or reverse engineering, involves developing an initial conceptual schema of the application from the original database. This can be done simply by applying the CSDP to the database, treating it as a set of output reports. Most of the verbalization stage is usually straightforward because tables provide the easiest kind of output report to interpret. Usually, at least an incomplete logical schema for the database is also available, and constraints in this schema (e.g., primary and foreign key constraints) can be used to help derive some of the constraints in a fairly automatic fashion.

If the database is not relational, some of the intertable connections may need to be verbalized as fact types. Often, additional constraints that have not been specified will be identified with the assistance of the domain expert.

The second stage, transformation, involves modifying the original conceptual schema to cater for changes in the UoD not modeled in the original database, and/or optimizing the conceptual schema as discussed in the previous sections.

The third stage, mapping or forward engineering, takes us down to the logical schema. If a relational database system is to be used, we may use the Rmap procedure for this. The fourth stage, data migration, copies the facts stored in the original database to the new database. This involves conversion as well as copying because some of the fact types involved will be grouped into different table structures (recall the patient data example in Section 14.1). If the final two stages update the original database (rather than simply generating a new database), the whole reengineering process is called round-trip engineering or simply “round-tripping”.

Much of the reengineering process can be automated, especially if a very detailed database schema is provided at stage 1. However, human interaction is also required to ensure
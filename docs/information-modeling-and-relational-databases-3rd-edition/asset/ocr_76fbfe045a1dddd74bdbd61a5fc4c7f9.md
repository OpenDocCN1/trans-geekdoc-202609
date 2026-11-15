Student ( studentNr, studentName, degree )
Result ( studentNr_subjectCode, [rating] )

+   2. (a) Schematize this UoD including derivation. Note that external uniqueness constraints may be declared across any join path. If any subset constraints apply (possibly from a join), specify them. Ensure that the fact types are all elementary.
+   (b) Rmap your solution.
+   (c) Discuss whether a denormalized relational schema may be more appropriate.

# 14.8 Reengineering

While conceptual modeling provides the best approach to developing new applications, it can also be used to remodel existing systems to better meet requirements. There are three main reasons for replacing or revising (perhaps drastically) an existing information system.

First, the current system might provide an incorrect model of the UoD, either by being inaccurate (wrong information) or by being incomplete (missing information). Wrong or missing fact types, constraints, and derivation rules might arise because of bad modeling in the first place. For example, the schema might assert that planets orbit moons, allow people to have more than one birth date, or derive ages from a simple formula that ignores the extra day in leap years.

Such errors can also arise because the model has not kept pace with changes in the UoD. For example, a system for recording academic results based on a seven-point numeric rating scale becomes outdated if the rating scheme is replaced by a five-point letter grade.

Second, the existing system might be inefficient. It might be too slow (e.g., too many table joins needed in queries), too large (e.g., too many nulls gobbling up space), or difficult to evolve (e.g., outdated rules hardwired into program code rather than modeled as data in tables). Perhaps the hardware platform itself is outmoded and needs to be replaced, or the external interface is awkward for users.

Finally, the existing system might be unclear. This also makes it hard to maintain or evolve. Many legacy systems in place today were designed at the logical, or even physical, level and have no conceptual schema formulated for them. They may have been developed completely in 3GLs, with no underlying design method, have little or poor documentation, and be riddled with misleading or cryptic identifiers.

Often, a combination of the three reasons leads to an information system that needs to be reengineered, or restructured, for its owner (e.g., a company) to remain competitive in today's marketplace. The company might even reengineer the very way it does business. Although the need for restructuring is sometimes used as an excuse for retrenching, a
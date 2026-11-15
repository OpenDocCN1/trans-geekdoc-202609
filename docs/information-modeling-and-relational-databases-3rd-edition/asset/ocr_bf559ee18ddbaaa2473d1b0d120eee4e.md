# # Schema Transformations

# ## Chapter Outline

+   14.1 Schema Equivalence and Optimization
+   14.2 Predicate Specialization and Generalization
+   14.3 Nesting, Coreferencing, and Flattening
+   14.4 Other Transformations
+   14.5 Conceptual Schema Optimization
+   14.6 Normalization
+   14.7 Denormalization and Low-Level Optimization
+   14.8 Reengineering
+   14.9 Data Migration and Query Transformation
+   14.10 Summary

# ## 14.1 Schema Equivalence and Optimization

Previous chapters discussed how to model the structure of an application in terms of a conceptual schema, and then map it to a logical schema for implementation in a relational database system. Although much of the design and mapping can be automated, humans are required to perform conceptual schema design procedure (CSDP) step 1 because validating the relevant facts about the real world involves human understanding. Given the informal nature of this initial step in modeling the universe of discourse (UoD), it is not surprising that people often come up with different ways of describing the same reality.

Hence, the same business domain may be modeled by more than one conceptual schema. Moreover, the same conceptual schema may be mapped in different ways to a logical schema, either by choosing a different type of logical model (e.g., object relational) or by overriding the default mapping choices (e.g., choosing separate subtype tables or denormalizing). Finally, the same logical schema may be implemented in more than one way in the physical schema (e.g., different index choices).

To help you choose from such a variety of different designs, this chapter examines various ways in which schemas may be transformed to provide alternatives and then presents guidelines for optimizing your choice. On the way, we'll cover some theory on schema transformations and normalization to ensure a proper understanding of the underlying concepts. We'll start at the conceptual level and then move down to the logical and physical levels. Examples will illustrate how the ideas can also be used to reengineer existing applications that proved unsatisfactory.
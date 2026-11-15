The rest of this chapter provides an overview of ORM’s CSDP and a detailed discussion of the first three steps in this procedure. The ORM approach has been used productively in industry since the mid-1970s. Details of its history can be found in the chapter notes.

# ## 3.2 Conceptual Schema Design Procedure

When developing an information system, we first specify what is required and produce a design to meet these requirements. We recommend first developing this design at the conceptual level using ORM. This entails describing the structure of the universe of discourse (UoD) formally in terms of an ORM conceptual schema. If an ORM context is understood, we’ll often shorten “ORM conceptual schema” to just “conceptual schema”.

The procedure for designing a conceptual schema small enough to manage as a single unit is referred to as the **Conceptual Schema Design Procedure** (CSDP). Large business domains are first divided into subareas (which may overlap). These subareas are normally prioritized to determine which ones to develop first, and a conceptual *subschema* is designed for each using the CSDP.

With a team of modelers, a consensus on terminology is reached, so the same names are used for the same concepts. Later, the subschemas are *integrated* or merged into a global conceptual schema that covers the whole UoD. This integration is often performed iteratively.

This top-down design approach may be summarized as follows:

+   - Divide the universe of discourse into manageable subareas.
+   - Apply the CSDP to each subarea.
+   - Integrate the subschemas into a global conceptual schema.

For each manageably sized business domain or subarea, the conceptual schema design is performed in **seven steps**, as listed below. Often, all seven steps are performed for each model component as it is discussed with the domain expert, rather than applying step 1 to all components, then step 2 and so on.

+   1. Transform familiar examples into elementary facts.
+   2. Draw the fact types, and apply a population check.
+   3. Check for entity types to be combined, and note any arithmetic derivations.
+   4. Add uniqueness constraints, and check the arity of fact types.
+   5. Add mandatory role constraints, and check for logical derivations.
+   6. Add value, set-comparison, and subtyping constraints.
+   7. Add other constraints and perform final checks.

A **fact** (or *fact instance*) is a proposition that is taken to be true by users in the business domain. Whether the proposition is actually true in the UoD is of no concern to the information system. Here, “taken to be true” has the sense of epistemic commitment, that is, the business users are prepared to act as if they believed the assertion is true.
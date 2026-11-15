We have now covered all the basic steps in the Rmap procedure. Even if you are using a CASE tool to do the mapping for you, it's nice to understand how the mapping works. The basic steps in the relational mapping procedure are summarized below.

# Basic Rmap procedure:

+   0 Absorb subtypes into their top supertype.
+      Mentally erase all explicit preferred identification schemes,
+      treating compositely identified object types as "black boxes".
+   
+   1 Map each fact type with a compound UC [box] to a separate table.
+   
+   2 Fact types with functional roles attached to the same object type [circle-line-circle]
+      are grouped into the same table, keyed on the object type's identifier.
+      Map 1:1 cases to a single table, generally favoring fewer nulls.
+   
+   3 Map each independent object type with no functional roles to a separate table.
+   
+   4 Unpack each "black box column" into its component attributes.
+   
+   5 Map all other constraints and derivation rules.
+      Subtype constraints on functional roles map to qualified optional columns,
+      and those on nonfunctional roles map to qualified subset constraints.
+      Nonfunctional roles of independent object types map to column sequences
+      that reference the independent table.

Step 0 may be thought of as a preparatory mental exercise. Erasing all explicit preferred reference schemes (i.e., those shown other than by parenthesized reference modes) ensures that all the remaining predicates on display (as box sequences) belong to fact types (rather than reference types).

Recall that a *compositely identified object type* is either a nested object type (objectified association) or a coreferenced object type (identified via an external uniqueness constraint).

There are plenty of questions in the section exercise to give you practice at performing the mapping manually. As preparation for this exercise, some larger examples are now considered.

Fig. 11.27 shows the conceptual schema for the compact disc case study discussed in Chapter 5. If you feel confident, you might like to try mapping this to a relational schema yourself before reading on.

As there are no subtypes in this example, step 0 amounts to mentally erasing any preferred reference schemes that are shown explicitly. There are only two, each involving a compositely identified object type: Track and Listing.

Fig. 11.28 depicts this erasure by removing the predicate boxes and showing their connections to object types as dashed lines. For steps 1–3, we treat these two compositely identified entity types just like any other entity type.

We now proceed to group the asserted fact types into tables. To help visualize this, we *place a lasso around each group of predicates that maps to the same table* (see Fig. 11.28). We lasso only the predicates, not the object types. Because each fact type should map to exactly one table, *all predicates must be lassoed*, and *no lassos may overlap*.

In step 1, we look around for a predicate with a compound uniqueness constraint. Because the objectified association is now hidden, we see only one such predicate: is sung by. So, we lasso this predicate, indicating it goes to a table all by itself.
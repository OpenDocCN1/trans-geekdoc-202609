
![](img/1344db3eba3d550e6edb009556fcd95c_530_0.png)

```
Patient ( patientNr, patientName, gender, [phone], [prostateStatus]¹, [nrPregnancies]² )
¹ exists only if gender = 'M'
² exists iff gender = 'F'
```

FIG. 11.25 Subtype constraints on functional roles map to qualified optionals.

Some limited support for subtyping is included in the SQL standard, but current relational systems typically do not support this concept directly. Nevertheless, there are three main ways in which subtyping can be implemented on current systems: absorption, separation, and partition. With _absorption_, we _absorb the subtypes back into the (top) supertype_ (giving _qualified optional roles_), _group the fact types as usual_, and then _add the subtyping constraints as textual qualifications_, as shown in Fig. 11.25.

To best understand this example, visualize the subtypes on the conceptual schema absorbed back into the supertype Patient, with the subtype roles attached as qualified optional roles to Patient. All the roles attached to Patient are functional, so the fact types all map to the same table, as shown. The phone, prostateStatus, and nrPregnancies attributes are all optional, but the latter two are qualified.

In the qualifications, “exists” means the value is not null. Qualification 1 is a pure subtyping constraint, indicating that a nonnull value for prostate status is recorded **only if** the value of gender on that row is “M”. Some men might have a null recorded here. Qualification 2 expresses both a subtype constraint (number of pregnancies is recorded **only if** gender is “F”) and a mandatory role constraint (nrPregnancies is recorded **if** gender is “F”). Recall that “iff” is short for “if and only if”.

Because only functional fact types are involved in this example, the absorption approach leads to a table that basically matches that of the original output report (except that most relational systems support only one kind of null). The main advantage of this approach is that it maps all the functional predicates of a subtype family into a single table. This usually makes related queries and updates more efficient. Its main disadvantage is that it generates nulls.

The second main approach, separation, creates separate tables for facts with subtype-specific functional roles. With this approach, the conceptual schema of Fig. 11.25 maps to three tables: one for common facts, one for male-specific facts, and one for female-specific facts.

The third main approach, partition, may be used when the subtypes form a partition of their supertype. Because MalePatient and FemalePatient are exclusive and exhaustive, this approach may be used here, resulting in two tables: one with the facts about the male patients and the other with facts about female patients.

The next section discusses the relative merits of these three approaches and considers mapping cases where subtypes use a preferred identification scheme different from the supertype’s. Our default approach, however, is to absorb the subtypes before grouping.

Even with this approach, any fact types with a nonfunctional role played by a subtype map to separate tables, with their subtype definitions expressed by qualified subset constraints targeting the main supertype table.

For example, the ORM schema in Fig. 11.26 adds the optional m:n fact type FemalePatient attended prenatal clinic on Date. This fact type maps to a separate table with the qualified subset constraint “only where gender = 'F'”, as shown. If the new fact type were instead mandatory for FemalePatient, the qualification would read “exactly where” instead of “only where”.

![](img/1344db3eba3d550e6edb009556fcd95c_531_0.png)

```
Patient ( patientNr, patientName, gender, [phone], [prostateStatus] 1, [nrPregnancies] 2 )
PreNatalVisit ( patientNr, attendanceDate )
1 exists only if gender = 'M'
2 exists iff gender = 'F'
3 only where gender = 'F'
```

FIG. 11.26 Nonfunctional fact type of subtypes map to separate tables.

We have now covered all the basic steps in the Rmap procedure. Even if you are using a CASE tool to do the mapping for you, it's nice to understand how the mapping works. The basic steps in the relational mapping procedure are summarized below.

## Basic Rmap procedure:

- 0 Absorb subtypes into their top supertype.
  - Mentally erase all explicit preferred identification schemes, treating compositely identified object types as "black boxes".
- 1 Map each fact type with a compound UC [box] to a separate table.
- 2 Fact types with functional roles attached to the same object type [circle-line-circle] are grouped into the same table, keyed on the object type's identifier. Map 1:1 cases to a single table, generally favoring fewer nulls.
- 3 Map each independent object type with no functional roles to a separate table.
- 4 Unpack each "black box column" into its component attributes.
- 5 Map all other constraints and derivation rules.
  - Subtype constraints on functional roles map to qualified optional columns, and those on nonfunctional roles map to qualified subset constraints.
  - Nonfunctional roles of independent object types map to column sequences that reference the independent table.

Step 0 may be thought of as a preparatory mental exercise. Erasing all explicit preferred reference schemes (i.e., those shown other than by parenthesized reference modes) ensures that all the remaining predicates on display (as box sequences) belong to fact types (rather than reference types).

Recall that a *compositely identified object type* is either a nested object type (objectified association) or a coreferenced object type (identified via an external uniqueness constraint).

There are plenty of questions in the section exercise to give you practice at performing the mapping manually. As preparation for this exercise, some larger examples are now considered.

Fig. 11.27 shows the conceptual schema for the compact disc case study discussed in Chapter 5. If you feel confident, you might like to try mapping this to a relational schema yourself before reading on.

As there are no subtypes in this example, step 0 amounts to mentally erasing any preferred reference schemes that are shown explicitly. There are only two, each involving a compositely identified object type: Track and Listing.

Fig. 11.28 depicts this erasure by removing the predicate boxes and showing their connections to object types as dashed lines. For steps 1–3, we treat these two compositely identified entity types just like any other entity type.

We now proceed to group the asserted fact types into tables. To help visualize this, we *place a lasso around each group of predicates that maps to the same table* (see Fig. 11.28). We lasso only the predicates, not the object types. Because each fact type should map to exactly one table, *all predicates must be lassoed*, and *no lassos may overlap*.

In step 1, we look around for a predicate with a compound uniqueness constraint. Because the objectified association is now hidden, we see only one such predicate: is sung by. So, we lasso this predicate, indicating it goes to a table all by itself.

![](img/1344db3eba3d550e6edb009556fcd95c_533_0.png)

- For each Month, totalQtySold = sum(listing.nrSold).
- For each Month, totalProfit = sum(listing.profit).

FIG. 11.27 The conceptual schema from the compact disc case study.

![](img/1344db3eba3d550e6edb009556fcd95c_533_1.png)

FIG. 11.28 The reference types are erased, and fact types are lassoed into groups.

In step 2, we group functional fact types of the same object type together. For example, CompactDisc has five functional roles attached to it, so these five fact types are grouped into a table keyed on the identifier for CompactDisc. Similarly, the two functional fact types for Track are lassoed together, as are the two functional fact types of the nested object type.

This example has no 1:1 cases, and no independent object types. We have now roped all the predicates, and there are four lassos, so the conceptual schema maps to four tables.

The final relational schema is shown in Fig. 11.29. Because five functional fact types map to the CD (CompactDisc) table, and all the objects involved have simple identifiers, this table has six columns (one for the key and one for each fact attribute).

The other three tables involve a compositely identified object type, which is unpacked into its component attributes (step 4).

```
Sales   (cdNr, monthCode, qtySold, revenue)
        .......
CD      (cdNr, cdName, [artist], company, stockQty, rpp)
        ....^....
Track   (cdNr, trackNr, title, duration)
        ....^....
Vocals  (cdNr, trackNr, singer)
*
* SalesTotals(monthCode, totalQtySold, totalRevenue) ::
        monthCode, sum(qtySold), sum(revenue)
        from Sales
        group by monthCode
```

FIG. 11.29 Relational schema mapped from the conceptual schema in Fig. 11.27.

The keys of the tables are already determined, but the mandatory role constraints are enforced by mandatory columns and intertable subset/equality constraints. Note the composite subset constraint from the pair cdNr, trackNr in Vocals to the primary key of Track. Finally, the two derivation rules are mapped (step 5).

If you lasso fact types into groups before writing down the table schemes, you may mentally erase all preferred identification schemes (including reference modes) in step 0 (thus treating all object types as black boxes) and then in step 4 replace each column by its identifying attribute(s). This alternative formulation of the Rmap procedure is logically cleaner. If performing Rmap manually, you might find it convenient to photocopy the conceptual schema and use colored pencils to cross out the reference types and lasso the fact types.

As a complicated example, consider the ORM schema in Fig. 11.30. This concerns television channels. Notice that TimeSlot is modeled as a coreferenced entity type (a time slot is identified as a given hour on a given day). For variety, the object types Office and Department are modeled as objectified associations. A television channel may have different offices in different suburbs. For this UoD, a channel may have only one office in any given suburb. A given office may have many departments.

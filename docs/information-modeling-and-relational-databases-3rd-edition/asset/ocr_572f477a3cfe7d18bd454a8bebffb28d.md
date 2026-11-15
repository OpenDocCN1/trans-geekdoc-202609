In step 2, we group functional fact types of the same object type together. For example, CompactDisc has five functional roles attached to it, so these five fact types are grouped into a table keyed on the identifier for CompactDisc. Similarly, the two functional fact types for Track are lassoed together, as are the two functional fact types of the nested object type.

This example has no 1:1 cases, and no independent object types. We have now roped all the predicates, and there are four lassos, so the conceptual schema maps to four tables.

The final relational schema is shown in Fig. 11.29. Because five functional fact types map to the CD (CompactDisc) table, and all the objects involved have simple identifiers, this table has six columns (one for the key and one for each fact attribute).

The other three tables involve a compositely identified object type, which is unpacked into its component attributes (step 4).

```
Sales   (cdNr, monthCode qtySold, revenue)
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
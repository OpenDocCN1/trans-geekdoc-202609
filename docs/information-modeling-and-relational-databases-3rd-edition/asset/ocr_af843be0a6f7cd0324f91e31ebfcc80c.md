The second main approach, separation, creates separate tables for facts with subtype-specific functional roles. With this approach, the conceptual schema of Fig. 11.25 maps to three tables: one for common facts, one for male-specific facts, and one for female-specific facts.

The third main approach, partition, may be used when the subtypes form a partition of their supertype. Because MalePatient and FemalePatient are exclusive and exhaustive, this approach may be used here, resulting in two tables: one with the facts about the male patients and the other with facts about female patients.

The next section discusses the relative merits of these three approaches and considers mapping cases where subtypes use a preferred identification scheme different from the supertype’s. Our default approach, however, is to absorb the subtypes before grouping.

Even with this approach, any fact types with a nonfunctional role played by a subtype map to separate tables, with their subtype definitions expressed by qualified subset constraints targeting the main supertype table.

For example, the ORM schema in Fig. 11.26 adds the optional m:n fact type FemalePatient attended prenatal clinic on Date. This fact type maps to a separate table with the qualified subset constraint “only where gender = ’F’”, as shown. If the new fact type were instead mandatory for FemalePatient, the qualification would read “exactly where” instead of “only where”.

![](bbox=[0.18, 0.52, 0.8, 0.72])

```
Patient ( patientNr, patientName, gender, [phone], [prostateStatus] 1, [nrPregnancies] 2 )
PreNatalVisit ( patientNr attendanceDate )
1 exists only if gender = 'M'
2 exists iff gender = 'F'
3 only where gender = 'F'
```

FIG. 11.26 Nonfunctional fact type of subtypes map to separate tables.
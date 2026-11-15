However, the table in Fig. 14.60(b) is not in 3NF because population depends on birth-country, and these are both nonkey attributes. Note that population is transitively dependent on the key (studentNr determines birthcountry, and birthcountry determines population). This table exhibits redundancy: the fact that the United States has a population of 301,139,947 is shown twice. To avoid this redundancy, the fact type underlying the FD between the nonkey attributes is split off to another table, as in Fig. 14.61, which shows both ORM and relational schemas for the example.

![](bbox=[0.18, 0.25, 0.83, 0.315])

FIG. 14.61 Conceptual schema and correct relational schema for Fig. 14.60(b).

Now consider the table in Fig. 14.62, which is a modified version of an example used in Section 5.5 to illustrate the logical derivation check in the CSDP. If this CSDP step has been carried out properly, FDs from one nonkey attribute to another cannot arise in any tables obtained from Rmap. In the original Section 5.5 example, we split this table into two, one for the fact type Lecturer works for Department and one for the fact type Department is located in Building, deriving the fact type Lecturer works in Building iff Lecturer works for a Department that is located in Building.

Lecturer ( surname, department, building )

| | | |
|---|---|---|
| Halpin | CS | 69 |
| Okimura | JA | 1 |
| Orlowska | CS | 69 |
| Wang | ? | 1 |
| Zelewski | ? | 2 |

FIG. 14.62 Are facts underlying the FD surname → building transitively derivable?

However, if the “only if” part of the “iff” in this biconditional is not satisfied, the two-table design loses information. For example, suppose that Wang and Zalewski don’t work for any department (e.g., they might be visiting lecturers). This situation is represented by the last two table rows in Fig. 14.62, using “?” to indicate a null. If we split the table in two as described earlier, it would be impossible to derive the facts about where Wang and Zelewski work.

The original work on normalization assumed that nulls do not occur, but this assumption is often false. If we agree with Codd (1990, p. 201) that nulls should be ignored when applying rules about FDs, then the FDs shown in Fig. 14.62 still exist; however, it is wrong to decompose this table into two, so this normalization step can be unsafe. The safest way to deal with such issues is at the conceptual level.
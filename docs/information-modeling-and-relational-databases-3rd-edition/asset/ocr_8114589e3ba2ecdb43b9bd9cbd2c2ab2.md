![](bbox=[0.373, 0.096, 0.656, 0.233])

FIG. 5.24 The three components are derived and stored.

# Table 5.9 Employee details.

| EmpNr | Employee Name | Room |
|---|---|---|
| 715 | Adams A | 69-301 |
| 139 | Cantor G | 67-301 |
| 503 | Hagar TA | 69-507 |
| ... | ... | ... |

current form, a separate system (e.g., a data warehouse) can be constructed to better support queries on the components. In copying the data from the legacy system to the new system, the codes are transformed into separate component fields.

How much of the semantics underlying an information-bearing name should be exposed in a conceptual schema depends on the queries we wish to issue.

For example, consider the output report shown in Table 5.9. Here, room numbers have the format _dd-ddd_ (where _d_ denotes a digit). The first two digits provide the building number for the room’s building, the third digit indicates the room’s floor (in this UoD no building has more than nine floors), and the last two digits comprise a serial number to distinguish rooms on the same floor.

If we never wish to query the information system about buildings or floors, it’s fine to model rooms using the simple reference scheme Room.(nr). Now suppose instead that we also expect the system to output reports such as the extract shown in Table 5.10. Here, we _are_ interested in buildings, and we want to list the number of rooms _for each_ building. In this case, we must expose at least the building component of the reference scheme for buildings, as in Fig. 5.25.

# Table 5.10 Building details.

| BuildingNr | Building Name | Nr rooms |
|---|---|---|
| ... | ... | ... |
| 67 | Plently | 100 |
| 68 | Chemistry | 100 |
| 69 | Computer Science | 150 |
| ... | ... | ... |
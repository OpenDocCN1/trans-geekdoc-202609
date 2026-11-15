```
PlantKind ( plantKindNr. genus, [ species, [infraRank, infraName] ], author )

DisplayedIn ( plantKindNr, museum )
```

This approach has two main advantages: the primary keys have no nulls, and table joins are faster (now based just on plantKindNr). The artificial identifier option is not all good news. The secondary key in PlantKind still has optional fields. Moreover, because this secondary key uses the natural reference scheme, this is what users will normally want to see (not the artificial PlantKindNr). For example, to find what kinds of plants are on display in a museum, we now need to join the tables because we want to see the natural plant names.

A simpler solution is just to concatenate the formerly separate parts of the identifier into a single name. This leads to the very simple relational schema:

```
PlantKind ( plantKindName, author )

DisplayedIn ( plantKindName, museum )
```

This simple schema is the best solution if we don't need to list or group the formerly separate parts of the identifier. However, if we wanted to issue a query such as “Which species has the most plant kinds?” there is now no simple way to do this.

The third option is to keep the original components of the reference scheme separate but make each of them mandatory by using special default values when no actual value exists. For example, the plant kind *acacia interior* could be stored as the tuple (“acacia”, “interior”, “nil”, “nil”) using “nil” as a special default value (different from null) to indicate that plant kind has no actual value for infraRank and infraName. The conceptual schema in Fig. 11.48 is modified by making the species and infraspecies predicates mandatory for PlantKind, deleting the subset constraint, and adding “nil” to any value list for Rank, e.g., {“ssp”, “var”, “forma”, “n-ssp”, “n-var”, “n-forma”, “nil”}. The following relational schema is obtained (value-list omitted):

```
PlantKind ( genus, species, infraRank, infraName, author )

DisplayedIn ( genus, species, infraRank, infraName, museum )
```

In this case, the default value “nil” is unlikely to ever be confused with an actual value. However, in some cases, such confusion might arise (e.g., a default score of 0) and the user
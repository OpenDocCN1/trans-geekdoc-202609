![](bbox=[0.17, 0.09, 0.8, 0.28])

FIG. 11.48 PlantKind has a disjunctive reference scheme.

For symmetric 1:1 binaries (roles are both optional or both mandatory, and both object types have other functional roles), we have a choice as to how the 1:1 binary should be mapped. This mapping choice should be noted in step 0.5 (e.g., by annotation or option selection) and adhered to when the fact type is mapped in step 2.

In rare cases, a conceptual schema may include a disjunctive preferred reference scheme (identification by a mandatory disjunction of two or more roles, at least one of which is optional). In Fig. 11.48, PlantKind is identified in this way (this botanical naming convention was discussed in Chapter 5). When mapped to a relational schema, such schemes can prove awkward to handle.

For example, the conceptual schema in Fig. 11.48 maps to the following relational schema. This violates the relational entity integrity rule because the primary keys may contain nulls. We enclose both infraRank and infraName in the same pair of square brackets to indicate that the qualification applies to *both*, and that if one is null so is the other. Enclosing both these inside the option brackets for species indicates that they can only be given a nonnull value when species is nonnull.

```
PlantKind   ( genus.[species.[infraRank, infraName]], author )
DisplayedIn ( genus.[species.[infraRank, infraName]] museum )
```

Although forbidden by the relational model, this is allowed in most relational database systems (which permit tables without primary keys), and the relevant uniqueness constraint can be enforced by a procedure or assertion. However, a simpler implementation can often be obtained by altering the conceptual schema to replace the disjunctive reference with a nondisjunctive one. In step 0.6, we consider such replacements.

There are three basic ways of replacing a disjunctive reference scheme: artificial identifiers, concatenated identifiers, or use of special default values. Let's look at these three alternatives briefly, using this botanical example. The first option is to introduce a new identifier for PlantKind (e.g., PlantKindNr), leading to the following relational schema.
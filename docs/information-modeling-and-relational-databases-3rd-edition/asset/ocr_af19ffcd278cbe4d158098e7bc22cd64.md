Unfortunately, the HasKey feature only partly addresses the need to specify identification schemes (simple or compound) for entity types because HasKey captures only the inverse functional nature of the data property.

The name choice “HasKey” for this feature is somewhat misleading, as it is weaker than the notion of “key” in relational databases. To fully capture the identification scheme, we need to explicitly declare the data property to be both functional and mandatory.

In Manchester syntax, the mandatory role constraint that each Politician has a name is expressed by using the SubClassOf property to declare that Politician is a subclass of those things that play the subject role in the hasPoliticianName predicate with a minCardinality of 1 (or more), as follows:

```
Class: Politician
SubClassOf: hasPoliticianName min 1.
```

A maxCardinality of 1 may be declared in a similar way using max 1, which is another way to declare that the predicate is functional. If minCardinality = maxCardinality, you can set both at once using exactCardinality. For example, the 1:1 reference scheme for Politician may be declared in OWL 2 as follows:

```
Class: Politician
SubClassOf: hasPoliticianName exactly 1.
HasKey: hasPoliticianName
DataProperty: hasPoliticianName
Domain: Politician
Range: PoliticianName
```

As a composite identification scheme example, consider the ORM schema in Fig. 18.25(a). Here, each building is identified by its building number, and each room is identified by combining its local room number with its building.

![](bbox=[0.16, 0.63, 0.5, 0.73])

```
(b) Class: Room
SubClassOf: isInBuilding exactly 1.
SubClassOf: hasRoomNr exactly 1.
HasKey: isInBuilding, hasRoomNr
ObjectProperty: isInBuilding
Domain: Room
Range: Building
DataProperty: hasRoomNr
Domain: Room
Range: RoomNr
Class: Building
SubClassOf: hasBuildingNr exactly 1
HasKey: hasBuildingNr
DataProperty: hasBuildingNr
Domain: Building
Range: BuildingNr
```

FIG. 18.25 An ORM schema where Room has a composite reference scheme.
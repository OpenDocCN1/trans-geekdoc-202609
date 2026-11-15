However, some constraints have to be specified textually no matter how we choose our fact types. For example, directly linked nodes belong to the same network. If each network is to be continuous (no gaps), a constraint for this also needs to be declared textually. You are invited to express such constraints (and any others) formally.

As an exercise, try to model the linkage information using node position numbers instead, and notice the impact on constraints and derivation rules. Note that this absolute position approach makes it more awkward to add or delete nodes in the network because global changes to positional information would be required.

For instance, if we add a node, say D, between F and E, then not only will D be assigned the position 2, but nodes E, C, and B will all need to have their position numbers increased by 1. With our previous approach, only a local change would be needed. Swapping nodes is simple with both approaches. As an exercise, set out the compound transactions for some sample updates.

# Exercise 7.4

+   1. (a) Rugby union teams have 15 positions, numbered 1 through 15. Teams are identified by name. Players have names (not necessarily unique) and are identified by their position in the team. Each player is a member of exactly one team and has exactly one position. It is possible for any team that not all of its 15 positions are currently filled. Specify an ORM schema to store membership details for multiple teams. (b) Now restrict the UoD to a single team, whose name must still be recorded. (c) Now restrict the UoD to a single team, whose name is not recorded.

+   2. A given company always has exactly one head employee, and each employee other than the head reports to exactly one employee. The reporting relationship is acyclic. Schematize this situation.

+   3. Schematize the following table about the current age categories for humans. Unpack the semantics of ranges, and include any applicable graphical constraint.

| Age category | Age range (y) |
|---|---|
| Child | 0..14 |
| Youth | 15..24 |
| Adult | 25..64 |
| Senior | 65..140 |

+   4. A television survey on soap operas is conducted. Participants in this survey are identified by a number. Their gender is recorded as well as what soap operas they watch. Women may nominate all the soap operas they watch, if any, but to be included in the survey each man must specify exactly one soap opera. Model this UoD.
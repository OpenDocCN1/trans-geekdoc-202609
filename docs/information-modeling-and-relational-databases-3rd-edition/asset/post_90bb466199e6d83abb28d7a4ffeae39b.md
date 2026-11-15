

![](img/1344db3eba3d550e6edb009556fcd95c_465_0.png)

FIG. 10.42 Can you spot what is wrong with schemas (a) and (b)?

Both schemas omit the constraint that each role belongs to only one fact type. Fig. 10.42(a) requires each role list to belong to at most one fact type, but that’s not strong enough; the use of a collection list type here prevents us from capturing the required uniqueness constraint graphically. The ternary in Fig. 10.42(b) is not elementary (a uniqueness constraint applies to its second role). Fig. 10.42(c) provides a correct solution.

Recall that bags (multisets) are unordered collections with duplicates allowed. These may be implemented by ternary associations using a frequency object type to count the number of occurrences for each entry.

For example, suppose student 1001 obtains the bag of grades [A, A, B, B, B] in five tests, and student 1002 obtains the bag of grades [B, B, B] in three tests. This may be modeled in flat ORM as shown in Fig. 10.43(a). By default, multivalued association ends in UML denote sets (unique and unordered). Assuming that the nonunique setting is allowed here (the UML specification is unclear on this issue), a bag setting may be specified by the {nonunique} property, as shown in Fig. 10.43(b).

![](img/1344db3eba3d550e6edb009556fcd95c_465_1.png)

| 1001 | A | 2 |
|---|---|---|
| 1001 | B | 3 |
| 1002 | B | 3 |

FIG. 10.43 Modeling a bag of grades for each student in (a) ORM and (b) UML.

Recall that a sequence is an ordered bag (ordered collection with duplicates allowed). For example, a paragraph is a sequence of sentences. Sequences may be modeled in flat ORM using a ternary association with a “Position” object type in the key. Suppose a lottery presents prizes to a sequence of people, in descending order of prize value, with no ties. For example, the prizes for lottery L1 might be awarded to the sequence (Ann Smith, Tom Jones, Ann Smith). This may be modeled in flat ORM using Rank as a position type, as shown in Fig. 10.44(a), along with a sample population. Fig. 10.44(b) models this in UML using the {ordered, nonunique} setting, assuming this is allowed.

![](img/1344db3eba3d550e6edb009556fcd95c_466_0.png)

FIG. 10.44 Modeling a sequence in (a) flat ORM and (b) UML.

Arrays are indexed sequences. They may be modeled in flat ORM using a ternary with a “Position” type for the index as part of the key. For example, the ORM model in Fig. 10.45(a) uses Place as a position type to record the first three places in sporting events, assuming **no ties** are allowed.

Using a suitable mapping annotation, this could be mapped to an indexed array of countries inside sport events, leading to an object-relational database model such as

```
SportEvent ( eventName, results; array[1..3] of Country )
. ‘Mens 100 m freestyle’[1: ‘US’
2: ‘AU’
3: ‘US’]
```

![](img/1344db3eba3d550e6edb009556fcd95c_466_1.png)

FIG. 10.45 Modeling arrays of sporting event places with no ties in flat ORM.

Fig. 10.45(b) shows a similar example involving an additional uniqueness constraint (each country has at most one rank in any given sport). Again, no ties are allowed. This could be mapped to a unique array structure (with uniqueness indicated by underlining) as follows:

```
Sport ( sportName, results; array[1..3] of Country )
‘Swimming’ [1: ‘US’
2: ‘AU’
3: ‘CN’]
```

Although direct use of collection types in a conceptual model can lead to compactness, an alternative flat model (no constructors) of comparable convenience is generally available. The use of constructors often makes it harder to express constraints (which typically occur on members, not collections).

Because constructors involve compound facts, they are awkward to populate or check for validation, and they require more sophisticated modeling skills. Constructors are sometimes used even when there is a simpler modeling solution without them. It seems better to relegate constructor usage to annotations that guide the later mapping phase.

## Exercise 10.4

- 1. In Terry's Railway, each train consists of exactly one locomotive and exactly one carriage train (ordered set of railway cars). Each carriage is classified as first class, second class, or third class. It is possible that a carriage is not currently part of a train. Trains, carriages, and locomotives are identified by numbers. The same locomotive may power many trains.

- (a) The same carriage may belong to more than one train (e.g., a carriage used on a morning train may be used on a different train in the afternoon). However, the same carriage train can be used in only one train. Model this in ORM using a collection type constructor.

- (b) Model the domain described in (a) without using a collection type constructor.

- (c) Suppose now that each train is uniquely determined by its composition (i.e., its locomotive and carriage train). Is any change needed to your model for (a) to capture this? Explain.

- (d) Can this additional constraint be captured graphically in your solution to (b)? Answer yes or no.

- (e) The domain is changed so that each carriage belongs to at most one train. Can this rule be added as a graphic constraint (without adding a fact type) to your solution to (a)? Answer yes or no.

- (f) Remodel your solution to (b) to ensure that the rule in (e) is expressed graphically.

- (g) If the composition constraint in (c) also applies to your solution to (f), does any further constraint need to be added to that solution? Answer yes or no.

- 2. In cricket, a player may score runs in singles, fours, or sixes. Some players may score a duck (no runs). The following report extract lists a bag of runs (ignore the order) for each cricketer. Each cricketer belongs to exactly one team. Model this in flat ORM.

| Cricketer | Team | Runs |
|---|---|---|
| Don Superman | A | 6, 6, 6, 4, 4, 6, 4, 1, 6, 1, 6 |
| Fred Bloggs | A | 1, 1, 1, 1, 4, 1, 4, 1 |
| Mark Hitter | B | 1, 1, 1, 1, 4, 1, 1 |

## 10.5 Nominalization and Objectification

Roughly speaking, objectification or nesting treats a relationship instance as an object in its own right, so it may be talked about like any other object. In UML this is called reification, where instances of an association are objectified as instances of an association class. The basic notion of objectification in ORM and UML was discussed in Chapters 4 and 9, respectively. Industrial ER typically provides no support for objectification. Some academic versions of ER support objectification, but typically with restrictions (e.g., objectified relationships may have attributes but cannot play in other relationships).

This section examines objectification in greater depth, first distinguishing two kinds of nominalization and then considering objectification of unary fact types and binary or longer associations that have a uniqueness constraint that doesn't span all its roles.

We treat nominalization as the recasting of a declarative sentence using a noun phrase morphologically related to a corresponding verb in the original sentence. Declarative sentences may be nominalized in different ways.

One common way is to use a gerund (verbal noun) derived from the original verb or verb phrase. For example, “Elvis sang the song ‘Hound Dog’” may be nominalized as “Elvis’s singing of the song ‘Hound Dog’”. Another way is to introduce a pronoun or description to refer back to the original (e.g., “that Elvis sang the song ‘Hound Dog’” or “the fact that Elvis sang the song ‘Hound Dog’”).

In philosophy, it is usual to interpret the resulting nominalizations as naming either corresponding states of affairs or corresponding propositions. In linguistics, further alternatives are sometimes included. For example, states of affairs might be distinguished into events and situations.

For information modeling purposes, we adopt the philosophical approach, ignoring finer linguistic distinctions, and classify all nominalizations into just two categories.

A situational nominalization refers to a state of affairs or situation in the business domain being modeled. A propositional nominalization refers to a proposition. We treat events (instantaneous) and activities (of short or long duration) to be special cases of a state of affairs.

The relationships among states of affairs, propositions, sentences, and communication acts have long been matters of philosophical dispute. At one extreme, states of affairs and propositions are sometimes argued to be identical. Some view logic as essentially concerned with the connection between sentences and states of affairs while others view its focus to be propositions as abstract structures. Our viewpoint on some of these issues is motivated pragmatically by the need to model information systems, and is now summarized.

We define a proposition as that which is asserted when a declarative sentence is uttered or inscribed. A proposition (e.g., Elvis sang Hound Dog) must be true or false (and hence is a truth bearer).

Intuitively, it seems wrong to say that a state of affairs (e.g., Elvis’s singing of Hound Dog) is true or false. Rather, a state of affairs is actual (occurs in the actual world, is the



Although it might sound hard to believe, if you have performed step 1 properly, you have completed the hardest part of the CSDP. The remaining steps consist of diagramming and constraining the fact types. Apart from the problem of detecting unusual constraints and derivation rules, once you learn the techniques you can often carry out those steps almost automatically. With step 1, however, you always need to draw upon your interpretation skills.

## Exercise 3.3

- 1. Assuming suitable entity types and reference modes are understood, which of the following sentences fit our standard pattern for expressing exactly one elementary fact?
- (a) Adam likes Eve.
- (b) Bob does not like John.
- (c) Tom visited Los Angeles and New York.
- (d) Tom visited Los Angeles or New York.
- (e) If Tom visited Los Angeles then he visited New York.
- (f) Sue is funny.
- (g) All people are funny.
- (h) Some people in New York have toured Australia.
- (i) Brisbane and Sydney are in Australia.
- (j) Brisbane and Sydney are in the same country.
- (k) Who does Adam like?

- 2. Indicate at least two different meanings for each of the following sentences by including names for object types and reference modes.
- (a) Pluto is owned by Mickey.
- (b) Dallas is smaller than Sydney.
- (c) Arnold can lift 300.

Perform step 1 of the CSDP for the following output reports. In verbalizing the facts, you may restrict yourself to the top row unless another row reveals a different kind of fact.

| Athlete | Height (cm) |
|---|---|
| Jones EM | 166 |
| Pie QT | 166 |
| Smith JA | 175 |

| Athlete | Height (cm) |
|---|---|
| Jones EM | 400 |
| Pie QT | 450 |
| Smith JA | 550 |

| Person | Height (cm) | Year |
|---|---|---|
| Jones EM | 166 | 1955 |
| Pie QT | 160 | 1970 |
| Smith JA | 175 | 1955 |

| Person | Height (cm) | Year |
|---|---|---|
| Jones EM | 160 | 1970 |
| | 166 | 1980 |
| | 166 | 1990 |

| Advisory panel | Internal member | External member |
|---|---|---|
| Databases | Codd Kowalski | Ienshtein Spock |
| Logic programming | Colmerauer Kowalski Spock | Robinson |

| Student Nr | Course | Rating |
|---|---|---|
| 1001 | CS112 | 7 |
| 1001 | CS100 | 6 |
| 1002 | CS112 | 4 |
| 1003 | CS100 | 7 |
| 1003 | CS112 | 4 |
| 1003 | MP104 | 4 |

| Parents | Children |
|---|---|
| Ann, Bill David, Fiona | Colin, David, Eve Gus |

| Country | Friends | Enemies |
|---|---|---|
| Disland Hades | Oz | Oz Wundrland Hades |
| Wundrland Oz | Oz Disland Wundrland | |

| Apple | Australia | June, July, August |
| | America | Oct, Dec, Jan |
| | Ireland | Oct, Dec |
| Mango | Australia | Nov, Dec, Jan, Feb |
| Pineapple | America | June, July |
| | Australia | Oct, Nov, Dec, Jan |

## 3.4 CSDP Step 2: Draw Fact Types and Populate

Once we have translated the information examples into elementary facts, and performed quality checks, we perform the next step in the CSDP. First, we draw a conceptual schema diagram that shows all the fact types. This illustrates the relevant object types, predicates, and reference schemes. Once the diagram is drawn, we check it with a sample population.

### CSDP step 2: Draw the fact types and apply a population check.

Consider the sample output report of Table 3.6.

| Person | Car |
|---|---|
| Adams B | 235PZN |
| Jones E | 235PZN |
| Jones E | 108AAQ |

Let us agree that the information in this report can be expressed by the following three elementary facts, using “RegNr” to abbreviate “registration number”:

- The Person named “Adams B” drives the Car with RegNr “235PZN”.
- The Person named “Jones E” drives the Car with RegNr “235PZN”.
- The Person named “Jones E” drives the Car with RegNr “108AAQ”.

Before looking at the relevant conceptual schema diagram, it may help to explain things if we first view an instance diagram for this example (see Fig. 3.8).

![](img/1344db3eba3d550e6edb009556fcd95c_107_0.png)

FIG. 3.8 An instance diagram.

Instance diagrams illustrate particular instances of objects and relationships. Taking advantage of the concrete nature of the entities in this example, cartoon drawings denote the actual people and cars. The values are shown as character strings. A particular fact or relationship between a person and a car is shown as a solid line. A particular reference between a value and an entity is shown as a broken line.

Fig. 3.9(a) shows a conceptual schema diagram for the same example, adding inverse readings for the two fact types. Instance diagrams and conceptual schema diagrams depict an entity type as a named, solid, soft rectangle (rectangle with rounded corners). A value type is shown as a named, broken, soft rectangle. The object type’s name is written inside. Some versions of ORM allow an ellipse (Fig. 3.9(b)) or a hard rectangle (Fig. 3.9(c)) instead of a soft rectangle.

On an instance diagram, individual objects are portrayed explicitly (by icons or text). However, on a conceptual schema diagram, individual objects are omitted (unless we reference them in associated tables). Recalling that a type is the set of permitted instances, we may imagine that objects are represented as points inside the type shape.

On a conceptual schema diagram, the roles (relationship parts) played by objects are shown explicitly as boxes. Optionally, roles may be given a name, in which case the role name is displayed in square brackets next to the role box, for example, “[driver]” in Fig. 3.9(a). Each predicate is depicted as a named, contiguous sequence of one or more role boxes (“contiguous” means the boxes are adjacent, with no gaps in between).

![](img/1344db3eba3d550e6edb009556fcd95c_108_0.png)

FIG. 3.9 (a) A conceptual schema (minus constraints) and (b and c) alternate shapes.

Predicates are typically ordered from one end to the other, with their reading displayed next to the predicate shape. For binary relationships (two roles), both forward and inverse predicate readings may be shown, separated by a slash “/”, as in Fig. 3.9(a).

Each predicate must have at least one reading displayed. If just one predicate reading is displayed, by default this is read left to right on a horizontal predicate and downward on a vertical predicate. Arrow tips may be added to a predicate reading to indicate the reading direction. For example, “◄” indicates the predicate reading is right to left, and “▲” indicates the reading direction is upward.

Each role is connected to exactly one object type by a line, indicating that the role is played only by objects of that type. A complete conceptual schema diagram includes the relevant constraints. We’ll see how to add these later.

A relationship used within the preferred identification scheme for an entity is called a reference or existential fact (e.g., There exists a car that has the car registration number “235PZN”).

All other conceptual schema relationships are called elementary facts (e.g., The person named “Adams B” drives the car with car registration number “235PZN”).

Typically, elementary facts are relationships between entities, and references are relationships between entities and values. References provide the bridge between the world of entities and the world of values. Simple references as well as elementary facts are both examples of _atomic facts_.

This is clearly seen in Fig. 3.10(a), where an instance has been added to populate each relationship. The relationship between the person and the car (depicted with icons) is an elementary fact. The relationship between the name “Adams B” and the person is a reference or existential fact, as is the relationship between the registration number “235PZN” and the car.

![](img/1344db3eba3d550e6edb009556fcd95c_109_0.png)

Although the predicate reading “has” may be used with fact types, it is best avoided if there is a more descriptive, natural alternative. For example, “Person drives Car”, if accurate, is better than “Person has Car”, which could mean many things (e.g., Person owns Car).

For this example, each person has exactly one name, and each person name refers to at most one person. Each car has exactly one car registration number, and each car registration number refers to at most one car. This situation is seen clearly in the earlier instance diagram, Fig. 3.8. Each of the two reference types is said to provide a _simple 1:1 reference scheme_. We read “1:1” as “one to one”. Later, we’ll see how to specify this on a conceptual schema diagram using uniqueness and mandatory role constraints.

When a simple 1:1 naming convention exists, we indicate the _reference mode_ by appending its name in _parentheses_ to the name of the entity type, and then use the values themselves to depict object instances in associated _fact tables_. Ignoring other constraints,

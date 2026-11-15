
The first three normal forms were originally proposed by E. F. “Ted” Codd, who founded the relational model of data. The other forms were introduced later to cater for additional cases. These improvements were due to the work of several researchers, including Codd, R. Boyce, R. Fagin, A. Aho, C. Beeri, and J. Ullman. Other normal forms have also been proposed (e.g., horizontal normal form and nested normal form) but are not discussed here.

A table is normalized, or in **first normal form** (**1NF**), if and only if its attributes are single valued and fixed. In other words, a 1NF table has a fixed number of columns, and each entry in a row-column position is a simple value (possibly null). Almost every table we’ve seen so far in this book has been in 1NF.

A table may violate 1NF (and hence be an NF² table) either by having multivalued attributes (e.g., entries that are a collection such as sets, arrays, or even relations) or by allowing different rows to have different numbers of attributes.

As an example of the first kind of violation, consider Table 14.7. While the first two columns in this Student table store only atomic values, the Car column stores sets of values, and the Result column holds sets of (course, rating) pairs.

To model this in a relational database, we need to flatten the structure out into three tables: Student( studentNr, gender ); Drives( studentNr, car ); and Scores( studentNr, course, rating ). Hence, 1NF relations are often called *flat relations*.

Table 14.7 A nested-relational structure.

| studentNr | gender | Car.regNr | Result.course | Result.rating |
|---|---|---|---|---|
| 1001 | F | ABC123 PKJ155 | CS100 CS114 PD102 | 6 7 6 |
| 1002 | M | | CS100 MA104 | 5 |

However, it is possible to model the structure directly by using a relation that is not in first normal form. For example, we might use the following *nested relation* scheme: Student ( studentNr, gender, Car( regNr ), Result( course, rating) ).

Here, an entry in the third column is itself a relation (here, a set of car registration numbers). Similarly, each entry in the Result column is a relation (with course and rating attributes). Because the logical data model underlying this approach allows relations to be nested inside relations, it is called the *nested relational model*.

Because the nested table is not in 1NF, it is not a relational table (i.e., it does not conform to the relational model of data). Although pure nested relational systems have yet to make any significant commercial impact, many of the major relational DBMSs have evolved into object-relational systems with support for NF² tables, as discussed in the next section. While tables not in 1NF might be in some other exotic “normal form”, it is common practice to refer to them as being “unnormalized”.

Set-valued fields such as Car in Table 14.7 are sometimes called “repeating attributes”, and fields such as Result that hold sets of grouped values are sometimes called “repeating groups”. This term may be used to include the notion of repeating attribute by allowing degenerate groups with one value. Using this somewhat misleading terminology, we may say that 1NF tables have no repeating groups.

Another example of an unnormalized table is the “variant record type” used in languages such as Pascal and Modula. Here, different “rows” in the same record type may contain different fields. For example, the figure record type in Fig. 14.57 is designed to store details about colored geometric figures. A sample data population is included. The record type includes common fields for figureId, color, and shape (circle, rhombus, triangle).

| figureId | color | shape | attribute1 | attribute2 | attribute3 |
|---|---|---|---|---|---|
| | | circle | radius | | |
| | | rhombus | side | angle | |
| | | triangle | side1 | side2 | side3 |
| F1 | red | circle | 15 | | |
| F2 | red | rhombus | 10 | 30 | |
| F3 | blue | triangle | 40 | 30 | 50 |
| ... | | | | | |

FIG. 14.57 A variant record type, with a sample population.

The record type has different remaining fields depending on the shape (radius for circle; side and angle for rhombus; three sides for triangle). This provides one way to implement a restricted notion of subtypes without using subclasses, as is common in modern object-oriented programming languages.

A key of a table is a set of one or more attributes spanned by an explicit uniqueness constraint. Here, “explicit” excludes any UCs that are implied by shorter UCs inside them; so, keys are spanned by “minimal” UCs. For a given relation, an attribute is a *key attribute* if and only if it belongs to some key (primary or secondary) of the relation. A *nonkey* attribute is neither a key nor a part of a composite key.

For example, consider the relation scheme City( cityNr, cityname, statecode, population, [mayor] ). Here, cityNr is the primary key and (cityname, statecode) is an alternate key. So cityNr, cityname, and statecode are key attributes. Although unique, the mayor attribute is not a key because it is optional. Because they don’t belong to a key, population and mayor are nonkey attributes.

Although definitions of normal form and related dependencies are often given in terms of relations (fixed sets of tuples), we should define them in term of *relation schemes* because we want the table structures to exhibit the desired quality for each possible population (this requires revised definitions for some of the higher normal forms). With this in mind, we define an FD over a relation scheme as follows. Given attributes X and Y of a relation scheme, X functionally determines Y (X → Y) if and only if, *given any possible* population of the table scheme, for each value of X there is only one value for Y. Attributes X and Y may be composite. To decide whether a population is possible for a business domain requires the understanding of a domain expert (an informal semantic issue, not a syntactic issue).

A table scheme is in **second normal form** (**2NF**) if and only if it is in 1NF and every nonkey attribute is (functionally) dependent on the whole of a key (not just a part of it). If a table is normalized, it is in at least 1NF. For example, the table in Fig. 14.58(a) is in 2NF because gender and birthdate are both functions of student number. Here, the FDs from studentNr are depicted as arrows.

The table in Fig. 14.58(b) is in 1NF but not 2NF because height, a nonkey attribute, is functionally dependent on athleteName, which is just part of the composite key. Note the redundancy: the fact that Jones E has a height of 180 cm is recorded twice.

![](img/1344db3eba3d550e6edb009556fcd95c_761_0.png)

FIG. 14.58 Table (a) is in 2NF but table (b) is not.

To avoid redundancy, we split the original Athlete table into two smaller ones, as in Fig. 14.59. This figure shows both conceptual and relational schemas for the example (assuming that the information is mandatory for athletes).

![](img/1344db3eba3d550e6edb009556fcd95c_761_1.png)

FIG. 14.59 Conceptual schema and correct relational schema for Fig. 14.58(b).

If you verbalized Fig. 14.58(b) correctly in terms of elementary facts, you would obtain this conceptual schema directly, and the relational schema would follow automatically using Rmap.

You would have to be a real novice to verbalize Fig. 14.58(b) in terms of a ternary, but suppose you did. The checks provided in the CSDP, especially steps 4 and 5, prompt you to split the ternary into two binaries.

If you were careless in applying the CSDP, you could end up with the ternary in your relational schema. At this stage, you could look for an FD coming from only part of a key, and use the 2NF normalization rule to at last correct your error. Even at this level, you should think in terms of the functional fact type behind the FD.

Recall that if fact types are elementary, all FDs are implied by UCs. This property is preserved by Rmap because it groups together only functional fact types with a common key. So, if we find an FD in a relational schema that is not implied by a UC, we must have gone wrong earlier. Because UCs imply FDs, every nonkey attribute is functionally dependent on any key of the relation. Note that to determine the hNF of a relation, we need to be told what the relevant dependencies are (e.g., keys and FDs) or have a significant population from which these may be deduced.

Although normalization to 2NF overcomes the redundancy problem in the original Athlete table, this reduces the efficiency of those queries that now have to access both the new tables. For example, if we want the name and height of all the hockey players, the 2NF design means that two tables must be searched and their athleteName fields matched. This kind of efficiency loss, which is common to each normalization refinement (each involves splitting), is usually more than offset by the higher degree of data integrity resulting from the elimination of redundancy.

For example, if we need to change the height of Jones E to 182 cm, and we record this change on only the first row of the original Athlete table, we now have two different values for the height. With more serious examples (e.g., defense, medical, business), such inconsistencies could prove disastrous.

As discussed in the next section, we sometimes denormalize by introducing controlled redundancy to speed up queries. Although the redundancy is then safe, control of the redundancy is more expensive to enforce than in fully normalized tables, where redundancy is eliminated simply by enforcing key constraints. In short, normalization tends to make updates more efficient (by making constraints easier to enforce) while slowing down queries that now require additional table joins.

Given attributes X and Y (possibly composite), if X → Y, then an update of X entails a possible update of Y. Within a relation, a set of attributes is *mutually independent* if and only if none of the attributes is (functionally) dependent on any of the others. The attributes may then be updated independently of one another.

![](img/1344db3eba3d550e6edb009556fcd95c_762_0.png)

FIG. 14.60 Table (a) is in 3NF; table (b) is in 2NF but not 3NF.

A table scheme is in **third normal form** (**3NF**) if and only if it is in 2NF and its *nonkey attributes are mutually independent*. Hence, in a 3NF table no FD can be transitively implied by two FDs, one of which is an FD between two nonkey attributes. For example, the table in Fig. 14.60(a) is in 3NF because there is no dependency between gender and birthdate.

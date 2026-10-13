
Candidate identifiers for the same entity are said to be *synonyms*. Some people use the term “*homonym*” for a label that refers to more than one entity. For example, the same surname “Jones” may refer to more than one person. Because “homonym” has different grammatical senses, another term such as “nonidentifying label” is preferable. At any rate, the “problem of homonyms” is solved either by augmenting the reference scheme until identification is achieved (e.g., combining surname and initials) or by using a completely different preferred identification scheme (e.g., Social Security number).

In our examples so far, an object’s reference scheme is the same throughout the whole schema. The next chapter examines some cases involving subtypes where this assumption is removed; this leads to *context dependent reference*. To end this section, we consider the case of variable reference where *different units are used for the same physical quantity* in the same application domain.

In Australia, pieces of lumber have their longest length specified in meters, but their breadth and depth are measured in millimeters. Because this is a standard in the Australian building industry, a report on lumber sizes might look like [Table 5.11](#Ch005_159-209_B9780443237904000098.xhtml#t0060). Suppose we want to compare the different linear measurements (e.g., Which sizes of lumber are 20 times as long as their breadth?) or compute volumes in standard units (e.g., What is the volume of lumber size C7 in cubic meters?). [Fig. 5.30](#Ch005_159-209_B9780443237904000098.xhtml#f0155)(a) shows one way to model this situation.

[Table 5.11](#Ch005_159-209_B9780443237904000098.xhtml#B-t0060)

Lumber details.

| ![t05-11-9780443237904](images/B9780443237904000098/t05-11-9780443237904.jpg) |

| --- |

![Fig. 5.30 Derived units are based on a standard unit.](images/B9780443237904000098/f05-30-9780443237904.jpg)

[Fig. 5.30](#Ch005_159-209_B9780443237904000098.xhtml#B-f0155) Derived units are based on a standard unit.

The asterisk “\*” after “(mm:)” indicates that millimeter (mm) is a *derived unit*, unlike meter (m), which is a *standard unit*. [Fig. 5.30](#Ch005_159-209_B9780443237904000098.xhtml#f0155)(b) displays the expanded form of the unit reference modes, with each unit based on the same *unit dimension* (Length). It also shows the *conversion rule* between the units, with the derived unit on the left of the “=” sign. We use the term “dimension” to include derived dimensions (e.g., Volume = Length³). Both sides of a conversion rule equation must have the same dimension (e.g., Length) or dimension expression (e.g., Mass/Volume).

Many units might be used for the same physical quantity. To reduce the number of conversion rules, we choose a standard unit and just supply rules to convert to this standard (rather than supply conversions between each unit pair).

ORM 2 regards object types with the same unit-based reference mode to be compatible. So, if Length and Pressure occur in the same model, it would be incorrect to use the reference schemes `Length(mm:)` and `Pressure(mm:)` because this implies that Length and Pressure are based on the same semantic domain. To avoid this problem, we need to rename one of the reference modes, for example, `Pressure (mmHg:)`.

As a more abstract approach, we could model the metadata (length, etc.) in [Table 5.11](#Ch005_159-209_B9780443237904000098.xhtml#t0060) as data, as shown in the populated model in [Fig. 5.31](#Ch005_159-209_B9780443237904000098.xhtml#f0160). The first fact from [Table 5.11](#Ch005_159-209_B9780443237904000098.xhtml#t0060) could then be expressed by the facts: `LumberSize “A4” has Attribute “length” of NumericValue 3`; `Attribute “length” has Unit “m”`. The unit conversion rule is still required. This technique is called *metadata demotion* because it demotes metadata (data about data) to domain data. While this approach is very powerful, it is often unnatural for most users. If used at all, it should normally be transformed into a simpler external schema for user interaction.

![Fig. 5.31 Demoting metadata to data.](images/B9780443237904000098/f05-31-9780443237904.jpg)

[Fig. 5.31](#Ch005_159-209_B9780443237904000098.xhtml#B-f0160) Demoting metadata to data.

As a simpler example of treating different units as values, a financial application involving many currencies might model amounts of money using the compound reference scheme `MoneyAmount(is in Currency(.code), has NumericValue())`.

Demoting metadata (types) to data (instances) can help to minimize changes to the schema over time. An abstract model such as [Fig. 5.31](#Ch005_159-209_B9780443237904000098.xhtml#f0160) might be used to permit new attributes to be added without altering the database schema. For example, a medical application might use the association `Patient has Attribute of Value` to anticipate new patient tests to be added later. In such cases, additional associations are often needed to control the use of units within their contexts.

Sometimes, we may need to work with multiple unit systems. For example, we may need both metric and nonmetric measures as users gradually move from one unit system to another, or merge separate applications. In addition to supplying conversion rules to transform between different units, we must take care to expose the units to humans interacting with the system (recall the fate of the Mars Climate Orbiter).

## Exercise 5.3

1.  It is desired to identify a warehouse by its physical location. Design an appropri­ate identification scheme for the each of the following contexts:

    1.  (a) UoD restricted to one suburb. The street in which the warehouse is located is identified by its name.

    2.  (b) UoD restricted to one city. Each suburb is identified by its name.

    3.  (c) UoD restricted to one country. Each city is a major city, identified by name.

    4.  (d) UoD restricted to planet Earth. Countries are identified by name.

    5.  (e) UoD restricted to Milky Way galaxy. Planets are identified by name.

2.  The UoD is restricted to Earth, and we wish to store facts of the form: `Warehouse has Floorspace`; `Warehouse contains Item in Quantity`. Is the identification scheme discussed in Question 1 (d) practical from the implementation point of view? If not, suggest a better scheme and support your scheme by comparing a sample population for the two fact types, using both approaches. Comment on the relative work needed to perform a join (conceptual or relational) between the fact types.

3.  (a) A triangle ABC is formed from points in a Cartesian coordinate system. The coordinates are pure numbers (no units). Assume that at any given time, only one shape can be displayed, which must be a triangle. Model the information displayed.

    ![](images/B9780443237904000098/u05-02-9780443237904.jpg)

    (b) The map shown here indicates the approximate location of parking stations near a famous cathedral. The squares on the grid represent city blocks. Model the parking information stored on this map.

    ![](images/B9780443237904000098/u05-03-9780443237904.jpg)

4.  Members of a small social club are identified by the combination of their given names and surname. Each member has at least one and at most three given names. For example, one member is Eve Jones, another is Johann Sebastian Bach, and another is Eve Mary Elizabeth Jones. It is required that each component of their names be individually accessible. Draw a conceptual schema diagram for this situation.

5.  Members of a small American gymnasium have their weight recorded in pounds (lb). The weight that each member can bench press is also recorded, but in kilograms (kg). It is desired to compare these two weights but retain the separate units. Specify a conceptual schema for this situation. Note that 1 lb = 0.454 kg and 1 kg = 2.205 lb.


![](img/1344db3eba3d550e6edb009556fcd95c_535_0.png)

FIG. 11.30 An ORM schema for TV channels.

For example, one department might be the advertising department for the channel 9 office located in the suburb Toowong. Alternatively (and arguably more naturally), the object types Office and Department could have been modeled as coreferenced object types. However, this would not change the mapping.

The external uniqueness constraint on Program indicates that a channel can screen only one program at a given time. As an exercise, try to map this yourself before reading on. Start by mentally erasing the reference types and lassooing the fact types that should be grouped together before you write down the relational schema.

Fig. 11.31 hides the identifying predicates for Time, Office, and Department, and lassoes the fact types into groups. The 1:1 associations must be grouped with Channel and Program because these have other functional roles, but Frequency and Title do not.

The detailed relational schema is shown in Fig. 11.32. The identifier for Office unpacks into two attributes while the Department key unpacks into three (two for Office and one for DepartmentKind). Notice also the intertable uniqueness constraint. This indicates that when a natural join is performed between the Program and ProgTime tables, there will be a uniqueness constraint spanning the three columns channelNr, progDay, and progHour. In other words, for any given channel and time, there is at most one program being shown.

Notice the many equality constraints in the relational schema. These lead to referential cycles that may be awkward to implement. The many mandatory roles also entail that a lot of data must be entered in a single transaction. As discussed earlier, to minimize referential cycles, you should not add a mandatory role constraint to a nonfunctional role unless it is absolutely required.

As an optional exercise, you may wish to consider which mandatory role constraints would best be removed from Fig. 11.30.

The following exercise contains many questions to give you practice with relational mapping. The choice of names for tables and columns is up to you, but you may wish to consider the naming guidelines discussed earlier.

| Relation | Attributes |
|----------|------------|
| Survey | ( channelNr, surveyNr_category, rating ) |
| Channel | ( channelNr, frequency, [worth] ) |
| Ownership | ( channelNr, companyName ) |
| Company | ( companyName, assets ) |
| Program | ( progCode, progTitle, channelNr ) |
| ProgTime | ( progCode, progDay, progHour ) |
| Office | ( channelNr, suburb, yearOpened ) |
| Department | ( channelNr, suburb, deptKind, nrStaff, [nrVacancies] ) |

FIG. 11.32 A relational schema mapped from the model in Fig. 11.30.

Mapping from a conceptual to a relational schema is a bit like doing CSDP step 1 in reverse. Try to choose names for tables and columns that would make it easier for you to perform conceptual schema design procedure (CSDP) step 1 if presented with the relational tables. Remember that tables are basically just collections of facts.

## Exercise 11.3

- 1. Map the following conceptual schema onto a relational schema using the Rmap procedure. Use descriptive table and column names. Underline the keys, and enclose any optional columns in square brackets. Indicate any subset or equality constraints.

![](img/1344db3eba3d550e6edb009556fcd95c_537_0.png)

- 2. Rmap the following conceptual schema.

![](img/1344db3eba3d550e6edb009556fcd95c_538_0.png)

- 3. (a) The conceptual schema for a given UoD is shown. A novice designer maps the likes and costs fact types into a single table: Likes ( woman, dress, cost ). With the aid of a small sample population, explain why this table is badly designed. Use surrogates w1, w2, ... for women and d1, d2, ... for dresses.
   (b) Rmap the conceptual schema.

![](img/1344db3eba3d550e6edb009556fcd95c_538_1.png)

- 4. In a given UoD, each lecturer has at least one degree and optionally has taught at one or more institutions. Each lecturer has exactly one identifying name, and at most one nick-name. Each degree is standardly identified by its code, but also has a unique title. Some degrees might not be held by any lecturer. Each institution is identified by its name. The gender and birth year of the lecturers are recorded as well as the years in which their degrees were awarded.
   (a) A novice designer develops the following relational schema for this UoD. Explain, with the aid of sample data why these tables are badly designed.
Lecturer ( lecturerName, gender, degreeCode, degreeTitle )
Qualification ( degreeCode, yearAwarded )
   (b) Draw a conceptual schema for this UoD.
   (c) Rmap your answer to (b).

- 5. Add constraints to your conceptual schema for the following and then perform Rmap.
   (a) Exercise 3.5, Question 2.
   (b) Exercise 3.5, Question 3.

- 6. Rmap the Invoice conceptual schema for Exercise 6.3, Question 3.

- 7. Rmap the Oz Bank conceptual schema for Exercise 6.4, Question 6.

- 8. Consider a naval UoD in which sailors are identified by a sailorNr and ships by a shipNr, although both have names as well (not necessarily unique). We must record the sex, rank, and birthdate of each sailor and the weight (in tonnes) and construction date of each ship. Each ship may have only one captain and vice versa. Specify a conceptual schema and relational schema for this UoD for the following cases.
   (a) Each captain commands a ship but some ships might not have captains.
   (b) Each ship has a captain but some captains might not command a ship.
   (c) Each captain commands a ship, and each ship has a captain.
   (d) Some captains might not command a ship, and some ships might not have captains.

- 9. Consider a UoD in which students enroll in subjects, and later obtain scores on one or more tests for each subject. Schematize this conceptually using nesting and then Rmap it.
   (a) Assume that scores are available for all enrollments.
   (b) Assume that enrollments are recorded before any scores become known.

- 10. Rmap the conceptual schema in Fig. 6.46 (absorb the subtypes before mapping).

- 11. Refer to the MediaSurvey conceptual schema in Fig. 6.53.
   (a) Rmap this schema (absorb subtypes).
   (b) Set out an alternative relational schema with separate tables for each node in the subtype graph. Which schema is preferable?

- 12. (a) Rmap the Taxpayer conceptual schema for Exercise 6.5, Question 3(a).
   (b) Rmap the Taxpayer conceptual schema for Exercise 6.5, Question 3(b).

- 13. Rmap the SolarSystem conceptual schema for Exercise 6.5, Question 6.

- 14. Rmap the conceptual schema in Fig. 7.5 (Panel is an independent object type).

- 15. Rmap the CountryBorders conceptual schema for Exercise 7.3, Question 5.

- 16. Rmap the IT Company schema shown.

![](img/1344db3eba3d550e6edb009556fcd95c_539_0.png)

- 17. Rmap the University schema shown. Note that Degree is compositely identified (e.g., a Ph.D. from UCLA and a Ph.D. from MIT are treated as different degrees). Student is also compositely identified (by the time you finish the mapping, you will appreciate how much better it would be to use a StudentNr instead!).

The codes “y”, “n”, “PT”, “FT”, “int”, and “ext” abbreviate “yes”, “no”, “part-time”, “full-time”, “internal”, and “external”.

![](img/1344db3eba3d550e6edb009556fcd95c_540_0.png)

- 18. Rmap the following conceptual schema. Ignore the implicit semantic connection between Year and Date.

![](img/1344db3eba3d550e6edb009556fcd95c_541_0.png)

*Each TopDirector is by definition a Person who directed a Movie that won an Award.*

- 19. A life insurance company maintains an information system about its clients. The following information samples are extracted from a fragment of this system. For simplicity, several data items (e.g., client's name and address) are omitted and may be ignored for this question. Each client is identified by his/her client number (ClientNr).

The following table uses these abbreviations: Emp. = employment (EA = Employed by Another; SE = Self-Employed; NE = Not Employed); Acct = accounting; NS = Nonsmoker; S = Smoker. Some clients are referred by other clients (referrers) to take out a policy (this entitles referrers to special benefits outside our UoD). The value “?” is an ordinary null value meaning “not recorded” (e.g., nonexistent or unknown). The value “-” means “inapplicable” (because of some other data).

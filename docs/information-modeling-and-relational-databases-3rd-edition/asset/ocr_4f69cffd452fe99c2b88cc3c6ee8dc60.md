# 2. Rmap the following conceptual schema.

![](bbox=[0.26, 0.13, 0.71, 0.32])

3. (a) The conceptual schema for a given UoD is shown. A novice designer maps the likes and costs fact types into a single table: Likes ( woman, dress, cost ). With the aid of a small sample population, explain why this table is badly designed. Use surrogates w1, w2, ... for women and d1, d2, ... for dresses.

(b) Rmap the conceptual schema.

![](bbox=[0.21, 0.45, 0.78, 0.53])

4. In a given UoD, each lecturer has at least one degree and optionally has taught at one or more institutions. Each lecturer has exactly one identifying name, and at most one nick-name. Each degree is standardly identified by its code, but also has a unique title. Some degrees might not be held by any lecturer. Each institution is identified by its name. The gender and birth year of the lecturers are recorded as well as the years in which their degrees were awarded.

(a) A novice designer develops the following relational schema for this UoD. Explain, with the aid of sample data why these tables are badly designed.
Lecturer ( lecturerName, gender, degreeCode, degreeTitle )
Qualification ( degreeCode, yearAwarded )

(b) Draw a conceptual schema for this UoD.
(c) Rmap your answer to (b).

+   5. Add constraints to your conceptual schema for the following and then perform Rmap.
+   (a) Exercise 3.5, Question 2.
+   (b) Exercise 3.5, Question 3.

6. Rmap the Invoice conceptual schema for Exercise 6.3, Question 3.

7. Rmap the Oz Bank conceptual schema for Exercise 6.4, Question 6.

8. Consider a naval UoD in which sailors are identified by a sailorNr and ships by a shipNr, although both have names as well (not necessarily unique). We must record the
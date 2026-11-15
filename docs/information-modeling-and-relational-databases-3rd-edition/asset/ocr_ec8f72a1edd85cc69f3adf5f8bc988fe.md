![](bbox=[0.26, 0.1, 0.76, 0.15])

FIG. 4.47 A weird UoD where Degree and Gender are functions of each other.

If Gender really is a function of Degree, then any given degree is restricted to one gender (e.g., only males can seek a BS). If Degree really is a function of Gender, then all people of a given gender seek the same degree (e.g., all females seek just a BA). These two FDs are captured in Fig. 4.47 by the two UCs on the relationship type between Degree and Gender.

While such a UoD is possible, our knowledge about degree-awarding institutions makes this interpretation highly unlikely. To resolve our doubts, we could add test rows to the population. Although this is best done on conceptual fact tables, we could also test this example using the original output report. For example, if the domain expert accepts the population of Table 4.9 as being consistent with the UoD, then no FDs occur between Degree and Gender.

# Table 4.9 A counterexample to any FD between degree and gender.

| Person | Degree | Gender |
|---|---|---|
| Adams | BS | M |
| Brown | BA | F |
| Collins | BS | M |
| Davis | BS | F |

It is impractical to treat fact tables in a purely formal way, hunting for FDs. The number of dependencies to check increases rapidly with the fact type length. Although our conceptual focus on elementary fact types constrains this length, the search for FDs can still be laborious. While an automated FD checker can be of use, this kind of exhaustive checking is not fit for humans. We can short-circuit this work by taking advantage of human knowledge of the UoD.

As another simple example, consider the output report of Table 4.10. Suppose that, with the help of the domain expert, we express row 1 thus: the Lecturer with surname “Halpin” works for the Department coded “CS”, which is located in the Building numbered “69”. Is this fact splittable, and if so, how?

# Table 4.10 University data.

| Lecturer | Department | Building |
|---|---|---|
| Halpin | CS | 69 |
| Okimura | JA | 1 |
| Orlowska | CS | 69 |
| Wang | CN | 1 |

Here, the pronoun “which” introduces a nonrestrictive clause about the department that may be stated separately. So, this can be rephrased as two facts: Halpin works for the CS department, and the CS department is located in building 69. So, we should split on Department to get two fact types (Fig. 4.48).
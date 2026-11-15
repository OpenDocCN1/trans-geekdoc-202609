same term, use that. If different people use different terms for the same concept, get them to agree upon a standard term, and also note any synonyms in use.

Returning to the header of our preferences form in Fig. 3.5, we see the word “Tutorial”. Could this change (e.g., to “Lecture”)? If we wish to capture preferences for lectures as well as tutorials, the answer is “yes”, and we could model this as data. But let’s assume that this is not the case. The rest of the form header contains other information (e.g., duration of tutorials) but let’s assume this doesn’t need to be modeled.

The middle section of the form contains information about the tutorial times. If our UoD has only one subject (CS114), we could model this information as unary facts (e.g., Time “Mon 3 p.m.” is available). If we need to cater for other subjects as well, then we need to treat the “CS114” at the top of the form as data, and hence verbalize the schedule as binary facts (e.g., Subject “CS114” has a tutorial slot at Time “Mon 3 p.m.”). A completed tutorial preference form for a different subject is shown in Fig. 3.6.

Here, the layout of the five weekdays into columns makes it more obvious that the times are to be treated as data. The first fact from this section reads: Subject “CS183” has a tutorial slot at Time “Tues 2 p.m.”

| Monday | Tuesday | Wednesday | Thursday | Friday |
| :--- | :--- | :--- | :--- | :--- |
| | | | 9 a.m. | |
| | | | 11. a.m. | |
| | | | | |
| | 2 p.m. | 3 p.m. | 2 p.m. | |
| | | | | |
| \multicolumn{5}{|c|}{Student number: 211780..} | \\
| \multicolumn{5}{|c|}{Student surname: Smith................ Initials: J.A...} | \\
| \multicolumn{5}{|c|}{Tutorial preference 1: Tues 2 p.m.......} | \\
| \multicolumn{5}{|c|}{Tutorial preference 2: Thurs 11 a.m.......} | \\
| \multicolumn{5}{|c|}{Tutorial preference 3: Tues 3 p.m.......} | \\


FIG. 3.6 A completed tutorial preference form for a different subject.

If you reformat the structure of the earlier CS114 example (Fig. 3.5) to agree with this structure and place the two forms side by side, you can see what aspects are to be modeled as data by looking at what data changes between the two forms (subject code, times, student details).

In this larger UoD, assuming that students may enroll in many subjects, the facts about student preferences now need to take the subject into account. Instead of binaries, the preference facts are verbalized as ternaries. For example: Student 302156 has first tutorial preference for Subject “CS114” at Time “Mon 3 p.m.”; Student 211780 has third tutorial preference for Subject “CS183” at Time “Tues 3 p.m.”
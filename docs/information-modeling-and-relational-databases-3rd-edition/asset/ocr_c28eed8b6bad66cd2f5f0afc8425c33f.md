Note that the “%” and “_” are interpreted as wildcard characters only in the context of a like condition. For example, the following query returns the null set. There are no rows that satisfy the condition because if “=” is used instead of like, the expression “A%” is taken literally.

```
select starsign from Person
where starsign = 'A%'
```

As discussed earlier, to include a single quote in a string, we use two single quotes. For example, for the table scheme Actor ( surname, firstname, gender ) considered earlier, the following query returns each actor whose surname begins with “D”: select surname from Actor where surname like 'D%'.

To see a few examples where the like operator is quite useful, consider Table 12.10, which indicates which subjects are offered in which semester at a given university. The sample population is small to save space.

At this university, subject codes have the following meaning: the first two characters indicate the discipline area (e.g., “CS” denotes Computer Science and “PD” denotes Philosophy) and the third character denotes the year level (e.g., “1” for first-year level).

# Table 12.10 A relational table showing subjects offered and semesters.

| subject | semester |
|---|---|
| CS112 | 1 |
| CS112 | 2 |
| PD102 | 1 |
| PD102 | 2 |
| CS225 | 2 |
| CS314 | 1 |

Try to formulate the following queries yourself before peeking at the answers.

+   - List the computer science subjects.
+   - List the first-year level subjects.
+   - List subjects higher than first level that are offered in semester 2.

The queries in order are:

```
select distinct subject from Offering where subject like 'CS%'
```

```
select distinct subject from Offering where subject like '_ _1%'
```

```
select distinct subject from Offering
where subject not like '_ _1%' and semester = 2
```

Another common example of a string that is often interpreted as having structure is a person name. Usually, a person’s family name as well as either a first given name or initials